---
aliases:
  - administration/cli/
description: Guide to using grafana cli
keywords:
  - grafana
  - cli
  - grafana cli
  - command line interface
labels:
  products:
    - enterprise
    - oss
title: Grafana CLI
weight: 400
---

# Grafana CLI

* == small executable / -- bundled with -- Grafana server
  * can be executed | SAME machine / Grafana server is running on

## Invoking Grafana CLI

* ways
  * add the path to the grafana binaries | your `PATH` environment variable
  * invoke from the grafana binaries
    * | `bin` directory, run `./grafana cli`
    * `FULLPath/grafana cli`
      * _Example1:_ | Linux,  `/usr/share/grafana/bin/grafana cli`
      * _Example1:_ | Windows,  `C:\Program Files\GrafanaLabs\grafana\bin\grafana.exe cli`

## Grafana CLI command syntax

```bash
grafana cli [global options] command [command options] [arguments...]
```
* allowed command
  * `plugins`
  * `admin`
* 
    ```
    grafana cli -h
    ```
  * list ALL commands & options

* commands / require admin rights
  * installing or removing plugins

## Global options

* allows
  * temporarily ( | command) override certain Grafana default settings

### `--help` / `-h`

* displays the help

```bash
grafana cli -h
```

### `--version` / `-v`

* prints the version of Grafana CLI / currently running

```bash
grafana cli -v
```

### `--pluginsDir value`

* overrides the path | your local Grafana instance stores plugins
* uses
  * install, update, or remove a plugin
* _Example:_ 
    ```bash
    grafana cli --pluginsDir "/var/lib/grafana/devplugins" plugins install <plugin-id>
    ```

### `--repo value`

* allows
  * download and install or update plugins -- from a -- repository / != default Grafana repo
* _Example:_

    ```bash
    grafana cli --repo "https://example.com/plugins" plugins install <plugin-id>
    ```

### `--pluginUrl value`

* allows
  * download a .zip file / contain a plugin -- from a -- local URL 
    * alternative to 
      * downloading it -- from the -- default Grafana source
* _Example:_

    ```bash
    grafana cli --pluginUrl https://company.com/grafana/plugins/<plugin-id>-<plugin-version>.zip plugins install <plugin-id>
    ```

### Override Transport Layer Security

**Warning:** Turning off TLS is a significant security risk. We do not recommend using this option.

`--insecure` allows you to turn off Transport Layer Security (TLS) verification (insecure). You might want to do this if you are downloading a plugin from a non-default source.

**Example:**

```bash
grafana cli --insecure --pluginUrl https://company.com/grafana/plugins/<plugin-id>-<plugin-version>.zip plugins install <plugin-id>
```

### Enable debug logging

`--debug` or `-d` enables debug logging. Debug output is returned and shown in the terminal.

**Example:**

```bash
grafana cli --debug plugins install <plugin-id>
```

### Override a configuration setting

`--configOverrides` is a command line argument that acts like an environmental variable override.

For example, you can use it to redirect logging to another file (maybe to log plugin installations in Grafana Cloud) or when resetting the admin password and you have non-default values for some important configuration value (like where the database is located).

**Example:**

```bash
grafana cli --configOverrides cfg:default.paths.log=/dev/null plugins install <plugin-id>
```

### Override homepath value

Sets the path for the Grafana install/home path, defaults to working directory. You do not need to use this if you are in the Grafana installation directory when using the CLI.

**Example:**

```bash
grafana cli --homepath "/usr/share/grafana" admin reset-admin-password <new password>
```

### Override config file

`--config value` overrides the default location where Grafana expects the configuration file. Refer to [Configuration]({{< relref "./setup-grafana/configure-grafana/" >}}) for more information about configuring Grafana and default configuration file locations.

**Example:**

```bash
grafana cli --config "/etc/configuration/" admin reset-admin-password mynewpassword
```

## Plugins commands

* allows
  * install, upgrade, and manage your Grafana plugins / 👀-- by default, apply to the -- Grafana default repositories 👀
    * if you want to override the defaults -> see [Global Options](#global-options) 
* see [plugins page]({{< relref "./administration/plugin-management/" >}})

### List available plugins

```bash
grafana cli plugins list-remote
```

### Install the latest version of a plugin

```bash
grafana cli plugins install <plugin-id>
```

### Install a specific version of a plugin

```bash
grafana cli plugins install <plugin-id> <version>
```

### List installed plugins

```bash
grafana cli plugins ls
```

### Update all installed plugins

```bash
grafana cli plugins update-all
```

### Update one plugin

```bash
grafana cli plugins update <plugin-id>
```

### Remove one plugin

```bash
grafana cli plugins remove <plugin-id>
```

## Admin commands

* requirements
  * Grafana 4.1+

### Show all admin commands

```bash
grafana cli admin
```

### Reset admin password

* TODO:
`grafana cli admin reset-admin-password <new password>` resets the password for the admin user using the CLI. You might need to do this if you lose the admin password. By default, this command uses the default ID of the admin user, which is 1. If you know the ID of the admin user, you can use the `--user-id` flag to specify the user ID. If the `--user-id` flag is not specified and the command cannot find the admin user, it returns the list of current admin users' username and ID. From that list you can determine the ID of the admin user and run the command again with the `--user-id` flag.

If there are two flags being used to set the homepath and the config file path, then running the command returns this error:

> Could not find config defaults, make sure homepath command line parameter is set or working directory is homepath

To correct this, use the `--homepath` global option to specify the Grafana default homepath for this command:

```bash
grafana cli --homepath "/usr/share/grafana" admin reset-admin-password <new password>
```

If you have not lost the admin password, we recommend that you change the user password either in the User Preferences or in the Server Admin > User tab.

If you need to set the password in a script, then you can use the [Grafana User API]({{< relref "./developers/http_api/user/#change-password" >}}).

#### Reset admin password

If you installed Grafana using Homebrew, you can reset the admin password using the following command:

```bash
/opt/homebrew/opt/grafana/bin/grafana cli --config /opt/homebrew/etc/grafana/grafana.ini --homepath /opt/homebrew/opt/grafana/share/grafana --configOverrides cfg:default.paths.data=/opt/homebrew/var/lib/grafana admin reset-admin-password <new password>
```

### Migrate data and encrypt passwords

`data-migration` runs a script that migrates or cleans up data in your database.

`encrypt-datasource-passwords` migrates passwords from unsecured fields to secure_json_data field. Returns `ok` unless there is an error. Safe to execute multiple times.

**Example:**

```bash
grafana cli admin data-migration encrypt-datasource-passwords
```
