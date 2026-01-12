# Complex nmstate configurations with groups

Using example as documentation

## server.json

```
[
    {
        "hostname": "bm1-1",
        "kube": true,
        "redfish": {
            "endpoint_ip": "10.50.50.50"
        },
        "ssh": {
            "ip": "10.10.10.10"
        },
        "vlan": 701,
        "interface": [
            {
                "name": "eno7",
                "mac": "aa:aa:aa:aa:aa:48"
            },
            {
                "name": "eno8",
                "mac": "aa:aa:aa:aa:aa:49"
            },
            {
                "name": "eno9",
                "mac": "aa:aa:aa:aa:aa:50",
                "group": 1
            },
            {
                "name": "eno10",
                "mac": "aa:aa:aa:aa:aa:51",
                "group": 1
            },
            {
                "name": "eno11",
                "mac": "aa:aa:aa:aa:aa:52",
                "group": 2
            }
        ],
        "group": [
            {
                "id": 1,
                "ip": "10.20.20.51/24",
                "vlan": 666
            },
            {
                "id": 2,
                "ip": "10.30.30.65/28"
            }
        ],
        "nmstate": "bonding.yaml"
    },
    {
        "hostname": "bm1-2",
        "kube": false,
        "redfish": {
            "endpoint_ip": "10.50.50.51"
        },
        "ssh": {
            "ip": "10.10.10.11"
        },
        "vlan": 701,
        "interface": [
            {
                "name": "eno7",
                "mac": "bb:bb:bb:bb:bb:0c"
            },
            {
                "name": "eno8",
                "mac": "bb:bb:bb:bb:bb:0d"
            },
            {
                "name": "eno9",
                "mac": "bb:bb:bb:bb:bb:50",
                "group": 1
            },
            {
                "name": "eno10",
                "mac": "bb:bb:bb:bb:bb:51",
                "group": 1
            },
            {
                "name": "eno11",
                "mac": "bb:bb:bb:bb:bb:52",
                "group": 2
            }
        ],
        "group": [
            {
                "id": 1,
                "ip": "10.20.20.52/24",
                "vlan": 666
            },
            {
                "id": 2,
                "ip": "10.30.30.66/28"
            }
        ],
        "nmstate": "bonding.yaml"
    },
    {
        "hostname": "bm1-3",
        "kube": false,
        "redfish": {
            "endpoint_ip": "10.50.50.52"
        },
        "ssh": {
            "ip": "10.10.10.12"
        },
        "vlan": 701,
        "interface": [
            {
                "name": "eno7",
                "mac": "cc:cc:cc:cc:cc:6c"
            },
            {
                "name": "eno8",
                "mac": "cc:cc:cc:cc:cc:6d"
            },
            {
                "name": "eno9",
                "mac": "cc:cc:cc:cc:cc:50",
                "group": 1
            },
            {
                "name": "eno10",
                "mac": "cc:cc:cc:cc:cc:51",
                "group": 1
            },
            {
                "name": "eno11",
                "mac": "cc:cc:cc:cc:cc:52",
                "group": 2
            }
        ],
        "group": [
            {
                "id": 1,
                "ip": "10.20.20.53/24",
                "vlan": 666
            },
            {
                "id": 2,
                "ip": "10.30.30.67/28"
            }
        ],
        "nmstate": "bonding.yaml"
    }
]
```

## generated variables

### Server bm1-1

```
{
    "BOND": "bond0",
    "VLAN": 701,
    "BOND_MODE": "802.3ad",
    "LACP_RATE": "slow",
    "IP": "10.10.10.10",
    "PREFIX": "28",
    "GW": "10.10.10.14",
    "DNS_SEARCH_1": "domain.com",
    "DNS_SEARCH": "domain.com",
    "DNS_IP_1": "100.100.100.100",
    "DNS_IP": "100.100.100.100",
    "BOND_MEMBER_1": "eno7",
    "BOND_MEMBER_2": "eno8",
    "GROUP_1_BOND_MEMBER_1": "eno9",
    "GROUP_1_BOND_MEMBER_2": "eno10",
    "GROUP_2_IFNAME": "eno11",
    "GROUP_1_VLAN": 666,
    "GROUP_1_BOND": "bond1",
    "GROUP_1_BOND_MODE": "802.3ad",
    "GROUP_1_LACP_RATE": "slow",
    "GROUP_1_IP": "10.20.20.51",
    "GROUP_1_PREFIX": "24",
    "GROUP_2_IP": "10.30.30.65",
    "GROUP_2_PREFIX": "28"
}
```

