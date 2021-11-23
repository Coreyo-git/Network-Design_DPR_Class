# Network Map

## Brisbane Network

### Brisbane Domain: domainHere

### Brisbane Public

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.2.0 <=> 192.168.2.3 | 192.168.2.2 | 255.255.255.252 | /30 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| **192.168.1.253** | **Secondary Router** | **192.168.2.0/30** | **Priv/WAN** IP address  |
| 192.168.2.2 | Secondary Router | 192.168.2.0/30 | LAN |
| 192.168.2.1 | Web Server | 192.168.2.0/30 | Main Switch |

### Brisbane Private

#### DHCP RANGE

| START | END |
| ----- | --- |
|192.168.1.20 <=|=> 192.168.1.200 |

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.1.0 <=> 192.168.1.255 | 192.168.1.254 | 255.255.255.0 | /24 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.1.254 | Router | 192.168.1.0/24 | LAN |
| 192.168.1.253 | Secondary Router | 192.168.1.0/24 | Public |
| 192.168.1.252 | WiFi Router | 192.168.1.0/24 | WiFi |
| 192.168.1.251 | Main Switch | 192.168.1.0/24 | Switch |
| 192.168.1.250 | ESXI host 3 | 192.168.1.0/24 | ESXI 3 |
| 192.168.1.249 | ESXI host 2 | 192.168.1.0/24 | ESXI 2 |
| 192.168.1.248 | ESXI host 1 | 192.168.1.0/24 | ESXI |
| 192.168.1.247 | vCenter Server | 192.168.1.0/24 | vCenter |
| 192.168.1.14 | Workstation 4 | 192.168.1.0/24 | Wk1 |
| 192.168.1.13 | Workstation 3 | 192.168.1.0/24 | Wk1 |
| 192.168.1.12 | Workstation 2 | 192.168.1.0/24 | Wk1 |
| 192.168.1.11 | Workstation 1 | 192.168.1.0/24 | Wk1 |
| 192.168.1.8 | WSUS | 192.168.1.0/24 | WSUS |
| 192.168.1.7 | IPS | 192.168.1.0/24 | IPS |
| 192.168.1.6 | Hmail Server | 192.168.1.0/24 | Email |
| 192.168.1.5 | RRAS | 192.168.1.0/24 | RRAS |
| 192.168.1.4 | IIS | 192.168.1.0/24 | IIS |
| 192.168.1.3 | File Server | 192.168.1.0/24 | FS1 |
| 192.168.1.2 | DC-2 | 192.168.1.0/24 | DC-2 |
| 192.168.1.1 | DC-1 | 192.168.1.0/24 | DC-1 |

## Carins Network

### Cairns Domain: domainHere

### Carins Public

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.4.0 <=> 192.168.4.3 | 192.168.4.2 | 255.255.255.252 | /30 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| **192.168.3.253** | Secondary Router | 192.168.3.254 | **Priv/WAN** IP address  |
| 192.168.4.2 | Secondary Router | 192.168.3.254 | LAN |
| 192.168.4.1 | Web Server | 192.168.4.2 | Main Switch |

### Carins Private

#### Cairns DHCP RANGE

| START | END |
| ----- | --- |
|192.168.1.20 <=|=> 192.168.1.200 |

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.3.0 <=> 192.168.3.255 | 192.168.3.254 | 255.255.255.0 | /24 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.3.254 | Router | 192.168.3.0/24 | LAN |
| 192.168.3.253 | Secondary Router | 192.168.3.0/24 | Public |
| 192.168.3.252 | WiFi Router | 192.168.3.0/24 | WiFi |
| 192.168.3.251 | Main Switch | 192.168.3.0/24 | Switch |
| 192.168.3.250 | ESXI host 3 | 192.168.3.0/24 | ESXI 3 |
| 192.168.3.249 | ESXI host 2 | 192.168.3.0/24 | ESXI 2 |
| 192.168.3.248 | ESXI host 1 | 192.168.3.0/24 | ESXI |
| 192.168.3.247 | vCenter Server | 192.168.3.0/24 | vCenter |
| 192.168.3.14 | Workstation 4 | 192.168.3.0/24 | Wk1 |
| 192.168.3.13 | Workstation 3 | 192.168.3.0/24 | Wk1 |
| 192.168.3.12 | Workstation 2 | 192.168.3.0/24 | Wk1 |
| 192.168.3.11 | Workstation 1 | 192.168.3.0/24 | Wk1 |
| 192.168.3.8 | WSUS | 192.168.3.0/24 | WSUS |
| 192.168.3.7 | IPS | 192.168.3.0/24 | IPS |
| 192.168.3.6 | Hmail Server | 192.168.3.0/24 | Email |
| 192.168.3.5 | RRAS | 192.168.3.0/24 | RRAS |
| 192.168.3.4 | IIS | 192.168.3.0/24 | IIS |
| 192.168.3.3 | File Server | 192.168.3.0/24 | FS1 |
| 192.168.3.2 | DC-2 | 192.168.3.0/24 | DC-2 |
| 192.168.3.1 | DC-1 | 192.168.3.0/24 | DC-1 |
