# ansible-uwsgi | absible role for install uWsgi
Tested on Ubuntu -  Centos
## Role variables
| Name | Description | Default Value |
| --- | --- | --- |
|prometheus_node_exporter_version: | Node exporter version | 0.15.1
|prometheus_install_path:| Prometheus Installation Path | "/opt/prometheus"
|generic_exporter_compressed_binary_path:| Compressed Bynary Path | "{{prometheus_install_path}}/exporter_gz"
|node_exporter_compressed_binary_path:|Node_exporter Compressed path | "{{generic_exporter_compressed_binary_path}}/node_exporter"
|generic_exporter_binary_path: | generic Exporter decompressed |  "{{prometheus_install_path}}/exporter"
|node_exporter_path:|Node Exporter decompressed | "{{generic_exporter_binary_path}}/node_exporter"
|prometheus_exporters_common_root_dir:|working exporter root ( sl destination for current exporter version) | "{{ prometheus_install_path }}/exporter"
|prometheus_exporters_common_user:| node expoter user | prometheus
|prometheus_exporters_common_group:| node expoter group| prometheus

## List variables
Check on documentation what collectors are enabled by default, and what collectors are disable by default.
| Name | Description |
| --- | --- |
|prometheus_node_exporter_enabled_collectors: |list collector you want enable if are disable |
|prometheus_node_exporter_disable_collectors: |list of collecto you want disable if are enable by default |
|prometheus_node_exporter_config_flags|flag you can enable in node_exporter|

Example:
```yml
prometheus_node_exporter_enabled_collectors:
  - buddyinfo
  - ksmd
  - mountstats
prometheus_node_exporter_disable_collectors:
  - meminfo
  - stat
  
prometheus_node_exporter_config_flags:
  'web.listen-address': '0.0.0.0:9100'
  'log.level': 'info'
```
