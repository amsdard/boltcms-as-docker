{name}
========================
* [local] {name}.test
* [dev] {name}.app.amsdard.io
* [live] 

Requirements
---
 * configure your local [projects enrironment](https://bitbucket.org/as-docker/projects-environment)
 * make sure You have [YAKE](https://yake.amsdard.io/) installed


Run project
---
```
yake configure
yake up
yake install
```
* make sure `{name}.test` domain is routed to your localhost


Additional info
---
* do not use `require-dev` in composer.json (keep common vendors)


Deploy (dev / rancher)
---
```
yake deploy webapp
```
* import `./deploy/rancher/docker-compose.yml` into Rancher + complete ENVs
* make sure `mysql` works on specific host (Scheduling)
* make sure `webapp` has *Health Check* enabled


Deploy (prod)
---

*BEWARE* Webapp container (or PHP) has a `/opt/app/config` volume mounted. Please make sure you have copied all the YAML files manually to the `~/data/prod.php.{name}.docker/config` after you run the stack.

```
yake deploy webapp
```
* import `./deploy/prod/docker-compose.yml` into server + copy ENV files from `docker` directory
* `docker-compose pull --quiet`
* `docker-compose up -d --force-recreate`

