---
aliases:
  - ../../installation/mac/
description: How to install Grafana OSS or Enterprise on macOS
labels:
  products:
    - enterprise
    - oss
menuTitle: macOS
title: Install Grafana on macOS
weight: 600
---

# Install Grafana on macOS

* [youtube](https://www.youtube.com/watch?v=1zdm8SxOLYQ)

## -- via -- Homebrew

```
brew update
brew install grafana
```

* untars the files |
  - Intel Silicon,  
    - `/usr/local/Cellar/grafana/[version]` 
  - Apple Silicon,
    - `/opt/homebrew/Cellar/grafana/[version]`

```bash
brew services start grafana
```

### Grafana CLI + Homebrew

* requirements
  * add the CL's commands
    * `--homepath /opt/homebrew/opt/grafana/share/grafana`
    * `--config /opt/homebrew/etc/grafana/grafana.ini`
    * Reason: 🧠Homebrew installs Grafana | non-standard paths🧠
  * OTHER CL's commands -- based on the -- command
    * `admin` commands,
      * require `--configOverrides cfg:default.paths.data=/opt/homebrew/var/lib/grafana`
    * `plugins` commands,
      * ⚠️require `--pluginsDir /opt/homebrew/var/lib/grafana/plugins`⚠️

## -- via -- macOS binaries

1. [Grafana download page](https://grafana.com/grafana/download)
1. Select the Grafana version you want to install.
   - The **Version** field displays only tagged releases
   - If you want to install a nightly build, click **Nightly Builds** and then select a version.
1. Select an **Edition**.
   - **Enterprise:**
     - recommended version
     - have Enterprise features
   - **Open Source:** 
1. Click **Mac**.
1. Copy & paste the code / provided -- from the -- [download page](https://grafana.com/grafana/download) & run it | your CL
1. Untar the `gz` file
1. start Grafana service

   ```bash
   ./bin/grafana server
   ```

* [youtube](https://www.youtube.com/watch?v=T51Qa7eE3W8)
