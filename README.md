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
- Teecke [Devcontrol Tool](https://github.com/teecke/devcontrol)installed (3)

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

1. Start all components with `devcontrol platform start`
2. Check the health of the products and services:
   1. Webapp product: <http://localhost:8080>
   2. Statics product: <http://localhost:8090>
   3. Jenkins service: <http://localhost:4002>
   4. Sonar service: <http://localhost:9000>
   5. Nexus service: <http://localhost:8081>
   6. Passbolt Service: <http://localhost:10080> <http://localhost:10443>
3. Stop the platform with `devcontrol platform stop`
4. Destroy the platform with `devcontrol platform destroy`

## References and related projects

- Fulfill the [The DevOps Hispano Challenge](https://github.com/devops-hispano/reto-devops]) github project (1)
- Build with [GitOps](https://www.weave.works/technologies/gitops/) Mindset (2)
- Bash Scripts managed using Teecke [Devcontrol)](https://github.com/teecke/devcontrol) tool (3)
