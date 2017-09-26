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

All the default variables are defined in *defaults/main.yml*. There are two variables you should change, depending on your configuration. 

The first is whether you want to have the the default [*_server.json*](#templates/_server.json.j2) template file disabled. To disable, you would change **consul.apply** from `yes` to `no`.

The second is where you would want the **config_dir** of your consul installation to be placed. You can change the default by editing the **consul.config.dir** path to your choosing. 

The rest of the configurations pertain either to the the current version of consul to install and the *_server.json* default configuration under the **consul.config** variables.

``` yaml
consul:
  version: 0.9.3 # 
  arch: amd64
  apply: yes
  config:
    dir: /etc/consul.d
    datacenter: example_dc
    data_dir: /opt/consul
    log_level: DEBUG
    node_name: changeMe
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
[2i]: https://img.shields.io/badge/license-BSD_2-green.svg
[2p]: ./LICENSE
[3i]: https://img.shields.io/badge/twitter-a_baez-blue.svg
[3p]: https://twitter.com/a_baez
