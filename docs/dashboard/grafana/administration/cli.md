# Grafana CLI

Grafana cli is a small executable that is bundled with grafana server and is suppose to be executed on the same machine as grafana runs.

## Plugins

The CLI helps you install, upgrade and manage your plugins on the same machine it CLI is running.
You can find more information about how to install and manage your plugins at the
[plugin page](../plugins/installation.md).

## Admin

> This feature is only available in grafana 4.1 and above.

To show all admin commands:
`grafana-cli admin`

### Reset admin password

You can reset the password for the admin user using the CLI.

`grafana-cli admin reset-admin-password ...`
