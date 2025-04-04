+++
title = "Developer Guide"
type = "docs"
aliases = ["/plugins/development/", "/plugins/datasources/", "/plugins/apps/", "/plugins/panels/"]
[menu.docs]
name = "Developer Guide"
parent = "developing"
weight = 1
+++

# Developer Guide

From grafana 3.0 it's very easy to develop your own plugins and share them with other grafana users.

There are two blog posts about authoring a plugin that might also be of interest to any plugin authors, [Timing is Everything. Writing the Clock Panel Plugin for Grafana 3.0- part 1](https://grafana.com/blog/2016/04/08/timing-is-everything.-writing-the-clock-panel-plugin-for-grafana-3.0/) and [Timing is Everything. Editor Mode in Grafana 3.0 for the Clock Panel Plugin](https://grafana.com/blog/2016/04/15/timing-is-everything.-editor-mode-in-grafana-3.0-for-the-clock-panel-plugin/).

## Short version

1. [Setup grafana](http://docs.grafana.org/project/building_from_source/)
2. Clone an example plugin into ```/var/lib/grafana/plugins```  or `data/plugins` (relative to grafana git repo if your running development version from source dir)
3. Code away!

## What languages?

Since everything turns into javascript it's up to you to choose which language you want. That said it's probably a good idea to choose es6 or typescript since we use es6 classes in Grafana. So it's easier to get inspiration from the Grafana repo is you choose one of those languages.

## Buildscript

You can use any build system you like that support systemjs. All the built content should end up in a folder named ```dist``` and committed to the repository.By committing the dist folder the person who installs your plugin does not have to run any buildscript.

All our example plugins have build scripted configured.

## Metadata

See the [coding styleguide](./code-styleguide.md) for details on the metadata.

## module.(js|ts)

This is the entry point for every plugin. This is the place where you should export
your plugin implementation. Depending on what kind of plugin you are developing you
will be expected to export different things. You can find what's expected for [datasource](./datasources.md), [panels](./panels.md)
and [apps](./apps.md) plugins in the documentation.

The Grafana SDK is quite small so far and can be found here:

- [SDK file in Grafana](https://github.com/grafana/grafana/blob/master/public/app/plugins/sdk.ts)
- [SDK Readme](https://github.com/grafana/grafana/blob/master/public/app/plugins/plugin_api.md)

The SDK contains three different plugin classes: PanelCtrl, MetricsPanelCtrl and QueryCtrl. For plugins of the panel type, the module.js file should export one of these. There are some extra classes for [data sources](./datasources.md).

Example:

```javascript
import {ClockCtrl} from './clock_ctrl';

export {
  ClockCtrl as PanelCtrl
};
```

The module class is also where css for the dark and light themes is imported:

```javascript
import {loadPluginCss} from 'app/plugins/sdk';
import WorldmapCtrl from './worldmap_ctrl';

loadPluginCss({
  dark: 'plugins/grafana-worldmap-panel/css/worldmap.dark.css',
  light: 'plugins/grafana-worldmap-panel/css/worldmap.light.css'
});

export {
  WorldmapCtrl as PanelCtrl
};
```

## Start developing your plugin

There are three ways that you can start developing a Grafana plugin.

1. Setup a Grafana development environment. [(described here)](http://docs.grafana.org/project/building_from_source/) and place your plugin in the ```data/plugins``` folder.
2. Install Grafana and place your plugin in the plugins directory which is set in your [config file](../../installation/configuration.md). By default this is `/var/lib/grafana/plugins` on Linux systems.
3. Place your plugin directory anywhere you like and specify it grafana.ini.

We encourage people to setup the full Grafana environment so that you can get inspiration from the rest of grafana code base.

When Grafana starts it will scan the plugin folders and mount every folder that contains a plugin.json file unless
the folder contains a subfolder named dist. In that case grafana will mount the dist folder instead.
This makes it possible to have both built and src content in the same plugin git repo.

## Grafana Events

There are a number of Grafana events that a plugin can hook into:

- `init-edit-mode` can be used to add tabs when editing a panel
- `panel-teardown` can be used for clean up
- `data-received` is an event in that is triggered on data refresh and can be hooked into
- `data-snapshot-load` is an event triggered to load data when in snapshot mode.
- `data-error` is used to handle errors on dashboard refresh.

If a panel receives data and hooks into the `data-received` event then it should handle snapshot mode too. Otherwise the panel will not work if saved as a snapshot. [Getting Plugins to work in Snapshot Mode](./snapshot-mode.md) describes how to add support for this.

## Examples

We currently have three different examples that you can fork/download to get started developing your grafana plugin.

 - [simple-json-datasource](https://github.com/grafana/simple-json-datasource) (small datasource plugin for querying json data from backends)
 - [example-app](https://github.com/grafana/example-app)
 - [clock-panel](https://github.com/grafana/clock-panel)
 - [singlestat-panel](https://github.com/grafana/grafana/blob/master/public/app/plugins/panel/singlestat/module.ts)
 - [piechart-panel](https://github.com/grafana/piechart-panel)

## Other Articles

- [Getting Plugins to work in Snapshot Mode](./snapshot-mode.md)
- [Plugin Defaults and Editor Mode](./defaults-and-editor-mode.md)
- [Grafana Plugin Code Styleguide](./code-styleguide.md)
- [Grafana Apps](./apps.md)
- [Grafana Datasources](./datasources.md)
- [plugin.json Schema](./plugin.json.md)
