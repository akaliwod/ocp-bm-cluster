# 3 node cluster with OVNKubernetes CNI and single interface

## Input files

All input files that define the installation intent must be in the single directory that looks like below 

```
$ ls
-rw-rw-r--    cluster.json
-rw-rw-r--    single.yaml
```

## [cluster.json](./cluster.json)

Defines the key cluster parameters
- name
- base dns domain
- network type
- openshift version
- machine network gateway
- ntp
- dns ip
- dns search domain

Defines all the servers
- imc/redfish IP and credentials
- target server IP
- target hostname
- interface name and mac address
- ip stack configuration template reference with variables incl. [auto-generation](../../variables.md)

Additionally:
- ssh public key
- web server
- http proxy settings (if any)

[Tasks](https://github.com/datacenter/iserver/blob/main/doc/ocp/Operations.md) can be used for further customization post installation.

Refer to cluster.json [documentation](https://github.com/datacenter/iserver/blob/main/doc/ocp/bm/input_data_cluster_aio.md) to understand all configurable options and defaults.

## [single.yaml](./single.yaml)

IP stack configuration template in nmstate format as referred by server.nmstate parameter with variables

[Back](../../README.md)