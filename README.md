# Ansible Role: prometheus-node-exporter

An Ansible role that installs Prometheus Node Exporter on Ubuntu|Debian|Redhat-based machines with systemd|Upstart|sysvinit.

Installation Prometheus Tree Directory


```
│
├── exporter
│   ├── node_exporter
│   │   ├── node_exporter-0.14.0.linux-amd64
│   │   │   ├── LICENSE
│   │   │   ├── node_exporter
│   │   │   └── NOTICE
│   │   └── node_exporter-0.15.1.linux-amd64
│   │       ├── LICENSE
│   │       ├── node_exporter
│   │       └── NOTICE
│   └── node_exporter_current -> /opt/prometheus/exporter/node_exporter/node_exporter-0.15.1.linux-amd64
└── exporter_gz
    └── node_exporter
        ├── node_exporter-0.14.0.linux-amd64.tar.gz
        └── node_exporter-0.15.1.linux-amd64.tar.gz

```


Playblook Example
```yml
- name: install node-exporter
  hosts: all
  roles:
    - ansible-prometheus-node-exporter
  tags: node-exporter
```



## Requirements

All needed packages will be installed with this role.

## Role Variables

Available variables are listed below, along with default values:

```yaml
prometheus_node_exporter_version: 0.15.1
prometheus_node_exporter_enabled_collectors:
prometheus_node_exporter_disable_collectors:

prometheus_node_exporter_config_flags:
  'web.listen-address': '0.0.0.0:9100'
  'log.level': 'info'
```
## Dependencies

- UnderGreen.prometheus-exporters-common

## Example Playbook
```yaml
- hosts: node-exporters
  roles:
    - UnderGreen.prometheus-node-exporter
  vars:
    prometheus_node_exporter_enabled_collectors:
      - diskstats
      - filesystem
      - loadavg
      - systemd
```
## License

GPLv2
