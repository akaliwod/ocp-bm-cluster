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
BOND_MEMBER_1 | server.interface[0].name | if two interfaces
BOND_MEMBER_2 | server.interface[1].name | if two interfaces
IFNAME | server.interface[0].name | if one interface
BOND | server.bond | if two interfaces, defaults to bond0
BOND_MODE | server.bond_mode | if two interfaces, defaults to 802.3ad
LACP_RATE | server.lacp_rate | if two interfaces, defaults to slow
DNS_SEARCH | dns_search | only if single dns search domain defined
DNS_SEARCH_N | dns_search | for every comma (,) seperated domain in dns_search
DNS_IP | dns_ip | only if single dns ip defined
DNS_IP_N | dns_ip | for every comma (,) seperated ip in dns_ip

[[Back]](./README.md)