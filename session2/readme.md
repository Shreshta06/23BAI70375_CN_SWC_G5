# Computer Networks Notes: CDN, DHCP and Subnetting

## Table of Contents

- [CDN (Content Delivery Network)](#cdn-content-delivery-network)
- [DHCP (Dynamic Host Configuration Protocol)](#dhcp-dynamic-host-configuration-protocol)
- [IP Addressing Basics](#ip-addressing-basics)
- [Subnetting](#subnetting)
- [CIDR Notation](#cidr-notation)
- [VLSM](#vlsm)
- [Supernetting](#supernetting)
- [Important Formulas](#important-formulas)
- [Interview Questions](#interview-questions)

---

# CDN (Content Delivery Network)

## Definition

A CDN is a geographically distributed network of servers that delivers content from the server nearest to the user, reducing latency and improving performance.

## Why CDN?

- Faster page loading
- Reduced latency
- Reduced bandwidth consumption
- High availability
- DDoS protection
- Load balancing

## Components

### Origin Server

Stores original content.

### Edge Server

Caches frequently requested content close to users.

### DNS Server

Redirects users to the nearest edge server.

## Working

### Cache Hit

Content already exists in cache.

```
User
 ↓
Edge Server
 ↓
User
```

### Cache Miss

Content is fetched from the origin server.

```
User
 ↓
Edge Server
 ↓
Origin Server
 ↓
Edge Server
 ↓
User
```

## Types of Content

### Static Content

- Images
- CSS
- JavaScript
- Videos

### Dynamic Content

Generated on demand.

## Advantages

- Lower latency
- Reduced server load
- Better scalability
- Increased reliability

## Popular CDNs

- Cloudflare
- Akamai
- Amazon CloudFront
- Fastly

---

# DHCP (Dynamic Host Configuration Protocol)

## Definition

DHCP automatically assigns network configuration to devices.

## Information Provided

- IP Address
- Subnet Mask
- Default Gateway
- DNS Server
- Lease Time

## DORA Process

### Discover

Client broadcasts a request.

### Offer

Server offers an IP address.

### Request

Client requests the offered address.

### Acknowledge

Server confirms assignment.

### Flow

```
Client
   |
Discover
   ↓
DHCP Server
   |
Offer
   ↓
Client
   |
Request
   ↓
DHCP Server
   |
ACK
```

## Ports

| Device | Port |
|----------|------|
| Server | UDP 67 |
| Client | UDP 68 |

## Lease Renewal

- T1 = 50% of lease period
- T2 = 87.5% of lease period

## DHCP Relay Agent

Allows communication between DHCP clients and servers on different networks.

## Advantages

- Automatic IP allocation
- Prevents duplicate addresses
- Easy management

## Disadvantages

- Single point of failure
- Dependency on DHCP server

---

# IP Addressing Basics

## IPv4

32-bit address.

Example:

```
192.168.1.10
```

Structure:

```
Network ID | Host ID
```

## IP Classes

| Class | Range | Default Mask |
|---------|--------|------------|
| A | 1-126 | 255.0.0.0 |
| B | 128-191 | 255.255.0.0 |
| C | 192-223 | 255.255.255.0 |
| D | Multicast | - |
| E | Reserved | - |

## Private IP Ranges

### Class A

```
10.0.0.0 - 10.255.255.255
```

### Class B

```
172.16.0.0 - 172.31.255.255
```

### Class C

```
192.168.0.0 - 192.168.255.255
```

---

# Subnetting

## Definition

Subnetting divides a large network into smaller subnetworks.

## Advantages

- Efficient IP utilization
- Reduced broadcast traffic
- Better security
- Improved performance

## Terms

### Network Address

First address of the subnet.

### Broadcast Address

Last address of the subnet.

### Usable Hosts

Addresses between network and broadcast addresses.

## Formulas

### Number of Subnets

```
2^n
```

where `n = borrowed bits`

### Number of Hosts

```
2^h - 2
```

where `h = host bits`

---

# CIDR Notation

| Prefix | Subnet Mask |
|----------|-------------|
| /24 | 255.255.255.0 |
| /25 | 255.255.255.128 |
| /26 | 255.255.255.192 |
| /27 | 255.255.255.224 |
| /28 | 255.255.255.240 |
| /29 | 255.255.255.248 |
| /30 | 255.255.255.252 |

---

# Magic Number Method

Formula:

```
Magic Number = 256 - Interesting Octet
```

Example:

Subnet Mask:

```
255.255.255.192
```

Magic Number:

```
256 - 192 = 64
```

Subnets:

```
0
64
128
192
```

---

# Example

Network:

```
192.168.1.0/26
```

Mask:

```
255.255.255.192
```

Host bits = 6

Hosts:

```
2^6 - 2 = 62
```

Subnets:

| Network Address | Host Range | Broadcast Address |
|----------------|------------|------------------|
| 192.168.1.0 | 1-62 | 63 |
| 192.168.1.64 | 65-126 | 127 |
| 192.168.1.128 | 129-190 | 191 |
| 192.168.1.192 | 193-254 | 255 |

---

# VLSM (Variable Length Subnet Mask)

Allows different subnet sizes according to host requirements.

## Example

Requirements:

```
HR     : 50 hosts
Sales  : 25 hosts
IT     : 10 hosts
```

Allocate largest subnet first.

## Advantages

- Efficient utilization
- Less IP wastage

---

# Supernetting

Combines multiple networks into one larger network.

Example:

```
192.168.0.0/24
192.168.1.0/24
```

becomes

```
192.168.0.0/23
```

Used in route aggregation.

---

# Important Formulas

### Hosts

```
2^h - 2
```

### Subnets

```
2^n
```

### Wildcard Mask

```
255.255.255.255 - Subnet Mask
```

### Magic Number

```
256 - Interesting Octet
```

---

# Common Prefixes

| Prefix | Mask | Hosts |
|----------|------|------|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |

---

# Interview Questions

### What is a CDN?

A distributed network of servers that delivers content from the nearest server.

### What is a Cache Hit?

Content is available in cache.

### What is a Cache Miss?

Content must be fetched from the origin server.

### Explain DORA Process.

```
Discover → Offer → Request → Acknowledge
```

### Which ports are used by DHCP?

- Server : UDP 67
- Client : UDP 68

### Formula for hosts?

```
2^h - 2
```

### Formula for number of subnets?

```
2^n
```

### What is the network address?

First address of a subnet.

### What is the broadcast address?

Last address of a subnet.

### Difference between CIDR and VLSM?

| CIDR | VLSM |
|--------|------|
| Classless addressing | Variable subnet sizes |
| Used for routing | Used for efficient subnetting |

### What is Supernetting?

Combining multiple networks into one larger network to reduce routing table entries.
