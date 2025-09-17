---
aliases:
  - ../administration/configure-docker/
  - ../installation/configure-docker/
description: Guide for configuring the Grafana Docker image
keywords:
  - grafana
  - configuration
  - documentation
  - docker
  - docker compose
labels:
  products:
    - enterprise
    - oss
menuTitle: Configure a Docker image
title: Configure a Grafana Docker image
weight: 1800
---

# Configure a Grafana Docker image

* goal
  * how to run Grafana | Docker | complex environments / require
    * Use different images
    * Change logging levels
    * Define secrets | Cloud
    * Configure plugins

## Supported Docker image variants

- **Grafana Enterprise**: `grafana/grafana-enterprise`
  - variants
    - Alpine
    - Ubuntu
- **Grafana Open Source**: `grafana/grafana-oss`
  - variants
    - Alpine
    - Ubuntu

## Alpine image (recommended)

* [Alpine Linux](https://alpinelinux.org/about/)
  * == Linux distribution /
    * -- NOT affiliated with -- any commercial entity
    * audience
      * users / prioritize
        * security,
        * efficiency,
        * user-friendliness
    * much smaller vs other distribution base images
    * built -- based on -- [Alpine Linux project](http://alpinelinux.org/) base image
      * see [Alpine docker repo](https://hub.docker.com/_/alpine)
    * uses [musl libc](http://www.musl-libc.org/) -- instead of -- [glibc and others](http://www.etalabs.net/compare_libcs.html)
      * -> SOME software might encounter problems
    * _Example:_ [here](https://hub.docker.com/layers/grafana/grafana/main/images/sha256-c905e269ee455b2ee6d4281fef85fc1a78e70bfadba8a01a0dbb7047fa20e973)

## Ubuntu image

* built -- based on -- [Ubuntu](https://ubuntu.com/) base image
  * see [Ubuntu docker repo](https://hub.docker.com/_/ubuntu)
* audience
  * users /
    * prefer an Ubuntu-based image
    * require certain tools / unavailable | Alpine
* images
  - **Grafana Enterprise**: `grafana/grafana-enterprise:<version>-ubuntu`
  - **Grafana Open Source**: `grafana/grafana-oss:<version>-ubuntu`

## Run a specific version of Grafana

* [Grafana releases](https://github.com/grafana/grafana/releases)

* _Example:_ `docker run -d -p 3000:3000 --name grafana grafana/grafana-enterprise:<version number>` 

## Common problems

* permission errors | running `docker ....` 
  * Solutions:
    * `sudo docker ...` OR
    * add your user | `docker` group
      * [run Docker WITHOUT non-root user](https://docs.docker.com/engine/install/linux-postinstall/)

## Run the Grafana | main branch

* AFTER successful build of the main branch,
  * generated tags -- [grafana/grafana-oss](https://hub.docker.com/r/grafana/grafana-oss/tags/) --
    * `grafana/grafana-oss:main`
    * `grafana/grafana-oss:main-ubuntu`
  * ADDITIONALLY created -- [grafana/grafana-oss-dev](https://hub.docker.com/r/grafana/grafana-oss-dev/tags) -- 
    * `grafana/grafana-oss-dev:<version><build ID>-pre`
      * `<version>`
        * == Grafana`s NEXT version
      * `<build ID>`
        * == CI build's ID
      * use cases
        * run Grafana main branch | production environment
          * Reason:🧠
            * stable
            * consistent🧠
    * `grafana/grafana-oss-dev:<version><build ID>-pre-ubuntu` 

## Default paths

* == 👀default configuration parameters👀 
  * / INDEPENDENT of 
    * versions OR
    * OS OR
    * environment
  * _Example:_ virtual machine, Docker, Kubernetes, etc.
  * [here](configure-grafana)
  * / set | start the Grafana Docker container

| Setting               | Default value             |
| --------------------- | ------------------------- |
| GF_PATHS_CONFIG       | /etc/grafana/grafana.ini  |
| GF_PATHS_DATA         | /var/lib/grafana          |
| GF_PATHS_HOME         | /usr/share/grafana        |
| GF_PATHS_LOGS         | /var/log/grafana          |
| GF_PATHS_PLUGINS      | /var/lib/grafana/plugins  |
| GF_PATHS_PROVISIONING | /etc/grafana/provisioning |

* | run Grafana in Docker,
  * if you want to change the configurations -> -- via -- [environment variables](configure-grafana/_index.md#override-configuration-with-environment-variables) 
    * ❌NOT valid, -- via -- `conf/grafana.ini`❌

## Install plugins | Docker container

* types of plugins
  * private
  * community 

* [how to install plugins | Docker container](./installation/docker/index.md#install-plugins-in-the-docker-container)

### Install plugins -- from -- other sources

* `-e GF_INSTALL_PLUGINS=<url to plugin zip>;<plugin name>`

## Build a custom Grafana Docker image

* see [this Dockerfile](/grafana/packaging/docker/custom/Dockerfile)
  * 's arguments
    * `GRAFANA_VERSION`
      * requirements
        * valid `grafana/grafana` Docker image tag

### Build Grafana -- via -- Image Renderer plugin pre-installed

* TODO: > **Note:** This feature is experimental.

Currently, the Grafana Image Renderer plugin requires dependencies that are
not available in the Grafana Docker image (see [GitHub Issue#301](https://github.com/grafana/grafana-image-renderer/issues/301) for more details)
However, you can create a customized Docker image using the `GF_INSTALL_IMAGE_RENDERER_PLUGIN` build argument as a solution
This will install the necessary dependencies for the Grafana Image Renderer plugin to run.

Example:

The following example shows how to build a customized Grafana Docker image that includes the Image Renderer plugin.

```bash
# go to the folder
cd packaging/docker/custom

# running the build command
docker build \
  --build-arg "GRAFANA_VERSION=latest" \
  --build-arg "GF_INSTALL_IMAGE_RENDERER_PLUGIN=true" \
  -t grafana-custom .

# running the docker run command
docker run -d -p 3000:3000 --name=grafana grafana-custom
```

### Build a Grafana Docker image with pre-installed plugins

If you run multiple Grafana installations with the same plugins, you can save time by building a customized image that includes plugins available on the [Grafana Plugin download page](/grafana/plugins). When you build a customized image, Grafana doesn't have to install the plugins each time it starts, making the startup process more efficient.

> **Note:** To specify the version of a plugin, you can use the `GF_INSTALL_PLUGINS` build argument and add the version number. The latest version is used if you don't specify a version number. For example, you can use `--build-arg "GF_INSTALL_PLUGINS=grafana-clock-panel 1.0.1,grafana-simple-json-datasource 1.3.5"` to specify the versions of two plugins.

Example:

The following example shows how to build and run a custom Grafana Docker image with pre-installed plugins.

```bash
# go to the custom directory
cd packaging/docker/custom

# running the build command
# include the plugins you want e.g. clock planel etc
docker build \
  --build-arg "GRAFANA_VERSION=latest" \
  --build-arg "GF_INSTALL_PLUGINS=grafana-clock-panel,grafana-simple-json-datasource" \
  -t grafana-custom .

# running the custom Grafana container using the docker run command
docker run -d -p 3000:3000 --name=grafana grafana-custom
```

### Build a Grafana Docker image with pre-installed plugins from other sources

You can create a Docker image containing a plugin that is exclusive to your organization, even if it is not accessible to the public. Simply use the `GF_INSTALL_PLUGINS` build argument to specify the plugin's URL and installation folder name, such as `GF_INSTALL_PLUGINS=<url to plugin zip>;<plugin install folder name>`.

The following example demonstrates creating a customized Grafana Docker image that includes a custom plugin from a URL link, the clock panel plugin, and the simple-json-datasource plugin. You can define these plugins in the build argument using the Grafana Plugin environment variable.

```bash
# go to the folder
cd packaging/docker/custom

# running the build command
docker build \
  --build-arg "GRAFANA_VERSION=latest" \
  --build-arg "GF_INSTALL_PLUGINS=http://plugin-domain.com/my-custom-plugin.zip;my-custom-plugin,grafana-clock-panel,grafana-simple-json-datasource" \
  -t grafana-custom .

# running the docker run command
docker run -d -p 3000:3000 --name=grafana grafana-custom
```

## Logging

* == Docker container logs

* places | forward Docker container logs,
  * `STDOUT`
    * default one
  * 👀if you want to set -> -- via -- [log mode](./configure-grafana/_index.md#mode)👀

* `-e "GF_LOG_MODE=mode1 mode2 ..."`
  * `docker run -p 3000:3000 --name=grafana -e "GF_LOG_MODE=console file" grafana/grafana`

## Configure Grafana with Docker Secrets OR Docker volumes

* goal
  * input confidential data | Grafana, -- via -- configuration files

* use cases
  * input login credentials & secrets

### -- via -- Docker Secrets
* -- based on -- [Docker Secrets](https://docs.docker.com/engine/swarm/secrets/) 
  * Reason:🧠secrets are AUTOMATICALLY mapped -- to -- Docker container's `/run/secrets/` location🧠 

* steps
  * `docker secret create secretNameToSet`
  * `docker run -d -p 3000:3000 --name grafana -e "GF_<SectionName>_<KeyName>__FILE=/run/secrets/secretNameToSet" grafana/grafana`

### -- via -- Docker volumes
* [here](examples/configureDocker/README.md#---via----docker-volumes)

## Troubleshoot a Docker deployment

* recommendation
  * switch log level
    * ways
      * | Docker Cli,
        * `-e "GF_LOG_LEVEL=someAllowedLogLevel"`
      * | Docker Compose
        * add the environment variable `GF_LOG_LEVEL`
  * `docker compose config`
    * validate Docker Compose file

* [MORE](./configure-grafana/_index.md#log)
