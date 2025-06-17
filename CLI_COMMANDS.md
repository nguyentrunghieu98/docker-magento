## 🛠️ Custom CLI Commands (Overview)

> This guide summarizes the most useful `bin/*` commands available in the `nguyentrunghieu98/docker-magento` stack. Commands are grouped by functionality to help developers quickly locate and understand their purpose.

---

### 📚 Table of Contents

* [Docker & Container Management](#docker--container-management)
* [Magento Setup](#magento-setup)
* [Testing & Debugging](#testing--debugging)
* [Filesystem & Permissions](#filesystem--permissions)
* [Development Tools](#development-tools)
* [Composer & Frontend](#composer--frontend)
* [Database & Cache](#database--cache)
* [Networking & SSL](#networking--ssl)
* [PWA Studio](#pwa-studio)
* [Other Utilities](#other-utilities)

---

### Docker & Container Management

| Command                                                      | Description                       |
| ------------------------------------------------------------ | --------------------------------- |
| `bin/start`, `bin/stop`, `bin/restart`, `bin/status`         | Manage container lifecycle        |
| `bin/remove`, `bin/removeall`                                | Clean up containers and volumes   |
| `bin/stopall`                                                | Stop all Docker containers        |
| `bin/docker-compose`, `bin/docker-start`, `bin/docker-stats` | Compose commands & resource usage |

---

### Magento Setup

| Command                                       | Description                                   |
| --------------------------------------------- | --------------------------------------------- |
| `bin/setup`, `bin/setup-install`              | Install Magento with default or custom domain |
| `bin/setup-domain`, `bin/setup-composer-auth` | Set domain & Composer auth                    |
| `bin/create-user`, `bin/deploy`               | Create users or redeploy static content       |
| `bin/magento`, `bin/magento-version`          | Magento CLI access & version info             |

---

### Testing & Debugging

| Command                                                           | Description                               |
| ----------------------------------------------------------------- | ----------------------------------------- |
| `bin/test/unit`, `bin/test/unit-coverage`, `bin/test/unit-xdebug` | Run PHPUnit tests                         |
| `bin/dev-test-run`, `bin/mftf`                                    | Advanced test runners (integration, MFTF) |
| `bin/xdebug`, `bin/debug-cli`, `bin/spx`, `bin/log`               | Debugging & logging tools                 |

---

### Filesystem & Permissions

| Command                                          | Description                             |
| ------------------------------------------------ | --------------------------------------- |
| `bin/bash`, `bin/cli`, `bin/root` (and variants) | Run shell or commands inside containers |
| `bin/fixperms`, `bin/fixowns`                    | Fix file permissions/ownership          |
| `bin/copytocontainer`, `bin/copyfromcontainer`   | Sync files host <-> container           |

---

### Development Tools

| Command                                                  | Description                        |
| -------------------------------------------------------- | ---------------------------------- |
| `bin/analyse`, `bin/phpcs*`                              | Static analysis & coding standards |
| `bin/n98-magerun2`, `bin/devconsole`                     | Developer CLI tools                |
| `bin/dev-urn-catalog-generate`, `bin/check-dependencies` | IDE integration & dependency check |

---

### Composer & Frontend

| Command                            | Description                    |
| ---------------------------------- | ------------------------------ |
| `bin/composer`                     | Composer wrapper               |
| `bin/grunt`, `bin/node`, `bin/npm` | Frontend build tools           |
| `bin/setup-grunt`                  | Grunt setup for Magento themes |

---

### Database & Cache

| Command                      | Description             |
| ---------------------------- | ----------------------- |
| `bin/mysql`, `bin/mysqldump` | Import/export MySQL     |
| `bin/redis`                  | Redis CLI access        |
| `bin/cache-clean`            | Cache clear via watcher |

---

### Networking & SSL

| Command                             | Description                                 |
| ----------------------------------- | ------------------------------------------- |
| `bin/setup-ssl`, `bin/setup-ssl-ca` | Local HTTPS cert setup                      |
| `bin/configure-linux`               | Configure host entries, firewall for Xdebug |

---

### PWA Studio

| Command                                   | Description             |
| ----------------------------------------- | ----------------------- |
| `bin/pwa-studio`, `bin/setup-pwa-studio*` | Install & run Venia PWA |

---

### Other Utilities

| Command                                  | Description                           |
| ---------------------------------------- | ------------------------------------- |
| `bin/install-php-extensions`             | Install PHP extensions in container   |
| `bin/download`                           | Download Magento source from Composer |
| `bin/removevolumes`, `bin/removenetwork` | Manage Docker volumes & networks      |
| `bin/ece-patches`, `bin/blackfire`       | Cloud patches & profiling             |
| `bin/status`, `bin/update`               | Project status & self-update          |

---