### Server bm1-2

```
{
    "BOND": "bond0",
    "VLAN": 701,
    "BOND_MODE": "802.3ad",
    "LACP_RATE": "slow",
    "IP": "10.10.10.11",
    "PREFIX": "28",
    "GW": "10.10.10.14",
    "DNS_SEARCH_1": "domain.com",
    "DNS_SEARCH": "domain.com",
    "DNS_IP_1": "100.100.100.100",
    "DNS_IP": "100.100.100.100",
    "BOND_MEMBER_1": "eno7",
    "BOND_MEMBER_2": "eno8",
    "GROUP_1_BOND_MEMBER_1": "eno9",
    "GROUP_1_BOND_MEMBER_2": "eno10",
    "GROUP_2_IFNAME": "eno11",
    "GROUP_1_VLAN": 666,
    "GROUP_1_BOND": "bond1",
    "GROUP_1_BOND_MODE": "802.3ad",
    "GROUP_1_LACP_RATE": "slow",
    "GROUP_1_IP": "10.20.20.52",
    "GROUP_1_PREFIX": "24",
    "GROUP_2_IP": "10.30.30.66",
    "GROUP_2_PREFIX": "28"
}
```

### Server bm1-3

```
{
    "BOND": "bond0",
    "VLAN": 701,
    "BOND_MODE": "802.3ad",
    "LACP_RATE": "slow",
    "IP": "10.10.10.12",
    "PREFIX": "28",
    "GW": "10.10.10.14",
    "DNS_SEARCH_1": "domain.com",
    "DNS_SEARCH": "domain.com",
    "DNS_IP_1": "100.100.100.100",
    "DNS_IP": "100.100.100.100",
    "BOND_MEMBER_1": "eno7",
    "BOND_MEMBER_2": "eno8",
    "GROUP_1_BOND_MEMBER_1": "eno9",
    "GROUP_1_BOND_MEMBER_2": "eno10",
    "GROUP_2_IFNAME": "eno11",
    "GROUP_1_VLAN": 666,
    "GROUP_1_BOND": "bond1",
    "GROUP_1_BOND_MODE": "802.3ad",
    "GROUP_1_LACP_RATE": "slow",
    "GROUP_1_IP": "10.20.20.53",
    "GROUP_1_PREFIX": "24",
    "GROUP_2_IP": "10.30.30.67",
    "GROUP_2_PREFIX": "28"
}
```

## bonding.yaml

```
interfaces:
- name: ${BOND_MEMBER_1}
  type: ethernet
  state: up
- name: ${BOND_MEMBER_2}
  type: ethernet
  state: up
- name: ${GROUP_1_BOND_MEMBER_1}
  type: ethernet
  state: up
- name: ${GROUP_1_BOND_MEMBER_2}
  type: ethernet
  state: up  
- name: ${GROUP_2_IFNAME}
  type: ethernet
  state: up  
  mtu: 9000
  ipv4:
    address:
    - ip: ${GROUP_2_IP}
      prefix-length: ${GROUP_2_PREFIX}
    dhcp: false
    enabled: true
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
- name: ${GROUP_1_BOND}
  type: bond
  state: up
  link-aggregation:
    mode: ${GROUP_1_BOND_MODE}
    options:
      lacp_rate: ${GROUP_1_LACP_RATE}
    port:
    - ${GROUP_1_BOND_MEMBER_1}
    - ${GROUP_1_BOND_MEMBER_2}
- name: ${GROUP_1_BOND}.${GROUP_1_VLAN}
  type: vlan
  state: up
  vlan:
    base-iface: ${GROUP_1_BOND}
    id: ${GROUP_1_VLAN}
  ipv4:
    address:
    - ip: ${GROUP_1_IP}
      prefix-length: ${GROUP_1_PREFIX}
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

## outcome

### Server: bm1-1

```
interfaces:
- name: eno7
  type: ethernet
  state: up
- name: eno8
  type: ethernet
  state: up
- name: eno9
  type: ethernet
  state: up
- name: eno10
  type: ethernet
  state: up  
