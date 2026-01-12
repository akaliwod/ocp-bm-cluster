# Nmstate variables

Every server must have 'nmstate' property defined that points to the file in the installation directory that should follow nmstate yaml syntax. 

Nmstate file may be defined with variables following "${NAME}" format; check [bonding](./bonding.md) and [single](./single.md) for reference.

The variable values can be defined per server in the following way

```
[
        {
            "hostname": "node1",
            "nmstate": "filename.yaml",
            "variables": {
              "key1": "value1",
              "key2": "value2"
            }
        }
]
```

Several variables are auto-generated per server (!) as per table below. If you define the same value in variables section, it will be overwritten.

Variable Key | Variable Value | Note
--- | --- | ---
IP | server.ip | 
PREFIX | prefix part from machine_config_gateway cidr |
GW | ip part from machine_config_gateway cidr |
VLAN | server.vlan | if defined
BOND_MEMBER_X | server.interface[X].name | if multiple interfaces
IFNAME | server.interface[0].name | if one interface
BOND | server.bond | if multiple interfaces, defaults to bond0
BOND_MODE | server.bond_mode | if multiple interfaces, defaults to 802.3ad
LACP_RATE | server.lacp_rate | if multiple interfaces, defaults to slow
DNS_SEARCH | dns_search | only if single dns search domain defined
DNS_SEARCH_N | dns_search | for every comma (,) seperated domain in dns_search
DNS_IP | dns_ip | only if single dns ip defined
DNS_IP_N | dns_ip | for every comma (,) seperated ip in dns_ip

If [interface groups](./group.md) are defined
- group refers to server.group list item
- N in GROUP_N is generated with group.id for every group

Variable Key | Variable Value | Note
--- | --- | ---
GROUP_N_IP | ip part of group.ip | if defined 
GROUP_N_PREFIX | prefix part of group.ip | if defined 
GROUP_N_VLAN | group.vlan | if defined
GROUP_N_BOND_MEMBER_X | server.interface[X].name | if multiple interfaces in group
GROUP_N_IFNAME | server.interface[0].name | if one interface in group
GROUP_N_BOND | group.bond | if multiple interfaces, defaults to bondN
GROUP_N_BOND_MODE | group.bond_mode | if multiple interfaces, defaults to 802.3ad
GROUP_N_LACP_RATE | group.lacp_rate | if multiple interfaces, defaults to slow

[[Back]](./README.md)