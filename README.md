# Xray Ansible Collection

## Installation

```shell
ansible-galaxy collection install git+https://github.com/alsuo/ansible-xray-core.git
```

## Role: `alsuo.xray.xray-core`

Installs and configures the latest [xray-core](https://github.com/XTLS/Xray-core).

### Usage

Example playbook:

```yaml
- hosts: yourhost

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
    - alsuo.xray.xray-core
```

### Role Variables

```yaml
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
