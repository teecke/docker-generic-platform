# Teecke - Docker Generic Platform

Platform - GitOps

## Overview

Set of pieces able to act as a Docker Training Lab. Key points:

- Docker Powered
- Fully automated
- Infrastructure as Code provisioning
- DevOps / GitOps (2) mindset
- Compliant with The Devops Hispano Challenge (1)

## Objective

Learn to work on a platform composed of different components (services and products) with a kind of microservice architecture. Each piece of the platform can be developed, implemented and operated separately.

## Requirements

- [Docker](https://www.docker.com) installed
- Teecke [Devcontrol Tool](https://github.com/teecke/devcontrol) installed (3)

## Components

### Products

Developed by the Business Teams. Defined as the things that the customers or the end users can use.

- Web Application Server [Teecke GP Webapp](https://github.com/teecke/gp-webapp).
- Statics Server [Teecke GP Statics](https://github.com/teecke/gp-nginx).

### Services

Developed by the Platform Teams. Used to develop, build and operate the products.

- Jenkins from [Teecke GP Jenkins](https://github.com/teecke/gp-jenkins).
- Mail from [Teecke GP Mail](https://github.com/teecke/gp-mail).
- Nexus from [Teecke GP Nexus](https://github.com/teecke/gp-nexus).
- Sonar from [Warchant Sonar](https://gist.github.com/Warchant/0d0f0104fe7adf3b310937d2db67b512) recipie.
- Passbolt fromn [Official Passbolt](https://help.passbolt.com/hosting/install/ce/docker) docker-compose recipie.

## Operation

1. Install assets with `devcontrol assets-install`
2. Configure the pieces (products and services); review each piece documentation of how to setup.
3. Start all components with `devcontrol platform start`
4. Check the health of the products and services:
   1. Webapp product: <http://localhost:8001>
   2. Statics product: <http://localhost:8002>
   3. Jenkins service: <http://localhost:4001>
   4. Sonar service: <http://localhost:4002>
   5. Nexus service: <http://localhost:4003>
   6. Passbolt Service: <http://localhost:4004>
5. Make backups of the platform with `sudo devcontrol backup`. Note the use of `sudo` for the backups.
6. Stop the platform with `devcontrol platform stop`
7. Destroy the platform with `devcontrol platform destroy`

## Backups

Execute a backup of the static data, configurations and databases with `sudo devcontrol backup`.

Find three directories under `/var/backups/docker` directory with the configurations ad data for:

- `products`: all products
- `services`: all services
- `volumes`: the docker volumes of products and services

There are two sets of backups, with filenames beginning with "latest_" for the most recent ones, and "previous_" prefix for the oldest. The backup script will rotate the files from `latest_` to `previous_` with every execution.

You can put a crontab file under `/etc/cron.d/gp_backup` to set a daily backup task.

```console
# cat /etc/cron.d/gp_backup
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
00 04	* * *	root    (cd /home/master/platform; devcontrol backup > /var/log/gp_backup.log 2>&1)
```

## References and related projects

- Fulfill the [The DevOps Hispano Challenge](https://github.com/devops-hispano/reto-devops]) github project (1)
- Build with [GitOps](https://www.weave.works/technologies/gitops/) Mindset (2)
- Bash Scripts managed using Teecke [Devcontrol)](https://github.com/teecke/devcontrol) tool (3)

## Known issues
