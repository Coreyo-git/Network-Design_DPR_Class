# Network-Design_DPR_Class

A repository setup to document and record the plans, implementation and development of a complex Network.

This Schema includes Four networks, a public network and a private subnet.
For two Domain's of the network is: **group2.network**

![Network]())

## Table of Contents

- [Network-Design_DPR_Class](#network-design_dpr_class)
  - [Table of Contents](#table-of-contents)
  - [Status and Updates](#status-and-updates)
  - [Tasks and Objectives](#tasks-and-objectives)
  - [Cairns IP Scheme](#cairns-ip-scheme)
    - [Private Range](#private-range)
    - [Public Range](#public-range)
  - [Brisbane IP Scheme](#brisbane-ip-scheme)
    - [Private Range](#private-range-1)
    - [Public Range](#public-range-1)
  - [Hardware Specifications](#hardware-specifications)
  - [Services](#services)
  - [Network Diagram](#network-diagram)
  - [PfSense Configurations](#pfsense-configurations)
    - [Tips](#tips)
    - [Network, IP Address and Gateway](#network-ip-address-and-gateway)
      - [DPR.bris](#dprbris)
      - [DPR.cairns](#dprcairns)
    - [Port Forwarding Rules](#port-forwarding-rules)
      - [DPR.bris Port Forwarding Settings](#dprbris-port-forwarding-settings)
      - [DPR.cairns Port Forwarding Settings](#dprcairns-port-forwarding-settings)

---

## Status and Updates

Within this section, the status of the network and updates will be tracked weekly.

---

## Tasks and Objectives

This section covers tasks and objectives yet to be achieved towards the completion of the network plan

| #          | Task |
| ---------- | ------ |
|  |**ToDo** **26/10** |
| 1 | Install servers into rack |
| 2 | remote into Main DC and configure roles |
| 3 | access ESXI through web interface and install server 2019 VM |
| 4 | name DPRWSUS = 172.20.28.147, roles = WSUS, FS  |
| 5 | wipe and re configure site servers with ESXI 7.0  |
| 6 | all site servers will be server 2016 |
| 7 | configure external routers with new LAN addresses  ( can be wiped prior) |

---

## Cairns IP Scheme
### Private Range
| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.2.128 <=> 192.168.2.255 | 192.168.2.254 | 255.255.255.128 | /25 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| | | | |

### Public Range

| Main Network Range | Gateway | NetMask | CIDR |
| --------------------------------- | -------------- | --------------- | --- |
| 192.168.2.0 <=> 192.168.2.126 | 192.168.2.126 | 255.255.255.128 | /25 |

| IP Address     | Device                 | Network            | Description         |
| -------------- | ---------------------- | ------------------ | ------------------- |
| |  |  |

## Brisbane IP Scheme
### Private Range
| Main Network Range | Gateway | NetMask | CIDR |
| --------------------------------- | -------------- | --------------- | --- |
| 192.168.1.128 <=> 192.168.1.255 | 192.168.1.254 | 255.255.255.128 | /25 |

| IP Address     | Device                 | Network            | Description         |
| -------------- | ---------------------- | ------------------ | ------------------- |
| |  |  |

### Public Range

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.1.0 <=> 192.168.1.126 | 192.168.1.126 | 255.255.255.128 | /25 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| | | | |

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

![Network Plan](https://user-images.githubusercontent.com/89438022/138798528-5112dfcb-4ef4-4a48-828a-ba77be8e0711.png)




## PfSense Configurations

> Below will document all the changes and setup for PfSense

---

### Tips

- Rules to match port forwards, forwards to show pass instead of link
- Don't forward HTTP or port 80 until the default PfSense web app is listening on a different port
- NAT reflection should be set to **Nat + Proxy**

---

### Network, IP Address and Gateway

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
