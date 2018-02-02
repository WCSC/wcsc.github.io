# Learning IPv4
[Video on how to subnet](https://www.youtube.com/watch?v=POPoAjWFkGg&t=459s)

##### Private IP Address Range

| Class | Range          |
|-------|----------------|
| A     | 10.0.0.0/8     |
| B     | 172.16.0.0/12  |
| C     | 192.168.0.0/16 |

##### Subnetting Cheatsheet

| Total IPs | 32768 | 16384 | 8192 | 4096 | 2048 | 1024 | 512  | 256  | 128  | 64   | 32   | 16   | 8    | 4    | 2    | 1    |
|----|-------|-------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|
| Usable IPs | 32766 | 16382 | 8190 | 4094 | 2046 | 1022 | 510 | 254 | 126 | 62 | 30 | 14 | 6 | 2 | N/A | N/A |
| Netmask | /17   | /18   | /19  | /20  | /21  | /22  | /23  | /24  | /25  | /26  | /27  | /28  | /29  | /30  | /31  | /32  |
| Octet | 3rd   | 3rd   | 3rd  | 3rd  | 3rd  | 3rd  | 3rd | 3rd | 4th | 4th | 4th | 4th | 4th | 4th | 4th | 4th |
| Subnet | .128  | .192  | .224 | .240 | .248 | .252 | .254 | .255 | .128 | .192 | .224 | .240 | .248 | .252 | .254 | .255 |
| IPv4 | 128  | 64   | 32   | 16   | 8    | 4    | 2    | 1    | 128  | 64   | 32   | 16   | 8    | 4    | 2    | 1    |

###### Based off the cheatsheet: <a id="jump-to-section"></a>
- `192.168.0.0/24` has `256` IP addresses, one of those addresses is allocated to the Network ID, which is the first IP in the given network and another is allocated to the Broadcast, which is the last IP within the given network. Leaving `254` usuable IPv4 addresses.

```
Network ID: 192.168.0.0
Hosts: 192.168.0.1-254
Broadcast: 192.168.0.255
Subnet: 255.255.255.0

next Network ID: 192.168.1.0
```

- `192.168.0.0/30` has `4` IP addresses, one of those addresses is allocated to the Network ID, which is the first IP in the given network and another is allocated to the Broadcast, which is the last IP within the given network. Leaving `2` usuable IPv4 addresses.

```
Network ID: 192.168.0.0
Hosts: 192.168.0.1-2
Broadcast: 192.168.0.3
Subnet: 255.255.255.252

next Network ID: 192.168.0.4
```

- `192.168.0.128/30` has `4` IP addresses, one of those addresses is allocated to the Network ID, which is the first IP in the given network and another is allocated to the Broadcast, which is the last IP within the given network. Leaving `2` usuable IPv4 addresses.

```
Network ID: 192.168.0.128
Hosts: 192.168.0.129-130
Broadcast: 192.168.0.131
Subnet: 255.255.255.252

next Network ID: 192.168.0.132
```

- `192.168.0.0/20` has `4096` IP addresses, one of those addresses is allocated to the Network ID, which is the first IP in the given network and another is allocated to the Broadcast, which is the last IP within the given network. Leaving `4094` usuable IPv4 addresses.

```
Network ID: 192.168.0.0
Hosts: 192.168.0.1-15.254
Broadcast: 192.168.15.255
Subnet: 255.255.240.0

next Network ID: 192.168.16.0
```

[Back](../../)