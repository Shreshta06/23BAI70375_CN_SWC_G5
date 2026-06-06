# 1. Introduction to Computer Networks

A **Computer Network** is a collection of interconnected devices that communicate and share resources.

### Objectives of Networking
- Resource Sharing
- Communication
- Data Exchange
- Internet Access
- Centralized Management

### Types of Networks

| Type | Full Form | Coverage |
|--------|------------|------------|
| PAN | Personal Area Network | Few meters |
| LAN | Local Area Network | Building/Home |
| MAN | Metropolitan Area Network | City |
| WAN | Wide Area Network | Country/World |

### Example

```
Laptop ---- Router ---- Internet
       \
        Mobile
```

---

# 2. Networking Devices

## Router

A Router connects different networks and forwards data packets between them.

### Functions
- Connects LAN to Internet
- Assigns IP addresses (DHCP)
- Routes packets
- Performs NAT (Network Address Translation)

### Example

```
Devices --> Router --> ISP --> Internet
```

### Layer
Works mainly at **OSI Layer 3 (Network Layer)**.

---

## Switch

A Switch connects devices within the same network.

### Functions
- Connects computers in LAN
- Uses MAC addresses
- Reduces network collisions
- Forwards frames efficiently

### Example

```
PC1
   \
PC2 --- Switch
   /
PC3
```

### Layer
Works mainly at **OSI Layer 2 (Data Link Layer)**.

---

# 3. Data Units in Networking

Different layers use different names for data.

| OSI Layer | Data Unit |
|------------|------------|
| Application | Data |
| Transport | Segment |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

---

## Segment

A Segment is the data unit at the **Transport Layer**.

### Features
- Contains source and destination ports
- Used by TCP
- Helps in data sequencing

### Example

```
TCP Header + Data = Segment
```

---

## Packet

A Packet is the data unit at the **Network Layer**.

### Features
- Contains source and destination IP addresses
- Routed across networks

### Example

```
IP Header + Segment = Packet
```

---

# 4. Addressing

## IP Addresses

An IP Address uniquely identifies a device on a network.

### Types

#### IPv4

32-bit address.

Example:

```
192.168.1.10
```

#### IPv6

128-bit address.

Example:

```
2001:0db8:85a3::8a2e:0370:7334
```

### Purpose

- Device identification
- Routing data across networks

---

## MAC Addresses

MAC (Media Access Control) Address is a physical hardware address assigned to a network interface.

### Example

```
00:1A:2B:3C:4D:5E
```

### Characteristics

- 48-bit address
- Unique worldwide
- Assigned by manufacturer

### Purpose

Used for communication within a local network.

---

# 5. Flow of Data on Google/Internet

Suppose you visit:

```
https://www.google.com
```

### Step 1: DNS Resolution

Browser asks DNS server:

```
www.google.com = ?
```

DNS returns an IP address.

---

### Step 2: TCP Connection

Client establishes TCP connection using:

```
Three-Way Handshake

SYN
SYN-ACK
ACK
```

---

### Step 3: TLS Handshake

Browser and server exchange encryption keys.

---

### Step 4: HTTP Request

Browser sends:

```http
GET / HTTP/1.1
Host: www.google.com
```

---

### Step 5: Routing

Data travels through:

```
Computer
   ↓
Switch
   ↓
Router
   ↓
ISP
   ↓
Internet Backbone
   ↓
Google Router
   ↓
Google Server
```

---

### Step 6: Response

Server sends webpage data back to browser.

---

# 6. OSI Model

OSI = Open Systems Interconnection Model

A conceptual framework that divides networking into 7 layers.

| Layer | Name |
|---------|---------|
| 7 | Application |
| 6 | Presentation |
| 5 | Session |
| 4 | Transport |
| 3 | Network |
| 2 | Data Link |
| 1 | Physical |

---

## Layer 7 – Application

Provides services to end users.

### Examples
- HTTP
- FTP
- DNS

### Functions
- Web browsing
- Email
- File transfer

---

## Layer 6 – Presentation

Responsible for data formatting.

### Functions
- Encryption
- Compression
- Translation

Example:

