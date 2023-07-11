# Ansible Role: lighthouse

### Description
Ansible role that will install, configure and runs [lighthouse](https://lighthouse-book.sigmaprime.io/docker.html):

### Table of Contents
  - [Supported Platforms](#supported-platforms)
  - [Dependencies](#dependencies)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [License](#license)
  - [Author Information](#author-information)

### Supported Platforms
```
* MacOS
* Debian
* Ubuntu
* Redhat(CentOS/Fedora)
* Amazon
```

### Dependencies

* Docker 

### Role Variables:

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file. By and large these variables are configuration options. Please refer to the lighthouse [docs](https://lighthouse-book.sigmaprime.io/) for more information

| Name                           | Default Value                      |  Description                                                                                                        |
|--------------------------------|------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `lighthouse_version`             | ___unset___                        | __REQUIRED__ Version of lighthouse to install and run.                                                            |
| `lighthouse_user`                | lighthouse                         | lighthouse user                                                                                                   |
| `lighthouse_group`               | lighthouse                         | lighthouse group                                                                                                  |
| `lighthouse_base_dir`            | /opt/lighthouse                    | Path to install to                                                                                                  |
| `lighthouse_config_dir`          | /etc/lighthouse                    | Path for default configuration                                                                                      |
| `lighthouse_data_dir`            | /opt/lighthouse/data               | Path for data directory                                                                                             |
| `lighthouse_log_dir`             | /var/log/lighthouse                | Path for logs directory                                                                                             |
| `lighthouse_log_level`           | "info"                             | Log level                                                                                                           |
| `lighthouse_network`             | mainnet                            | Predefined network configuration                                                                                    |
| `lighthouse_jwt_auth_file`       | "/etc/jwt-secret.hex"              | Path of the JWT file                                                                                                |
| `lighthouse_enable_doppelganger_protection` | True                    | Doppleganger protection enabled by default                                                                          |
| `lighthouse_validator_enabled`              | "False"                 | Whether to run in validator mode - please note that the secrets and keys need to be copied by you                   |
| `lighthouse_execution_urls`                 | "http://127.0.0.1:8551" | The elc execution url                                                                                               |
| `lighthouse_validator_beaconnodes`          | "http://lighthouse-beacon:9596" | The beacon endpoint for the validator to use                                                                |
| `lighthouse_checkpoint_sync_url`            | "https://beaconstate-{{lighthouse_network}}.chainsafe.io" | Checkpoint sync to speed things up                                                |
| `lighthouse_default_fee_recipient`          | ""                     | The default fee recepient address                                                                                    |
| `lighthouse_disable_deposit_contract_sync`  | True                   |  The deposit_contract_sync for validators                                                                            |
| `lighthouse_keystores_dir`  | "/config/keys"                         |  The keys directory for validators                                                                                   |
| `lighthouse_secrets_dir`    | "/config/secrets"                      |  The secrets directory for validators                                                                                |

### Keys/Secrets
Please note that you must put your own secrets and keys in the config directory that you are using ie `lighthouse_config_dir`

### Example Playbook

1. Default setup:
Install the role from galaxy
```
ansible-galaxy install consensys.lighthouse
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use 
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: consensys.lighthouse
    vars:
      lighthouse_version: x.y.z

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


2. Install via github

```
ansible-galaxy install git+https://github.com/consensys/ansible-role-lighthouse.git
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use 
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: ansible-role-lighthouse
    vars:
      lighthouse_version: x.y.z

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


### License

Apache


### Author Information

Consensys, 2023