- name: eno11
  type: ethernet
  state: up  
  mtu: 9000
  ipv4:
    address:
    - ip: 10.30.30.65
      prefix-length: 28
    dhcp: false
    enabled: true
- name: bond0
  type: bond
  state: up
  link-aggregation:
    mode: 802.3ad
    options:
      lacp_rate: slow
    port:
    - eno7
    - eno8
- name: bond0.701
  type: vlan
  state: up
  vlan:
    base-iface: bond0
    id: 701
  ipv4:
    address:
    - ip: 10.10.10.10
      prefix-length: 28
    dhcp: false
    enabled: true
- name: bond1
  type: bond
  state: up
  link-aggregation:
    mode: 802.3ad
    options:
      lacp_rate: slow
    port:
    - eno9
    - eno10
- name: bond1.666
  type: vlan
  state: up
  vlan:
    base-iface: bond1
    id: 666
  ipv4:
    address:
    - ip: 10.20.20.51
      prefix-length: 24
    dhcp: false
    enabled: true
routes:
  config:
  - destination: 0.0.0.0/0
    next-hop-address: 10.10.10.14
    next-hop-interface: bond0.701
dns-resolver:
  config:
    search:
    - domain.com
    server:
    - 100.100.100.100
```

# Server: bm1-2

```
interfaces:
- name: eno7
  type: ethernet
  state: up
- name: eno8
  type: ethernet
  state: up
- name: eno9
  type: ethernet
  state: up
- name: eno10
  type: ethernet
  state: up  
- name: eno11
  type: ethernet
  state: up  
  mtu: 9000
  ipv4:
    address:
    - ip: 10.30.30.66
      prefix-length: 28
    dhcp: false
    enabled: true
- name: bond0
  type: bond
  state: up
  link-aggregation:
    mode: 802.3ad
    options:
      lacp_rate: slow
    port:
    - eno7
    - eno8
- name: bond0.701
  type: vlan
  state: up
  vlan:
    base-iface: bond0
    id: 701
  ipv4:
    address:
    - ip: 10.10.10.11
      prefix-length: 28
    dhcp: false
    enabled: true
- name: bond1
  type: bond
  state: up
  link-aggregation:
    mode: 802.3ad
    options:
      lacp_rate: slow
    port:
    - eno9
    - eno10
- name: bond1.666
  type: vlan
  state: up
  vlan:
    base-iface: bond1
    id: 666
  ipv4:
    address:
    - ip: 10.20.20.52
      prefix-length: 24
    dhcp: false
    enabled: true
routes:
  config:
  - destination: 0.0.0.0/0
    next-hop-address: 10.10.10.14
    next-hop-interface: bond0.701
dns-resolver:
  config:
    search:
    - domain.com
    server:
    - 100.100.100.100
```

# Server: bm1-3

```
interfaces:
- name: eno7
  type: ethernet
  state: up
- name: eno8
  type: ethernet
  state: up
- name: eno9
  type: ethernet
  state: up
- name: eno10
  type: ethernet
  state: up  
- name: eno11
  type: ethernet
  state: up  
  mtu: 9000
  ipv4:
    address:
    - ip: 10.30.30.67
      prefix-length: 28
    dhcp: false
    enabled: true
- name: bond0
  type: bond
  state: up
  link-aggregation:
    mode: 802.3ad
    options:
      lacp_rate: slow
    port:
    - eno7
    - eno8
- name: bond0.701
  type: vlan
  state: up
  vlan:
    base-iface: bond0
    id: 701
  ipv4:
    address:
    - ip: 10.10.10.12
      prefix-length: 28
    dhcp: false
    enabled: true
- name: bond1
  type: bond
  state: up
  link-aggregation:
    mode: 802.3ad
    options:
      lacp_rate: slow
    port:
    - eno9
    - eno10
- name: bond1.666
  type: vlan
  state: up
  vlan:
    base-iface: bond1
    id: 666
  ipv4:
    address:
    - ip: 10.20.20.53
      prefix-length: 24
    dhcp: false
    enabled: true
routes:
  config:
  - destination: 0.0.0.0/0
    next-hop-address: 10.10.10.14
    next-hop-interface: bond0.701
dns-resolver:
  config:
    search:
    - domain.com
    server:
    - 100.100.100.100
```

[[Back]](./README.md)