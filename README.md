# Network-Design_DPR_Class

A repository setup to document and record the plans, implementation and development of a complex Network.

This Schema includes two networks, a public network and a private subnet.
The Domain of the network is: **group2.network**

![Network]()

## Table of Contents

- [Network-Design_DPR_Class](#network-design_dpr_class)
  - [Table of Contents](#table-of-contents)
  - [Status and Updates](#status-and-updates)
  - [Tasks and Objectives](#tasks-and-objectives)
  - [Public Network IP Schema](#public-network-ip-schema)
  - [Subnet IP Schema](#subnet-ip-schema)
    - [Second Network](#second-network)
  - [Subnet 2 IP Schema](#subnet-2-ip-schema)
  - [Hardware Specifications](#hardware-specifications)
  - [Services](#services)
  - [Network Diagram](#network-diagram)
  - [PfSense Configurations](#pfsense-configurations)
    - [Tips](#tips)
    - [Network, IP Address and Gateway](#network-ip-address-and-gateway)
      - [DPR.bris](#dprbris)
      - [DPR.cairns](#dprcairns)
    - [Port Forwarding Rules](#port-forwarding-rules)

---

## Status and Updates

Within this section, the status of the network and updates will be tracked weekly.

---

## Tasks and Objectives

This section covers tasks and objectives yet to be achieved towards the completion of the network plan

| #          | Task |
| ---------- | ------ |
| **Title1** | **Insert Tasks here** |
| 1 |  |
| 2 |  |
| 3 |  |
| 4 |  |
| 5 |  |
| 6 |  |
| 7 |  |
| 8 |  |
| 9 |  |

---

## Public Network IP Schema

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.1.0 <=> 192.168.1.127 | 192.168.1.126 | 255.255.255.128 | /25 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| | | | |

---

## Subnet IP Schema

| Main Network Range | Gateway | NetMask | CIDR |
| --------------------------------- | -------------- | --------------- | --- |
| 192.168.2.128 <=> 192.168.2.255 | 192.168.2.254 | 255.255.255.128 | /25 |

| IP Address     | Device                 | Network            | Description         |
| -------------- | ---------------------- | ------------------ | ------------------- |
| |  |  |

### Second Network

| Main Network Range | Gateway | NetMask | CIDR |
| ------------------------------- | -------------- | --------------- | --- |
| 192.168.2.0 <=> 192.168.2.127 | 192.168.2.126 | 255.255.255.128 | /25 |

| IP Address | Device | Network    | Description |
| ----------| ------- | ---------- | ----------- |
| | | | |

---

## Subnet 2 IP Schema

| Main Network Range | Gateway | NetMask | CIDR |
| --------------------------------- | -------------- | --------------- | --- |
| 192.168.2.128 <=> 192.168.2.255 | 192.168.2.254 | 255.255.255.128 | /25 |

| IP Address     | Device                 | Network            | Description         |
| -------------- | ---------------------- | ------------------ | ------------------- |
| |  |  |

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

![Network Plan](/)

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

> **Main Router, Public**

| Port | Service | IP Address | Device | Protocol | Description | Source/Destination |
| ---- | ------- | ---------- | ------ | -------- | ----------- | ------------------ |
| | | | | | | 
> **Subnet-One Router, Private**

| Port | Service | IP Address | Device | Protocol | Description | Source/Destination |
| ---- | ------- | ---------- | ------ | -------- | ----------- | ------------------ |
| | | | | | | |
