AS docker - BoltCMS
========================
implement Docker into your BoltCMS (^4.x) project
https://boltcms.io

Requirements
---
 * [AS-docker](https://as-docker.app.amsdard.io) setup
 * install composer globally [global composer command](https://hub.docker.com/r/amsdard/composer/)


Install - Full sample (when you install a new project)
---
In your `~/Projects` directory, create a new project (a new `newproject.com` directory will be created)
NOTICE 01/2021: add `--ignore-platform-reqs`, PHP 8.x is not supported yet, use 7.x instead, 
  also ignore `@auto-scripts` fails
```
cd ~/Projects/
composer create-project --ignore-platform-reqs bolt/project newproject.com
```

install as-docker (*nginx* + *php* by default)
```
composer require --ignore-platform-reqs amsdard/boltcms-as-docker
./vendor/amsdard/boltcms-as-docker/setup
```


run the project
```
yake configure
yake up
yake install
```

see https://docs.bolt.cm/installation/installation for additional info

open URL `http://newproject.com.test/` and enjoy your new BoltCMS!


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
 
