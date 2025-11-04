# Single interface nmstate

Every server must have 'nmstate' property defined that points to the file in the installation directory that should follow nmstate yaml syntax. 

The reference single.yaml file content without vlan subinterface

```
interfaces:
- name: ${IFNAME}
  type: ethernet
  state: up
  ipv4:
    address:
    - ip: ${IP}
      prefix-length: ${PREFIX}
    dhcp: false
    enabled: true
routes:
  config:
  - destination: 0.0.0.0/0
    next-hop-address: ${GW}
    next-hop-interface: ${IFNAME}
dns-resolver:
  config:
    search:
    - ${DNS_SEARCH}
    server:
    - ${DNS_IP}

```

As you see this file has bunch of variables following "${VARIABLE_NAME}" syntax. You can define any variable here as long as it [resolves](./variables.md)

[[Back]](./README.md)