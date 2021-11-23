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

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.1.0 <=> 192.168.1.255 | 192.168.1.254 | 255.255.255.0 | /24 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.1.254 | Router | 192.168.1.0/24 | LAN |
| 192.168.1.254 | Secondary Router | 192.168.1.0/24 | Public |

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

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.3.0 <=> 192.168.3.255 | 192.168.3.254 | 255.255.255.0 | /24 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.3.254 | Router | 192.168.3.0/24 | LAN |
| 192.168.3.253 | Secondary Router | 192.168.3.0/24 | Main Switch |
