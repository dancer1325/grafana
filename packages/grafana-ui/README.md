# Grafana UI components library -- @grafana/ui --

* == componentS
  * 👀[Storybook catalog](http://developers.grafana.com/)👀 
  * uses
    * by [Grafana](https://github.com/grafana/grafana)
    * by plugins developers

## Installation

* ways
  * `yarn add @grafana/ui`, OR
  * `npm install @grafana/ui`

## Development

* recommendations
  * use `yarn link`
    * Reason:🧠create symlink -- to -- @grafana/ui lib🧠
    * steps
      * | this path,
        * `YARN_IGNORE_PATH=1 yarn link`
      * | your project,
        * `yarn link @grafana/ui`
