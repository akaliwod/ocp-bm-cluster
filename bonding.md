# Bonding nmstate

Every server must have 'nmstate' property defined that points to the file in the installation directory that should follow nmstate yaml syntax. 

The reference bonding.yaml file content

```
interfaces:
- name: ${BOND_MEMBER_1}
  type: ethernet
  state: up
- name: ${BOND_MEMBER_2}
  type: ethernet
  state: up
- name: ${BOND}
  type: bond
  state: up
  link-aggregation:
    mode: ${BOND_MODE}
    options:
      lacp_rate: ${LACP_RATE}
    port:
    - ${BOND_MEMBER_1}
    - ${BOND_MEMBER_2}
- name: ${BOND}.${VLAN}
  type: vlan
  state: up
  vlan:
    base-iface: ${BOND}
    id: ${VLAN}
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
    next-hop-interface: ${BOND}.${VLAN}
dns-resolver:
  config:
    search:
    - ${DNS_SEARCH}
    server:
    - ${DNS_IP}
```

As you see this file has bunch of variables following "${VARIABLE_NAME}" syntax. You can define any variable here as long as it [resolves](./variables.md)

[[Back]](./README.md)