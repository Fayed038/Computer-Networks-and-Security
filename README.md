# Computer Networks & Security – Cisco Packet Tracer Assignment

## Project Overview
This repository contains a configured network topology in Cisco Packet Tracer for static routing between two routers, switches, PCs, and servers. The project demonstrates IP addressing, gateway configuration, and cross-network connectivity as part of my Computer Networks & Security (CSE317/318) coursework.

## Topology Diagram

![Network Topology](./Portable%20Network%20Graphic%20File(PNG).PNG)

*Figure: Network topology diagram showing routers, switches, PCs, and servers.*

## Network Design

| Device        | Interface  | IP Address      | Subnet Mask       | Notes                      |
|---------------|------------|-----------------|-------------------|----------------------------|
| Router R0     | S0/1/0     | 11.0.0.2        | 255.255.255.252   | WAN link to R1             |
| Router R0     | G0/0/0     | 192.168.10.1    | 255.255.255.0     | LAN Gateway                |
| Router R1     | S0/2/0     | 11.0.0.1        | 255.255.255.252   | WAN link to R0             |
| Router R1     | G0/0/0     | 192.168.20.1    | 255.255.255.0     | LAN Gateway                |
| PC0           | Fa0        | 192.168.10.2    | 255.255.255.0     | LAN under R0               |
| PC1           | Fa0        | 192.168.10.3    | 255.255.255.0     | LAN under R0               |
| Web Server    | Fa0        | 192.168.20.2    | 255.255.255.0     | LAN under R1               |
| FTP Server    | Fa0        | 192.168.20.3    | 255.255.255.0     | LAN under R1               |

## Configuration Details

### Router R0

```plaintext
enable
configure terminal
int s0/1/0
ip address 11.0.0.2  255.255.255.252
clock rate 64000
no shutdown
exit

int g0/0/0
ip address 192.168.10.1  255.255.255.0
no shut
exit
```

### Router R1

```plaintext
enable
config term
int s0/2/0
ip address 11.0.0.1  255.255.255.252
no shut
exit

int g0/0/0
ip address 192.168.20.1  255.255.255.0
no shut
exit
```

### Static Routing (R0 & R1)

```plaintext
ip route 0.0.0.0  0.0.0.0 s0/1/0    # R0 default route
ip route 0.0.0.0  0.0.0.0 s0/2/0    # R1 default route
```

Full configuration notes are available in [config_notes_1.txt](./config_notes_1.txt).

## Connectivity & Ping Test

All devices (PCs and Servers) can successfully ping each other across the network, verifying cross-network connectivity.

| Source  | Destination   | Type | Status      |
|---------|---------------|------|-------------|
| PC0     | Web Server    | ICMP | Successful  |
| PC0     | FTP Server    | ICMP | Successful  |
| PC1     | Web Server    | ICMP | Successful  |
| PC1     | FTP Server    | ICMP | Successful  |

*See simulation results in the Packet Tracer file.*

## Getting Started

1. Open [231465038.pkt.pkt](./231465038.pkt.pkt) in Cisco Packet Tracer.
2. Refer to [config_notes_1.txt](./config_notes_1.txt) for all router/switch CLI commands.
3. Use the topology diagram ([Portable Network Graphic File(PNG).PNG](./Portable%20Network%20Graphic%20File(PNG).PNG)) for visual reference.
4. Test connectivity by pinging between PCs and Servers.

## Files Included

- [231465038.pkt.pkt](./231465038.pkt.pkt) : Cisco Packet Tracer network file
- [config_notes_1.txt](./config_notes_1.txt) : Configuration CLI commands
- [Portable Network Graphic File(PNG).PNG](./Portable%20Network%20Graphic%20File(PNG).PNG) : Topology diagram

## Author

Submitted by [Fayed038](https://github.com/Fayed038)  
CSE318 – Computer Networks & Security Laboratory  
Assignment 1

## Instructor

**Sheikh Hasanul Banna** - (BUET)  
Lecturer, Computer Science & Engineering - (PU)

## License


This project is for educational purposes.
