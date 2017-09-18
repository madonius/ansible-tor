# Tor hidden services

# Tor Hidden Services

A role to configure a tor hidden service

## Requirements

_None._

## Role Variables

##### ***Mandatory***:
_None._

##### ***Optional***:
| Name | Description | Default Value |
| :--- | :---------- | :------------ |
| tor_user | User under which tor is running | tor
| tor_group | Group associated with the tor user | tor
| tor_become | whether to become root during the installation | true
| tor_config_dir | Tor configuration file directory | /etc/tor
| tor_root_group | Group of the root-User | root
| hidden_services | List of services to be set up | _None_ |

##### ***Hidden service***
* **name**: Name describing the hidden name. _Defaults to **dir** if not defined_
* **dir**: Directory to store the hidden service configuration. _Defaults to /var/lib/tor/**name** if not defined_
* **port**: Port to expose to the TOR-Network
* **source**: The ip-address and port of the service to be exposed _Defualts to 127.0.0.1:**port** if not defined_

## Dependencies

_None._

## Example Playbook

```yaml
- hosts: servers
  roles:
    role: tor_hidden_services
    hidden_services:
    - name: ssh-onion
      port: 22
      source: 127.0.0.1:22
    - dir: /var/lib/tor/https-onion
      port: 443
      source: 127.0.0.1:443
```

## License

MIT License

## Author Information

* [Toke](https://github.com/toke)
* [Madonius](https://github.com/madonius)
