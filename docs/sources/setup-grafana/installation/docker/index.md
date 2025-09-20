---
aliases:
  - ../../installation/docker/
description: Guide for running Grafana using Docker
labels:
  products:
    - enterprise
    - oss
menuTitle: Grafana Docker image
title: Run Grafana Docker image
weight: 400
---

* | Grafana v12.4.0,
  * ❌[Docker Hub repository `grafana/grafana-oss`](https://hub.docker.com/r/grafana/grafana-oss) NO longer updated❌
  * use [Docker Hub repository `grafana/grafana`](https://hub.docker.com/r/grafana/grafana) 

# Run Grafana Docker image

* goal
  * install Grafana -- via the -- official Docker images

* [Youtube](https://www.youtube.com/watch?v=FlDfcMbSLXs)

* Grafana Docker images
  * types OR editions
    - **Grafana Enterprise**: `grafana/grafana-enterprise`
      - recommended one
      - 👀free👀
        - ⚠️!= [enterprise product](https://grafana.com/products/enterprise/?utm_source=grafana-install-page)⚠️
    - **Grafana Open Source**: `grafana/grafana-oss`
  * [MORE](../../configure-docker)

* steps
  * | any terminal
    * `docker run -d -p 3000:3000 --name=grafana grafana/grafana-enterprise`
  * | browser,
    * http://localhost:3000/login
      * admin/admin
  * | any terminal
    * `docker stop grafana`

### Save your Grafana data

* ways
  * [common ones](/grafana/docs/sources/shared/back-up)
  * using Docker
  * -- via -- [Docker volumes](https://docs.docker.com/storage/volumes/)
  * -- via -- [bind mounts](https://docs.docker.com/storage/bind-mounts/)

#### -- via -- Docker volumes (recommended)

* restrictions
  * ONLY accessible -- through --
    * Docker containers
    * Docker CLI

#### -- via -- bind mounts

* pros
  * accessible -- by -- ANY process 
    * == ❌NOT ONLY Docker❌

* restrictions
  * start the container / user has read & write permission to write | directory

### configure Grafana -- via -- environment variables

* [environment variables](../../configure-grafana/_index.md#override-configuration-with-environment-variables)
  * allows
    * configuring Grafana's custom configuration settings

## Install plugins | Docker container

* 
* see 
  * [Plugin Management](../../../administration/plugin-management/)
  * [Community Plugins](https://grafana.com/grafana/plugins/)

* For more information on managing plugins, refer to 

To install plugins in the Docker container, complete the following steps:

1. Pass the plugins you want to be installed to Docker with the `GF_PLUGINS_PREINSTALL` environment variable as a comma-separated list.

   This starts a background process that installs the list of plugins while Grafana server starts.

   For example:

   ```bash
   docker run -d -p 3000:3000 --name=grafana \
     -e "GF_PLUGINS_PREINSTALL=grafana-clock-panel, grafana-simple-json-datasource" \
     grafana/grafana-enterprise
   ```

1. To specify the version of a plugin, add the version number to the `GF_PLUGINS_PREINSTALL` environment variable.

   For example:

   ```bash
   docker run -d -p 3000:3000 --name=grafana \
     -e "GF_PLUGINS_PREINSTALL=grafana-clock-panel@1.0.1" \
     grafana/grafana-enterprise
   ```

   > **Note:** If you do not specify a version number, the latest version is used.

1. To install a plugin from a custom URL, use the following convention to specify the URL: `<plugin ID>@[<plugin version>]@<url to plugin zip>`.

   For example:

   ```bash
   docker run -d -p 3000:3000 --name=grafana \
     -e "GF_PLUGINS_PREINSTALL=custom-plugin@@https://github.com/VolkovLabs/custom-plugin.zip" \
     grafana/grafana-enterprise
   ```

## Example

 volume, the server root URL set, and the official [clock panel](/grafana/plugins/grafana-clock-panel) plugin installed.

```bash
# create a persistent volume for your data
docker volume create grafana-storage

# start grafana by using the above persistent storage
# and defining environment variables

docker run -d -p 3000:3000 --name=grafana \
  --volume grafana-storage:/var/lib/grafana \
  -e "GF_SERVER_ROOT_URL=http://my.grafana.server/" \
  -e "GF_PLUGINS_PREINSTALL=grafana-clock-panel" \
  grafana/grafana-enterprise
```

## Run Grafana via Docker Compose

Docker Compose is a software tool that makes it easy to define and share applications that consist of multiple containers. It works by using a YAML file, usually called `docker-compose.yaml`, which lists all the services that make up the application. You can start the containers in the correct order with a single command, and with another command, you can shut them down. For more information about the benefits of using Docker Compose and how to use it refer to [Use Docker Compose](https://docs.docker.com/get-started/08_using_compose/).

### Before you begin

To run Grafana via Docker Compose, install the compose tool on your machine. To determine if the compose tool is available, run the following command:

```bash
docker compose version
```

If the compose tool is unavailable, refer to [Install Docker Compose](https://docs.docker.com/compose/install/).

### Run the latest stable version of Grafana

This section shows you how to run Grafana using Docker Compose. The examples in this section use Compose version 3. For more information about compatibility, refer to [Compose and Docker compatibility matrix](https://docs.docker.com/compose/compose-file/compose-file-v3/).

> **Note:** If you are on a Linux system (for example, Debian or Ubuntu), you might need to add `sudo` before the command or add your user to the `docker` group. For more information, refer to [Linux post-installation steps for Docker Engine](https://docs.docker.com/engine/install/linux-postinstall/).

To run the latest stable version of Grafana using Docker Compose, complete the following steps:

1. Create a `docker-compose.yaml` file.

   ```bash
   # first go into the directory where you have created this docker-compose.yaml file
   cd /path/to/docker-compose-directory

   # now create the docker-compose.yaml file
   touch docker-compose.yaml
   ```

1. Now, add the following code into the `docker-compose.yaml` file.

   For example:

   ```yaml
   services:
     grafana:
       image: grafana/grafana-enterprise
       container_name: grafana
       restart: unless-stopped
       ports:
         - '3000:3000'
   ```

1. To run `docker-compose.yaml`, run the following command:

   ```bash
   # start the grafana container
   docker compose up -d
   ```

   Where:

   d = detached mode

   up = to bring the container up and running

To determine that Grafana is running, open a browser window and type `IP_ADDRESS:3000`. The sign in screen should appear.

### Stop the Grafana container

To stop the Grafana container, run the following command:

```bash
docker compose down
```

> **Note:** For more information about using Docker Compose commands, refer to [docker compose](https://docs.docker.com/engine/reference/commandline/compose/).

### Save your Grafana data

By default, Grafana uses an embedded SQLite version 3 database to store configuration, users, dashboards, and other data. When you run Docker images as containers, changes to these Grafana data are written to the filesystem within the container, which will only persist for as long as the container exists. If you stop and remove the container, any filesystem changes (i.e. the Grafana data) will be discarded. To avoid losing your data, you can set up persistent storage using [Docker volumes](https://docs.docker.com/storage/volumes/) or [bind mounts](https://docs.docker.com/storage/bind-mounts/) for your container.

#### Use Docker volumes (recommended)

Use Docker volumes when you want the Docker Engine to manage the storage volume.

To use Docker volumes for persistent storage, complete the following steps:

1. Create a `docker-compose.yaml` file

   ```bash
   # first go into the directory where you have created this docker-compose.yaml file
   cd /path/to/docker-compose-directory

   # now create the docker-compose.yaml file
   touch docker-compose.yaml
   ```

1. Add the following code into the `docker-compose.yaml` file.

   ```yaml
   services:
     grafana:
       image: grafana/grafana-enterprise
       container_name: grafana
       restart: unless-stopped
       ports:
         - '3000:3000'
       volumes:
         - grafana-storage:/var/lib/grafana
   volumes:
     grafana-storage: {}
   ```

1. Save the file and run the following command:

   ```bash
   docker compose up -d
   ```

#### Use bind mounts

If you plan to use directories on your host for the database or configuration when running Grafana in Docker, you must start the container with a user that has the permission to access and write to the directory you map.

To use bind mounts, complete the following steps:

1. Create a `docker-compose.yaml` file

   ```bash
   # first go into the directory where you have created this docker-compose.yaml file
   cd /path/to/docker-compose-directory

   # now create the docker-compose.yaml file
   touch docker-compose.yaml
   ```

1. Create the directory where you will be mounting your data, in this case is `/data` e.g. in your current working directory:

   ```bash
   mkdir $PWD/data
   ```

1. Now, add the following code into the `docker-compose.yaml` file.

   ```yaml
   services:
     grafana:
       image: grafana/grafana-enterprise
       container_name: grafana
       restart: unless-stopped
       # if you are running as root then set it to 0
       # else find the right id with the id -u command
       user: '0'
       ports:
         - '3000:3000'
       # adding the mount volume point which we create earlier
       volumes:
         - '$PWD/data:/var/lib/grafana'
   ```

1. Save the file and run the following command:

   ```bash
   docker compose up -d
   ```

### Example

The following example runs the latest stable version of Grafana, listening on port 3000, with the container named `grafana`, persistent storage in the `grafana-storage` docker volume, the server root URL set, and the official [clock panel](/grafana/plugins/grafana-clock-panel/) plugin installed.

```yaml
services:
  grafana:
    image: grafana/grafana-enterprise
    container_name: grafana
    restart: unless-stopped
    environment:
      - GF_SERVER_ROOT_URL=http://my.grafana.server/
      - GF_PLUGINS_PREINSTALL=grafana-clock-panel
    ports:
      - '3000:3000'
    volumes:
      - 'grafana_storage:/var/lib/grafana'
volumes:
  grafana_storage: {}
```

{{< admonition type="note" >}}
If you want to specify the version of a plugin, add the version number to the `GF_PLUGINS_PREINSTALL` environment variable. For example: `-e "GF_PLUGINS_PREINSTALL=grafana-clock-panel@1.0.1,grafana-simple-json-datasource@1.3.5"`. If you do not specify a version number, the latest version is used.
{{< /admonition >}}
