# Network-Design_DPR_Class

This Schema includes Five networks, an external network for Davis Property Rentals in two Offices in Brisbane and Cairns, a public network and a private subnet for each.
For two Domain's of the network is: **DPR.bris** For the brisbane office, and **DPR.cairns** for the Cairns based office.

![Network](/NetworkImage.png)

---

## Table of Contents

- [Network-Design_DPR_Class](#network-design_dpr_class)
  - [Table of Contents](#table-of-contents)
  - [Status and Updates](#status-and-updates)
    - [End of day – 19/10/2021](#end-of-day--19102021)
    - [Day of 26/10/2021](#day-of-26102021)
  - [- [ ] Reconfigure external routers with new respective LAN addressess (can be wiped instead of reconfigured)](#----reconfigure-external-routers-with-new-respective-lan-addressess-can-be-wiped-instead-of-reconfigured)
  - [Tasks and Objectives](#tasks-and-objectives)
  - [External Network IP Scheme](#external-network-ip-scheme)
  - [Cairns IP Scheme](#cairns-ip-scheme)
    - [Cairns Private Range](#cairns-private-range)
    - [Cairns Public Range](#cairns-public-range)
  - [Brisbane IP Scheme](#brisbane-ip-scheme)
    - [Brisbane Private Range](#brisbane-private-range)
    - [Brisbane Public Range](#brisbane-public-range)
  - [Hardware Specifications](#hardware-specifications)
  - [Services](#services)
  - [Network Diagram](#network-diagram)
  - [Rack Diagram](#rack-diagram)
  - [PfSense Configurations](#pfsense-configurations)
    - [Tips](#tips)
    - [Network, IP Address and Gateway](#network-ip-address-and-gateway)
    - [External Network](#external-network)
      - [DPR.bris](#dprbris)
      - [DPR.cairns](#dprcairns)
    - [Port Forwarding Rules](#port-forwarding-rules)
      - [DPR.bris Port Forwarding Settings](#dprbris-port-forwarding-settings)
      - [DPR.cairns Port Forwarding Settings](#dprcairns-port-forwarding-settings)

---

## Status and Updates

Within this section, the status of the network and updates will be tracked weekly.

### End of day – 19/10/2021

- Main DC – configured and ready for physical install
- Remote Access available through RDP on 172 network
- ESXi server for WSUS and FS configured and ready for physical install and Remote/Web access

### Day of 26/10/2021
- [ ] Install servers into rack
- [ ] remote into Main DC and configure AD DS & DNS
- [ ] access ESXI through web interface & install server 2019 VM (Name= DPRWSUS-172.20.28.147/roles=WSUS\FS)
- [ ] wipe & reconfigure site servers with ESXI 7.0
- [ ] Reconfigure external routers with new respective LAN addressess (can be wiped instead of reconfigured)
---

## Tasks and Objectives

This section covers tasks and objectives yet to be achieved towards the completion of the network plan

| #          | Task |
| ---------- | ------ |
|   |**ToDo** **26/10** |
| 1 | ~~Install servers into rack~~ |
| 2 | ~~remote into Main DC and configure roles~~ |
| 3 | access ESXI through web interface and install server 2019 VM |
| 4 | name DPRWSUS = 172.20.28.147, roles = WSUS, FS  |
| 5 | wipe and re configure site servers with ESXI 7.0  |
| 6 | configure external routers with new LAN addresses  ( can be wiped prior) |

---

## External Network IP Scheme

| Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 172.20.28.0 <=> 172.20.28.255 | 172.20.28.254 | 255.255.255.0 | /24 |

| Exclusion Range |
| --------------- |
| 172.20.28.200 <=> 172.20.28.205 |

| IP Address     | Device                 | Network            | Description         |
| -------------- | ---------------------- | ------------------ | ------------------- |
| 172.20.28.200 | Top level DC | 172.20.28.0/24 | Main DC head of tree |
| 172.20.28.201 | ESXi 7 | 172.20.28.0/24 | Main ESXi |
| 172.20.28.202 | Windows Server 2016 | 172.20.28.0/24 | WSUS and FS |
| 172.20.28.254 | Gateway |

---

## Cairns IP Scheme

### Cairns Private Range

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.2.128 <=> 192.168.2.255 | 192.168.2.254 | 255.255.255.128 | /25 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| 192.168.2.254 | SubNet Router | 192.168.2.128 | LAN |
| 192.168.2.253 | Main Switch | 192.168.2.128 | Main Switch |
| 192.168.2.130 | DC2 | 192.168.2.128 | Backup DC |
| 192.168.2.129| DC1 | 192.168.2.128 | Main DC |

### Cairns Public Range

| Main Network Range | Gateway | NetMask | CIDR |
| --------------------------------- | -------------- | --------------- | --- |
| 192.168.2.0 <=> 192.168.2.126 | 192.168.2.126 | 255.255.255.128 | /25 |

| DHCP Range Start | DHCP Range End |
| ---------------- | -------------- |
| 192.168.2.20 | 192.168.2.110 |

| IP Address     | Device                 | Network            | Description         |
| -------------- | ---------------------- | ------------------ | ------------------- |
| 192.168.2.126 | Router | 192.168.2.0 | Main PfSense Router |
| 192.167.2.125 | Wireless Router | 192.168.2.0 | Access Point |
| 192.168.2.124 | Main Switch | 192.168.2.0 | Main Switch |
| 192.167.2.123 | Access Switch | 192.168.2.0 | Access Switch |
| 192.168.2.122 | IDS | 192.168.2.0 | Intrusion Detection System |
| 192.168.2.121 | WebServer | 192.168.2.0 | Linux External WebServer |
| 192.168.2.120 | HMail Server | 192.168.2.0 | External Mail Server |
| 192.168.2.6 | VMware Centre | 192.168.2.0 | Clustering 11 and 12 |
| 192.168.2.4 | ESXi 7 | 192.168.2.0 | Main ESXi 3 |
| 192.168.2.3 | ESXi 7 | 192.168.2.0 | Main ESXi 2 |
| 192.168.2.2 | ESXi 7 | 192.168.2.0 | Hosting External Email and Web |
| 192.168.2.1 | SubNet Router | 192.168.2.0 | WAN |

---

## Brisbane IP Scheme

### Brisbane Private Range

| Main Network Range | Gateway | NetMask | CIDR |
| --------------------------------- | -------------- | --------------- | --- |
| 192.168.1.128 <=> 192.168.1.255 | 192.168.1.254 | 255.255.255.128 | /25 |

| IP Address     | Device                 | Network            | Description         |
| -------------- | ---------------------- | ------------------ | ------------------- |
| 192.168.1.254 | Router | 192.168.1.128 | LAN |
| 192.168.1.253 | Main Switch | 192.168.1.128 | Main Switch |
| 192.168.1.129 | DC2 | 192.168.1.128 | Backup DC |
| 192.168.1.128 | DC1 | 192.168.1.128 | Main DC |

### Brisbane Public Range

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.1.0 <=> 192.168.1.126 | 192.168.1.126 | 255.255.255.128 | /25 |

| DHCP Range Start | DHCP Range End |
| ---------------- | -------------- |
| 192.168.1.20 | 192.168.1.110 |

| IP Address | Device  | Network    | Description |
| ----------| -------  | ---------- | ----------- |
| 192.168.1.126 | Router | 192.168.1.0 | PfSense Main Router |
| 192.167.2.125 | Wireless Router | 192.168.2.0 | Access Point |
| 192.168.1.124 | Main Switch | 192.168.1.0 | Main Switch |
| 192.167.1.123 | Access Switch | 192.168.1.0 | Access Switch |
| 192.168.1.122 | IDS | 192.168.1.0 | Intrusion Detection System |
| 192.168.1.121 | WebServer | 192.168.1.0 | External Web Server |
| 192.168.1.120 | HMail Server | 192.168.1.0 | External Mail Server |
| 192.168.1.13 | VMware Centre | 192.168.1.0 | Clustering 11 and 12 |
| 192.168.1.5 | ESXi 7 | 192.168.1.0 | Main ESXi 3 |
| 192.168.1.4 | ESXi 7 | 192.168.1.0 | Main ESXi 2 |
| 192.168.1.3 | ESXi 7 | 192.168.1.0 | Guest ESXi Hosting External mail/web |
| 192.168.1.2 | VPN | 192.168.1.0 | Main VPN |
| 192.168.1.1 | SubNet Router | 192.168.1.0 | WAN |

---

## Hardware Specifications

| Device   | Specifications   | Role | Quantity |
| ---------| ---------------- | -------- | -----|
| Dell R520 | Ram: 26 GB Storage: yes  | DC2 | 1x |
| Dell R720 | Ram: 16 GB Storage: yes   | DC1 | 1x |
| Dell R230 | Ram: 16 GB Storage: 1.4 TB | WebServer | 1x |
| iMac | N/A | Terminal | 4x |
| Router | N/A | Router | 1x |
| Cisco Switch 2801 | N/A | Switch | 1x |

---

## Services

| Service  | Port | Ip Address | Description |
| -------- | ---- | ---------- | ----------- |
|   | | |  |
|   | | |  |

---

## Network Diagram

![Network Plan](https://user-images.githubusercontent.com/89438022/138798695-536097a1-4e2c-4005-9086-ca1929c168bb.png)

---

**Security Perimiter Diagram**
![Part3Complex3 security perimiter drawio](https://user-images.githubusercontent.com/89438022/138802179-d8506c78-b0e3-467b-9c01-d6b0b253993c.png)

---
## Rack Diagram

![Rack Diagram](/Rack%20Diagram/phy_diagram.png)

## PfSense Configurations

> Below will document all the changes and setup for PfSense

---

### Tips

- Rules to match port forwards, forwards to show pass instead of link
- Don't forward HTTP or port 80 until the default PfSense web app is listening on a different port
- NAT reflection should be set to **Nat + Proxy**

---

### Network, IP Address and Gateway

### External Network 

| Network | Range  | Gateway | CIDR |
| ------- | ------- | ----- | ---- |
| 172.20.28.0 | .0 - .255 | 172.20.28.254 | /24 |

#### DPR.bris

**Bris Router One, main router, Public:**
| Network | IP Address | Range  | Gateway | CIDR |
| ------- | ---------- | ------- | ----- | ---- |
| 192.168.1.0 | 192.168.1.126 | .0 - .127 | 172.20.28.x | /25 |

**Router Two, Subnet-One Router, Private:**
| Network | IP Address | Range | Gateway | CIDR |
| ------- | ---------- | ----- | ------- | ---- |
| 192.168.1.128 | 192.168.1.254 | .128 - .254| 192.168.1.254 | /25 |

---

#### DPR.cairns

**Router one, main router, Public:**
| Network | IP Address | Range  | Gateway | CIDR |
| ------- | ---------- | ------- | ----- | ---- |
| 192.168.2.0 | 192.168.2.126 | .0 - .127 | 172.20.28.x | /25 |

**Router Two, Subnet-One Router, Private:**
| Network | IP Address | Range | Gateway | CIDR |
| ------- | ---------- | ----- | ------- | ---- |
| 192.168.2.128 | 192.168.2.254 | .128 - .254| 192.168.2.254 | /25 |

---

### Port Forwarding Rules

#### DPR.bris Port Forwarding Settings

> **Main Router, Public**

| Port | Service | IP Address | Device | Protocol | Description | Source/Destination |
| ---- | ------- | ---------- | ------ | -------- | ----------- | ------------------ |
| | | | | | |
> **Subnet-One Router, Private**

| Port | Service | IP Address | Device | Protocol | Description | Source/Destination |
| ---- | ------- | ---------- | ------ | -------- | ----------- | ------------------ |
| | | | | | | |

#### DPR.cairns Port Forwarding Settings

> **Main Router, Public**

| Port | Service | IP Address | Device | Protocol | Description | Source/Destination |
| ---- | ------- | ---------- | ------ | -------- | ----------- | ------------------ |
| | | | | | |
> **Subnet-One Router, Private**

| Port | Service | IP Address | Device | Protocol | Description | Source/Destination |
| ---- | ------- | ---------- | ------ | -------- | ----------- | ------------------ |
| | | | | | | |
