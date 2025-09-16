* goal
  * install Grafana | mac

# install -- via -- Homebrew
* | any terminal
  * `cd /opt/homebrew/Cellar/grafana/` & `ls`
    * check grafana is installed
  * `brew services start grafana`
* | browser,
  * http://localhost:3000/
    * "admin" / "admin"
    * request you to change the password
      * 👀ALTHOUGH, you can pass SAME 👀

## Grafana CLI + Homebrew

* admin commands
  * | any terminal,
    * `/opt/homebrew/opt/grafana/bin/grafana cli --config /opt/homebrew/etc/grafana/grafana.ini --homepath /opt/homebrew/opt/grafana/share/grafana --configOverrides cfg:default.paths.data=/opt/homebrew/var/lib/grafana admin reset-admin-password newadmin`
      * change admin's password to "newadmin"
      * logout & try to log in again

* plugins commands
  * | any terminal,
    * `/opt/homebrew/opt/grafana/bin/grafana cli --config /opt/homebrew/etc/grafana/grafana.ini --homepath /opt/homebrew/opt/grafana/share/grafana --pluginsDir "/opt/homebrew/var/lib/grafana/plugins" plugins --help`
      * check plugins AVAILABLE commands
      * | this command,
        * you can skip `--config /opt/homebrew/etc/grafana/grafana.ini --homepath /opt/homebrew/opt/grafana/share/grafana`
          * ❌BUT NOT | ALL commands❌
          * recommendation
            * include ALWAYS
    * `/opt/homebrew/opt/grafana/bin/grafana cli --config /opt/homebrew/etc/grafana/grafana.ini --homepath /opt/homebrew/opt/grafana/share/grafana --pluginsDir "/opt/homebrew/var/lib/grafana/plugins" plugins list-remote`
      * check AVAILABLE plugins
    * `/opt/homebrew/opt/grafana/bin/grafana cli --config /opt/homebrew/etc/grafana/grafana.ini --homepath /opt/homebrew/opt/grafana/share/grafana --pluginsDir "/opt/homebrew/var/lib/grafana/plugins" plugins install grafana-azureprometheus-datasource`
      * install "grafana-azureprometheus-datasource" plugin 
      * `brew services restart grafana`
        * AFTER installing plugins, required to restart Grafana
      * `/opt/homebrew/opt/grafana/bin/grafana cli --config /opt/homebrew/etc/grafana/grafana.ini --homepath /opt/homebrew/opt/grafana/share/grafana --pluginsDir "/opt/homebrew/var/lib/grafana/plugins" plugins ls`
        * check installed plugins

# install -- via -- macOs binaries

* TODO:
