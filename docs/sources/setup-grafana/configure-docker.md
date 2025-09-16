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

## Install plugins in the Docker container

* types of plugins
  * private
  * community 

* [how to install plugins | Docker container](./installation/docker/index.md#install-plugins-in-the-docker-container)

### Install plugins from other sources

* TODO: To install plugins from other sources, you must define the custom URL and specify it immediately before the plugin name in the `GF_INSTALL_PLUGINS` environment variable: `GF_INSTALL_PLUGINS=<url to plugin zip>;<plugin name>`.

Example:

The following command runs Grafana Enterprise on **port 3000** in detached mode and installs the custom plugin, which is specified as a URL parameter in the `GF_INSTALL_PLUGINS` environment variable.

```bash
docker run -d -p 3000:3000 --name=grafana \
  -e "GF_INSTALL_PLUGINS=http://plugin-domain.com/my-custom-plugin.zip;custom-plugin,grafana-clock-panel" \
  grafana/grafana-enterprise
```

## Build a custom Grafana Docker image

In the Grafana GitHub repository, the `packaging/docker/custom/` folder includes a `Dockerfile` that you can use to build a custom Grafana image
* The `Dockerfile` accepts `GRAFANA_VERSION`, `GF_INSTALL_PLUGINS`, and `GF_INSTALL_IMAGE_RENDERER_PLUGIN` as build arguments.

The `GRAFANA_VERSION` build argument must be a valid `grafana/grafana` Docker image tag
* By default, Grafana builds an Alpine-based image
* To build an Ubuntu-based image, append `-ubuntu` to the `GRAFANA_VERSION` build argument.

Example:

The following example shows you how to build and run a custom Grafana Docker image based on the latest official Ubuntu-based Grafana Docker image:

```bash
# go to the custom directory
cd packaging/docker/custom

# run the docker build command to build the image
docker build \
  --build-arg "GRAFANA_VERSION=latest-ubuntu" \
  -t grafana-custom .

# run the custom grafana container using docker run command
docker run -d -p 3000:3000 --name=grafana grafana-custom
```

### Build Grafana with the Image Renderer plugin pre-installed

> **Note:** This feature is experimental.

Currently, the Grafana Image Renderer plugin requires dependencies that are not available in the Grafana Docker image (see [GitHub Issue#301](https://github.com/grafana/grafana-image-renderer/issues/301) for more details). However, you can create a customized Docker image using the `GF_INSTALL_IMAGE_RENDERER_PLUGIN` build argument as a solution. This will install the necessary dependencies for the Grafana Image Renderer plugin to run.

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

By default, Docker container logs are directed to `STDOUT`, a common practice in the Docker community. You can change this by setting a different [log mode]({{< relref "./configure-grafana#mode" >}}) such as `console`, `file`, or `syslog`. You can use one or more modes by separating them with spaces, for example, `console file`. By default, both `console` and `file` modes are enabled.

Example:

The following example runs Grafana using the `console file` log mode that is set in the `GF_LOG_MODE` environment variable.

```bash
# Run Grafana while logging to both standard out
# and /var/log/grafana/grafana.log

docker run -p 3000:3000 -e "GF_LOG_MODE=console file" grafana/grafana-enterprise
```

## Configure Grafana with Docker Secrets

You can input confidential data like login credentials and secrets into Grafana using configuration files. This method works well with [Docker Secrets](https://docs.docker.com/engine/swarm/secrets/), as the secrets are automatically mapped to the `/run/secrets/` location within the container.

You can apply this technique to any configuration options in `conf/grafana.ini` by setting `GF_<SectionName>_<KeyName>__FILE` to the file path that contains the secret information. For more information about Docker secret command usage, refer to [docker secret](https://docs.docker.com/engine/reference/commandline/secret/).

The following example demonstrates how to set the admin password:

- Admin password secret: `/run/secrets/admin_password`
- Environment variable: `GF_SECURITY_ADMIN_PASSWORD__FILE=/run/secrets/admin_password`

### Configure Docker secrets credentials for AWS CloudWatch

Grafana ships with built-in support for the [Amazon CloudWatch datasource]({{< relref "../datasources/aws-cloudwatch" >}}). To configure the data source, you must provide information such as the AWS ID-Key, secret access key, region, and so on. You can use Docker secrets as a way to provide this information.

Example:

The example below shows how to use Grafana environment variables via Docker Secrets for the AWS ID-Key, secret access key, region, and profile.

The example uses the following values for the AWS Cloudwatch data source:

```bash
AWS_default_ACCESS_KEY_ID=aws01us02
AWS_default_SECRET_ACCESS_KEY=topsecret9b78c6
AWS_default_REGION=us-east-1
```

1. Create a Docker secret for each of the values noted above.

   ```bash
   echo "aws01us02" | docker secret create aws_access_key_id -
   ```

   ```bash
   echo "topsecret9b78c6" | docker secret create aws_secret_access_key -
   ```

   ```bash
   echo "us-east-1" | docker secret create aws_region -
   ```

1. Run the following command to determine that the secrets were created.

   ```bash
   $ docker secret ls
   ```

   The output from the command should look similar to the following:

   ```
   ID                          NAME           DRIVER    CREATED              UPDATED
   i4g62kyuy80lnti5d05oqzgwh   aws_access_key_id             5 minutes ago        5 minutes ago
   uegit5plcwodp57fxbqbnke7h   aws_secret_access_key         3 minutes ago        3 minutes ago
   fxbqbnke7hplcwodp57fuegit   aws_region                    About a minute ago   About a minute ago
   ```

   Where:

   ID = the secret unique ID that will be use in the docker run command

   NAME = the logical name defined for each secret

1. Add the secrets to the command line when you run Docker.

   ```bash
   docker run -d -p 3000:3000 --name grafana \
     -e "GF_DEFAULT_INSTANCE_NAME=my-grafana" \
     -e "GF_AWS_PROFILES=default" \
     -e "GF_AWS_default_ACCESS_KEY_ID__FILE=/run/secrets/aws_access_key_id" \
     -e "GF_AWS_default_SECRET_ACCESS_KEY__FILE=/run/secrets/aws_secret_access_key" \
     -e "GF_AWS_default_REGION__FILE=/run/secrets/aws_region" \
     -v grafana-data:/var/lib/grafana \
     grafana/grafana-enterprise
   ```

You can also specify multiple profiles to `GF_AWS_PROFILES` (for example, `GF_AWS_PROFILES=default another`).

The following list includes the supported environment variables:

- `GF_AWS_${profile}_ACCESS_KEY_ID`: AWS access key ID (required).
- `GF_AWS_${profile}_SECRET_ACCESS_KEY`: AWS secret access key (required).
- `GF_AWS_${profile}_REGION`: AWS region (optional).

## Troubleshoot a Docker deployment

By default, the Grafana log level is set to `INFO`, but you can increase the log level to `DEBUG` mode when you want to reproduce a problem.

For more information about logging, refer to [logs]({{< relref "./configure-grafana#log" >}}).

### Increase log level using the Docker run (CLI) command

To increase the log level to `DEBUG` mode, add the environment variable `GF_LOG_LEVEL` to the command line.

```bash
docker run -d -p 3000:3000 --name=grafana \
  -e "GF_LOG_LEVEL=debug" \
  grafana/grafana-enterprise
```

### Increase log level using the Docker Compose

To increase the log level to `DEBUG` mode, add the environment variable `GF_LOG_LEVEL` to the `docker-compose.yaml` file.

```yaml
version: '3.8'
services:
  grafana:
    image: grafana/grafana-enterprise
    container_name: grafana
    restart: unless-stopped
    environment:
      # increases the log level from info to debug
      - GF_LOG_LEVEL=debug
    ports:
      - '3000:3000'
    volumes:
      - 'grafana_storage:/var/lib/grafana'
volumes:
  grafana_storage: {}
```

### Validate Docker Compose YAML file

The chance of syntax errors appearing in a YAML file increases as the file becomes more complex. You can use the following command to check for syntax errors.

```bash
# go to your docker-compose.yaml directory
cd /path-to/docker-compose/file

# run the validation command
docker compose config
```

If there are errors in the YAML file, the command output highlights the lines that contain errors. If there are no errors in the YAML file, the output includes the content of the `docker-compose.yaml` file in detailed YAML format.
