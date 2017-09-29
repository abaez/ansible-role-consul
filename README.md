Consul
=========
[![license][2i]][2p]
[![twitter][3i]][3p]

An [Ansible][4] role for installing and configuring a consul systemd instance.

Description
-----------

Installs [consul] with as little configuration as possible on a host. Designed for the host instance of a [hashicorp]'s [nomad] cluster.

<a name="Variables"></a> Role Variables
--------------

All the default variables are defined in [*defaults/main.yml*][2]. There are two variables you should change, depending on your configuration.

The first is whether you want to have the the default [*_server.json*][3] template file disabled. To disable, you would change **consul.apply** from `yes` to `no`.

The second is where you would want the **config_dir** of your consul installation to be placed. You can change the default by editing the **consul.config.dir** path to your choosing.

The rest of the configurations pertains either to the the current version of consul to install and the [*_server.json*][3] default configuration under the **consul.config** variables.

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

Once you've changed the [Role Variables](#Variables), you only need to apply the role to your playbook for it to function as you desired:

``` yaml
- hosts: servers
    roles:
        - abaez.consul
```

Author Information
------------------

[Alejandro Baez][1]

[hashicorp]: https://www.hashicorp.com/
[nomad]: https://www.hashicorp.com/products/nomad/
[consul]: https://www.hashicorp.com/products/consul/

[1]: https://keybase.io/baez
[2]: ./defaults/main.yml
[3]: ./templates/_server.json.j2
[4]: https://ansible.com

[2i]: https://img.shields.io/badge/license-BSD_2-green.svg
[2p]: ./LICENSE
[3i]: https://img.shields.io/badge/twitter-a_baez-blue.svg
[3p]: https://twitter.com/a_baez

