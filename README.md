# Xray Ansible Collection

## Installation

```shell
ansible-galaxy collection install git+https://github.com/alsuo/ansible-xray.git
```

## Role: `alsuo.xray.xray_core`

Installs and configures the latest [xray-core](https://github.com/XTLS/Xray-core).

### Usage

Example playbook:

```yaml
- hosts: yourhost
  become: yes

  collections:
    - alsuo.xray

  vars:
    xray_config:
      log:
        access: /var/log/xray/access.log
        error: /var/log/xray/error.log
        loglevel: debug
      inbounds:
        - ... your inbound config here ...
      outbounds:
        - ... your outbound config here ...
      routing:
        domainStrategy: IPIfNonMatch
        rules:
          - ... your routing rules here ...

  roles:
    - alsuo.xray.xray_core
```

### Role Variables

```yaml
# Enable/disable xray service
xray_enabled: true

# The user running xray
xray_user: xray

# The main group of xray user
xray_group: xray

# Directory containing .dat files
xray_assets_dir: /usr/local/share/xray

# Directory containing "config.json"
xray_config_dir: /usr/local/etc/xray

# Directory for storing logs.
# Xray will NOT log to this dir by default. You need to explicitly enable and configure logging (in config.json).
xray_logs_dir: /var/log/xray

# The Xray configuration.
xray_config: {}
```
