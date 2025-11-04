# 3 node cluster with Cilium CNI and bonded interface

## Input files

All input files that define the installation intent must be in the single directory that looks like below with manifests being the single sub-directory with unpacked Cilium EE manifest yaml files. 

```
$ ls
drwxrwxr-x    manifests
-rw-rw-r--    cluster.json
-rw-rw-r--    server.json
-rw-rw-r--    bonding.yaml
-rw-rw-r--    ssh.pub
-rw-rw-r--    web.json
-rw-rw-r--    proxy.json
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

Refer to cluster.json [documentation](https://github.com/datacenter/iserver/blob/main/doc/ocp/bm/input_data_cluster_base.md) to understand all configurable options and defaults.

## [server.json](./server.json)

Defines all the servers
- imc/redfish IP
- target server IP
- target hostname
- interface name and mac address
- ip stack configuration template reference with variables

Keep kube:true settings for the single server, this is so-called management node of the cluster where cli tools will be prepared for day2ops i.e.,
- bashrc following proxy settings
- kubeconfig uploaded to .kube/config

[Tasks](https://github.com/datacenter/iserver/blob/main/doc/ocp/Operations.md) can be used for post-installation cluster customization.

Refer to server.json [documentation](https://github.com/datacenter/iserver/blob/main/doc/ocp/bm/input_data_server.md) to understand all configurable options.

## [redfish.json](./redfish.json)

Define the redfish credentials for servers.

If credentials are different per server then add redfish credentials in server.json e.g.

```
[
    {
        "hostname": "my-cluster-node1",
        "redfish": {
            "endpoint_ip": "10.50.50.50",
            "username": "aaa",
            "password": "bbb
        }
    }
]
```

## [bonding.yaml](./bonding.yaml)

IP stack configuration template in nmstate format as referred by server.nmstate parameter with variables

## [ssh.pub](./ssh.pub)

Unmodified ssh public key of the user and server where you run iserver from.

## [web.json](./web.json)

Defines local web server that has been launched using for example

```
sudo docker run -it --rm -d -p 8080:80 --name image -v /home/user/image:/usr/share/nginx/html nginx
```

Refer to web.json [documentation](https://github.com/datacenter/iserver/blob/main/doc/ocp/bm/input_data_web.md) to understand all configurable options.

## [proxy.json](./proxy.json)

If your environment is connected via HTTP Proxy to Internet, then proxy settings are defined in dedicated file.

If there is no proxy requirement, just delete the file.

[Back](../../README.md)