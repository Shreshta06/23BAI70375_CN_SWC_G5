# 1. NAT (Network Address Translation)

## Definition
NAT is a technique used to translate private IP addresses into public IP addresses and vice versa.

## Purpose
- Conserves public IPv4 addresses.
- Provides basic security by hiding internal IP addresses.
- Allows multiple devices to share one public IP.

## Types of NAT

### Static NAT
- One-to-one mapping.
- One private IP ↔ One public IP.

### Dynamic NAT
- Maps private IPs to a pool of public IPs.
- Mapping changes dynamically.

### PAT (Port Address Translation)
- Also called NAT Overload.
- Many private IPs share one public IP using port numbers.

## Example

Private IP:
192.168.1.10

Public IP:
203.0.113.5

---

# 2. PAT (Port Address Translation)

## Definition
PAT translates multiple private IP addresses into a single public IP address using different port numbers.

## Advantages
- Saves public IP addresses.
- Most commonly used NAT method.
- Supports thousands of connections simultaneously.

## Example

192.168.1.2:1025 → 203.0.113.5:3001

192.168.1.3:1026 → 203.0.113.5:3002

---

# 3. ACL (Access Control List)

## Definition
ACL is a set of rules used to permit or deny network traffic.

## Purpose
- Traffic filtering
- Security implementation
- Network access control

## Types
1. Standard ACL
2. Extended ACL

---

# 4. Standard ACL

## Definition
Filters traffic based only on Source IP Address.

## ACL Number Range

1 – 99

1300 – 1999

## Syntax

access-list 10 permit 192.168.1.0 0.0.0.255

## Characteristics
- Checks source IP only.
- Usually placed near the destination.

## Example

access-list 1 deny 192.168.1.0 0.0.0.255

access-list 1 permit any

---

# 5. Extended ACL

## Definition
Filters traffic using:
- Source IP
- Destination IP
- Protocol
- Port Number

## ACL Number Range

100 – 199

2000 – 2699

## Syntax

access-list 101 permit tcp any any eq 80

## Characteristics
- More precise filtering.
- Usually placed near the source.

## Example

access-list 101 permit tcp any any eq 80

access-list 101 deny ip any any

---

# 6. ACL Ranges (Important for Exams)

## Standard ACL Range

1 – 99

1300 – 1999

## Extended ACL Range

100 – 199

2000 – 2699

### Easy Trick

1–99 = Standard ACL

100–199 = Extended ACL

---

# 7. Telnet

## Definition
Telnet is a remote login protocol used to access and manage network devices.

## Port Number

TCP Port 23

## Features
- Remote device management.
- Command-line access.

## Disadvantage
- Data transmitted in plain text.
- Username and password are not encrypted.

## Basic Configuration

line vty 0 4

password cisco

login

transport input telnet

---

# 8. VLAN (Virtual Local Area Network)

## Definition
A VLAN is a logical grouping of devices within a switch regardless of physical location.

## Benefits
- Reduces broadcast traffic.
- Improves security.
- Simplifies management.
- Creates separate broadcast domains.

## Example VLANs

VLAN 10 → HR Department

VLAN 20 → Finance Department

VLAN 30 → Sales Department

## VLAN Creation

Switch(config)# vlan 10

Switch(config-vlan)# name HR

## Assign Port to VLAN

Switch(config)# interface fa0/1

Switch(config-if)# switchport mode access

Switch(config-if)# switchport access vlan 10

---

# Important Values

NAT = Network Address Translation

PAT = Port Address Translation

Telnet Port = 23

Standard ACL = 1–99, 1300–1999

Extended ACL = 100–199, 2000–2699

VLAN = Virtual Local Area Network
