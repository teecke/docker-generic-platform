# Nexus Docker Platform Service

## Overview

Docker-compose configuration to bring up the Nexus service to the platform.

## Configuration

The service is formed by one container:

- **nexus**: based on [sonatype/nexus](https://hub.docker.com/r/sonatype/nexus/) docker image.

After the first run you must configure the service at http://[server]:8081/nexus URL.

## Operation

Start with `docker-compose up -d` and stop with `docker-compose stop` commands.

There is one volume created. All data and configuration are on this volumes, so never delete it.

```console
$ docker volume ls|grep "nexus\|VOLUME"
DRIVER              VOLUME NAME
local               nexus_sonatype-work
```

## Known issues

None known
