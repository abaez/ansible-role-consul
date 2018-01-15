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

The first is whether you want to have the the default [*_server.json*][3] template file disabled. To disable, you would comment out the **use_consul_server** variable.

The second is the version of consul to install through **consul_version**. 

The rest of the configurations pertains either to the the current version of consul to install and the [*_server.json*][3] default configuration under the **consul_server** dictionary variables.

[*defaults/main.yml*][2]
``` yaml
---


# consul version
consul_version: 1.0.2
# use _server.json
use_consul_server: yes

# _server.json defaults
consul_server:
  # datacenter name
  datacenter: some-dc
  # data directory for consul
  data_dir: /var/consul
  # log level
  log_level: DEBUG
  # host node name
  node_name: ChangeMe
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

