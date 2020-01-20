# Sonarqube Docker Platform Service

## Overview

Docker-compose configuration to bring up the SonarQube service to the platform.

## Configuration

The service is formed by two containers:

- **sonarqube**: based on [sonarqube](https://hub.docker.com/_/sonarqube/) docker image.
- **sonardb**: based on the [postgres](https://hub.docker.com/_/postgres) database docker image.

Before the first start, copy the `.env.dist` template file to `.env` file

```console
cp .env.dist .env
```

Then, edit the file and set the password variable.

```console
$ cat .env
POSTGRES_USER=sonar
POSTGRES_PASSWORD=[PUT_YOUR_POSTGRES_PASSWORD_HERE]
```

After the start, access to the service using the browser on the [server]:9000 port with "admin/admin" credentials and chnage the password once you are logged in.

## Operation

Start with `docker-compose up -d` and stop with `docker-compose stop` commands.

There are few volumes created. All data and configuration are on those volumes, so never delete they.

```console
$ docker volume ls|grep "sonar\|VOLUME"
DRIVER              VOLUME NAME
local               sonarqube_postgresql
local               sonarqube_postgresql_data
local               sonarqube_sonarqube_bundled-plugins
local               sonarqube_sonarqube_conf
local               sonarqube_sonarqube_data
local               sonarqube_sonarqube_extensions
```

## Known issues

The `docker-compose up -d` command should end with an error.

Edit `/etc/sysctl.conf` and put the line

```console
vm.max_map_count=262144
```

Then reboot the host

https://stackoverflow.com/questions/51445846/elastic-search-max-virtual-memory-areas-vm-max-map-count-65530-is-too-low-inc/51447991