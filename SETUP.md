# Setup

## New Magento 2 Project (macOS/Linux)

1. Create the project template by going to the place you want the new project (ex. cd ~/Sites/magento2), then run
	- `curl -s https://raw.githubusercontent.com/nguyentrunghieu98/docker-magento/master/lib/template | bash`
	- `Edit folder ENV`

2. Extract the contents of your current Magento site to the `src` folder, or download a fresh copy of the Magento source code for starting a new project with:
    - `download 2.4.2`
    - `download 2.3.7`

3. Add an entry to your local hosts file with your custom domain. Assuming the domain you want to setup is `magento2.test`, enter the below. Be sure to use a `.test` tld, as `.localhost` and `.dev` will present issues with domain resolution.
    - `echo "127.0.0.1 magento2.docker" | sudo tee -a /etc/hosts`

4. Start your Docker containers with the provided helper script:
    - `bin/start`
    
    ## If you install Magento 2.3x
    - `Edit docker-compose.yml`
	  ```
	  phpfpm:
	    image: markoshust/magento-php:7.3-fpm-6
	    environment:
	      PHP_IDE_CONFIG: serverName=localhost
	    links:
	      - db
	    volumes: *appvolumes
	  ```

5. For new projects: run Magento's setup install process with the below helper script. Feel free to edit this file to your liking; at the very least you will probably need to update the `base-url` value to the domain you setup in step 3. Also, be sure to setup [Composer Authentication](https://github.com/markshust/docker-magento#composer-authentication) before initiating the setup script.

6. Wait for 10 seconds

7. Starting in Magento 2.4x Elastic Search is required:
  - `bin/setup24x magento2.docker`
  
  ## If you install Magento 2.3x
  
  - `bin/setup23x magento2.docker`
  
  ### Magento Setup Install Commands (You can use the command)

    Starting in Magento 2.4 Elastic Search is required:
    ```
    bin/clinotty bin/magento setup:install \
    --db-host=db \
    --db-name=magento \
    --db-user=magento \
    --db-password=magento \
    --base-url=https://magento2.docker/ \
    --base-url-secure=https://magento2.docker/ \
    --admin-firstname=admin \
    --admin-lastname=Admin \
    --admin-email=admin@gmail.com \
    --admin-user=admin \
    --backend-frontname=admin \
    --admin-password=admin@123 \
    --language=en_US \
    --currency=USD \
    --timezone=America/New_York \
    --amqp-host=rabbitmq \
    --amqp-port=5672 \
    --amqp-user=guest \
    --amqp-password=guest \
    --amqp-virtualhost=/ \
    --cache-backend=redis \
    --cache-backend-redis-server=redis \
    --cache-backend-redis-db=0 \
    --page-cache=redis \
    --page-cache-redis-server=redis \
    --page-cache-redis-db=1 \
    --session-save=redis \
    --session-save-redis-host=redis \
    --session-save-redis-log-level=4 \
    --session-save-redis-db=2 \
    --elasticsearch-host=elasticsearch \
    --elasticsearch-port=9200 \
    --elasticsearch-username=magento \
    --elasticsearch-password=magento\
    --use-rewrites=1
   
    echo "Turning on developer mode.."
    bin/clinotty bin/magento deploy:mode:set developer

    echo "Forcing deploy of static content to speed up initial requests..."
    bin/clinotty bin/magento setup:static-content:deploy -f

    echo "Re-indexing with Elasticsearch..."
    bin/clinotty bin/magento indexer:reindex

    echo "Clearing the cache to apply updates..."
    bin/clinotty bin/magento cache:flush
    ```

    For Magento 2.3 installations and below the following will still work:
    
    If use Elasticsuite (https://github.com/Smile-SA/elasticsuite/issues/2180#issuecomment-867994165)
    Add: --es-hosts="elasticsearch:9200" \
    
    ```
    bin/clinotty bin/magento setup:install \
    --db-host=db \
    --db-name=magento \
    --db-user=magento \
    --db-password=magento \
    --base-url=https://magento2.docker/ \
    --base-url-secure=https://magento2.docker/ \
    --admin-firstname=Admin \
    --admin-lastname=Admin \
    --admin-email=admin@gmail.com \
    --admin-user=admin \
    --backend-frontname=admin \
    --admin-password=admin@123 \
    --language=en_US \
    --currency=USD \
    --timezone=America/New_York \
    --use-rewrites=1
    
    echo "Turning on developer mode.."
    bin/clinotty bin/magento deploy:mode:set developer

    echo "Forcing deploy of static content to speed up initial requests..."
    bin/clinotty bin/magento setup:static-content:deploy -f

    echo "Re-indexing with Elasticsearch..."
    bin/clinotty bin/magento indexer:reindex

    echo "Clearing the cache to apply updates..."
    bin/clinotty bin/magento cache:flush
    ```

  
8. You may now access your site! Check out whatever domain you setup from within a web browser.
    - `bin/restart`
    - `open http://magento2.docker`

## New Magento 2 Project (Windows)

Works with Docker in WSL. Full instructions to follow.