```
ASCII ↔ Unicode
```

---

## Layer 5 – Session

Manages communication sessions.

### Functions
- Session establishment
- Maintenance
- Termination

---

## Layer 4 – Transport

Provides end-to-end communication.

### Protocols
- TCP
- UDP

### Functions
- Reliability
- Flow control
- Error recovery

---

## Layer 3 – Network

Responsible for routing packets.

### Protocol
- IP

### Devices
- Router

---

## Layer 2 – Data Link

Provides node-to-node communication.

### Uses
- MAC Addressing
- Framing

### Devices
- Switch

---

## Layer 1 – Physical

Transmits raw bits.

### Examples
- Ethernet Cable
- Fiber Optics
- Radio Signals

---

# 7. Cryptography Basics

Cryptography protects information from unauthorized access.

---

## Symmetric Key Cryptography

Same key used for encryption and decryption.

### Process

```
Plaintext
   ↓
Encryption Key
   ↓
Ciphertext
   ↓
Same Key
   ↓
Plaintext
```

### Advantages
- Fast
- Efficient

### Disadvantages
- Key distribution problem

### Examples
- AES
- DES

---

## Asymmetric Key Cryptography

Uses two keys:

- Public Key
- Private Key

### Process

```
Public Key → Encrypt
Private Key → Decrypt
```

### Advantages
- Secure key exchange
- Digital signatures

### Disadvantages
- Slower than symmetric encryption

### Examples
- RSA
- ECC

---

# 8. Networking Protocols and Concepts

## MAC

MAC stands for Media Access Control.

### Purpose
Identifies devices on a LAN.

### Example

```
AA:BB:CC:DD:EE:FF
```

### Layer
Data Link Layer

---

## TCP

Transmission Control Protocol

### Features
- Connection-oriented
- Reliable
- Ordered delivery
- Error checking

### Applications
- HTTP
- HTTPS
- FTP

### Handshake

```
SYN
SYN-ACK
ACK
```

---

## UDP

User Datagram Protocol

### Features
- Connectionless
- Faster
- No delivery guarantee

### Applications
- Video Streaming
- Online Gaming
- DNS

### Comparison

| TCP | UDP |
|-------|-------|
| Reliable | Unreliable |
| Slower | Faster |
| Connection-Oriented | Connectionless |

---

## DNS

Domain Name System

Converts domain names into IP addresses.

### Example

```
google.com
      ↓
142.250.x.x
```

### Uses
- Website access
- Service discovery

---

## FTP

File Transfer Protocol

Used to transfer files between computers.

### Default Ports

| Protocol | Port |
|-----------|------|
| FTP Control | 21 |
| FTP Data | 20 |

### Uses
- Upload files
- Download files

---

## HTTP

HyperText Transfer Protocol

Used for web communication.

### Characteristics
- Stateless
- Application Layer Protocol

### Common Methods

```http
GET
POST
PUT
DELETE
```

### Default Port

```
80
```

---

## TLS

Transport Layer Security

Provides encryption and security for communication.

### Functions
- Encryption
- Authentication
- Integrity

### Used By
- HTTPS
- Secure Email
- VPNs

---

## HTTPS

HTTP Secure

HTTP running over TLS.

### Benefits
- Encryption
- Authentication
- Data Integrity

### Default Port

```
443
```

### Flow

```
Browser
   ↓
TLS Handshake
   ↓
Encrypted HTTP Communication
```

---

# 9. Remote Access and Connectivity Tools

## PuTTY

PuTTY is a free terminal emulator and SSH client.

### Features
- SSH
- Telnet
- Serial Connections
- Remote Login

### Common Usage

Connect to Linux servers remotely.

---

## SSH

Secure Shell

A secure protocol for remote system access.

### Features
- Encrypted communication
- Authentication
- File transfer (SCP/SFTP)

### Default Port

```
22
```

### Example

```bash
ssh user@server-ip
```

---

## TELNET

A protocol used for remote access.

### Features
- Command-line access
- Unencrypted communication

### Default Port

```
23
```

### Drawbacks
- No encryption
- Not secure for modern systems

### Example

```bash
telnet server-ip
```

