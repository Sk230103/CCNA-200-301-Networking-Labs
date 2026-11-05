# Lab 01: IPv4 Static Routing Configuration

## Overview

This lab demonstrates the configuration of IPv4 static routing in a three-router network using Cisco Packet Tracer. The objective is to establish end-to-end connectivity between two LANs by manually configuring routes on Cisco routers.

## Lab Objectives

- Configure IPv4 addresses on router interfaces and end devices.
- Configure default gateways on PCs.
- Implement static routes between remote networks.
- Verify routing table entries.
- Test end-to-end connectivity using ICMP.
- Practice Cisco IOS troubleshooting commands.

## Network Topology

The network consists of three Cisco 2911 routers (R1, R2, and R3), two Cisco 2960 switches, and two PCs.

![Static Routing Network Topology](topology.png)

## IP Addressing Table

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC1 | FastEthernet0 | 192.168.1.1 | 255.255.255.0 |
| R1 | G0/1 | 192.168.1.254 | 255.255.255.0 |
| R1 | G0/0 | 192.168.12.1 | 255.255.255.0 |
| R2 | G0/0 | 192.168.12.2 | 255.255.255.0 |
| R2 | G0/1 | 192.168.13.2 | 255.255.255.0 |
| R3 | G0/0 | 192.168.13.3 | 255.255.255.0 |
| R3 | G0/1 | 192.168.3.254 | 255.255.255.0 |
| PC2 | FastEthernet0 | 192.168.3.1 | 255.255.255.0 |

**Default Gateways**

- PC1: `192.168.1.254`
- PC2: `192.168.3.254`

## Static Routing Configuration

### Router R1

```cisco
configure terminal
ip route 192.168.3.0 255.255.255.0 192.168.12.2
end
```

### Router R2

```cisco
configure terminal
ip route 192.168.1.0 255.255.255.0 192.168.12.1
ip route 192.168.3.0 255.255.255.0 192.168.13.3
end
```

### Router R3

```cisco
configure terminal
ip route 192.168.1.0 255.255.255.0 192.168.13.2
end
```

## Verification Commands

Run the following commands on the routers:

```cisco
show ip route
show ip interface brief
show running-config
```

Test connectivity from PC1 to PC2:

```text
ping 192.168.3.1
tracert 192.168.3.1
```

These tests should succeed once the IP addressing, interfaces, default gateways, and static routes are configured correctly.

## Expected Result

PC1 should communicate with PC2 through the following path:

PC1 → R1 → R2 → R3 → PC2

The routers use manually configured static routes to forward traffic between remote LANs.

## Key Learning Outcomes

- Understanding next-hop IP addresses.
- Configuring static routes using Cisco IOS.
- Reading connected and static routing entries.
- Understanding bidirectional routing requirements.
- Troubleshooting connectivity across multiple routers.

## Tools Used

- Cisco Packet Tracer
- Cisco IOS
- ICMP Ping
- Traceroute

## Lab File

`Day-11-Configuring-Static-Routes.pkt`

This Packet Tracer file contains the lab topology and is intended for hands-on configuration and testing.
