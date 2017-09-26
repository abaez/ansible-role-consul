Consul
=========
[![license][2i]][2p]
[![twitter][3i]][3p]

An [Ansible][1] role for installing and configuring a consul systemd instance.

Description
-----------

Installs [consul] with as little configuration as possible on a host. Designed for the host instance of a [hashicorp]'s [nomad] cluster.

Role Variables
--------------

All the default variables are defined in [*defaults/main.yml*][2]. There are two variables you should change, depending on your configuration.

The first is whether you want to have the the default [*_server.json*][3] template file disabled. To disable, you would change **consul.apply** from `yes` to `no`.

The second is where you would want the **config_dir** of your consul installation to be placed. You can change the default by editing the **consul.config.dir** path to your choosing.

The rest of the configurations pertain either to the the current version of consul to install and the [*_server.json*][3] default configuration under the **consul.config** variables.

[*defaults/main.yml*][2]
``` yaml
# defaults file for template
consul:
  # consul version
  version: 0.9.3
  # consul architecture
  arch: amd64
  # use _server.json
  apply: yes
  # _server.json defaults
  config:
    # config_dir
    dir: /etc/consul.d
    # datacenter name
    datacenter: example_dc
    # data directory for consul
    data_dir: /opt/consul
    # log level
    log_level: DEBUG
    # host node name
    node_name: changeMe
    # which ip to bind to
    bind: 0.0.0.0
```

Usage
-----

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

``` yaml
- hosts: servers
    roles:
        - { role: username.rolename, x: 42 }
```

Author Information
------------------

[Alejandro Baez][1]

[1]: https://keybase.io/baez
[2]: ./defaults/main.yml
[3]: ./templates/_server.json.j2

[2i]: https://img.shields.io/badge/license-BSD_2-green.svg
[2p]: ./LICENSE
[3i]: https://img.shields.io/badge/twitter-a_baez-blue.svg
[3p]: https://twitter.com/a_baez
