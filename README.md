AS docker - BoltCMS
========================
implement Docker into your BoltCMS (^3.x) project


Requirements
---
 * configure your local [projects enrironment](https://bitbucket.org/as-docker/projects-environment)
 * make sure You have [YAKE](https://yake.amsdard.io/) installed


Install - Full sample (when you install a new project)
---
In your `~/Projects` directory, create a new project (a new `newproject.com` directory will be created)
```
mkdir ~/Projects/newproject.com
cd ~/Projects/newproject.com
curl -O https://bolt.cm/distribution/bolt-latest.tar.gz
tar -xzf bolt-latest.tar.gz --strip-components=1
rm -f bolt-latest.tar.gz
```

install as-docker (*nginx* + *php* by default)
```
composer require amsdard/boltcms-as-docker
./vendor/amsdard/boltcms-as-docker/setup
```

[alternative] as an alternative you can use *apache* mode
```
composer require amsdard/boltcms-as-docker
./vendor/amsdard/boltcms-as-docker/setup apache
```

run the project
```
yake configure
yake up
yake nut init
```

setup MySQL database, by opening `./app/config/config.yml` and update the following section:
```
database:
    driver: %DATABASE_DRIVER%
    host: %DATABASE_HOST%
    databasename: %DATABASE_NAME%
    username: %DATABASE_USERNAME%
    password: %DATABASE_PASSWORD%
```
and optionally other params by your environment variables (`.env`).

open URL `http://newproject.com.test/` and enjoy your new BoltCMS!

You can also run the following command to setup the webpage:
```
yake nut setup:run
```

Production deploy
---
Webapp container (or PHP) has a `/opt/app/config` volume mounted. Please make sure you have copied all the YAML files manually to the `~/data/prod.php.{name}.docker/config` after you run the stack.


How it works
---
* below file structure will be installed
```
.
├── README.md
├── docker-compose.yml
├── Yakefile
├── deploy
│   ├── prod
│   │   └── docker-compose.yml
│   └── rancher
│       └── docker-compose.yml
└── docker
    ├── mysql
    │   ├── config.env
    │   └── config.env.dist
    ├── nginx
    │   ├── Dockerfile
    │   └── default.conf
    └── php
        └── Dockerfile
```
* your project directory name will be filled as local domain name and docker image namespace (see `docker-compose.yml`)
* new rules will be added to your `.gitignore` file: 
  * `/composer.phar` internal project composer
  * `/docker/*/*.env` container ENV
 
