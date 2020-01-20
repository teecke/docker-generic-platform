# Passbolt Docker Platform Service

## Overview

Docker-compose configuration to bring up the Passbolt service to the platform.

## Configuration

The service is formed by two containers:

- **passbolt**: based on [passbolt/passbolt](https://hub.docker.com/r/passbolt/passbolt) docker image.
- **db**: based on [passbolt/passbolt](https://hub.docker.com/_/mariadb) databasse docker image.

After the first run you must configure the service at the [server]:80 and [server]:443 ports.

## Operation

Start with `docker-compose up -d` and stop with `docker-compose stop` commands.

There are two volumes created. All data and configuration are on those volumes, so never delete they.

```console
$ docker volume ls|grep "passbolt\|VOLUME"
DRIVER              VOLUME NAME
local               passbolt_database_volume
local               passbolt_gpg_volume
local               passbolt_images_volume
```

## Known issues

None known
