## 1. STP (Spanning Tree Protocol)

### Definition
Spanning Tree Protocol (STP) is a Layer 2 protocol used to prevent switching loops in Ethernet networks by creating a loop-free logical topology.

### Standard
- IEEE 802.1D

### Objectives
- Prevent switching loops
- Avoid broadcast storms
- Prevent duplicate frame delivery
- Maintain network stability

### Working
1. Elect a Root Bridge.
2. Determine the shortest path to the Root Bridge.
3. Block redundant paths.

### STP Port States

| State | Description |
|---------|------------|
| Blocking | Does not forward frames |
| Listening | Receives and processes BPDUs |
| Learning | Learns MAC addresses |
| Forwarding | Sends and receives traffic |
| Disabled | Administratively shut down |

---

## 2. BPDU (Bridge Protocol Data Unit)

### Definition
BPDUs are control messages exchanged between switches running STP.

### Purpose
- Elect the Root Bridge
- Exchange topology information
- Detect topology changes
- Maintain loop-free topology

### BPDU Information
- Root Bridge ID
- Sender Bridge ID
- Root Path Cost
- Port ID
- Timer Values

### Types of BPDUs

#### Configuration BPDU
Used for:
- Root Bridge election
- Path calculation
- Topology maintenance

#### Topology Change Notification (TCN) BPDU
Used to notify switches about topology changes.

---

## 3. Broadcast

### Definition
A broadcast frame is delivered to all devices within the same broadcast domain.

### Destination MAC Address

FF:FF:FF:FF:FF:FF

### Examples
- ARP Request
- DHCP Discover
- Network announcements

### Advantages
- Easy device discovery
- Simple communication mechanism

### Disadvantages
- Consumes bandwidth
- Can create broadcast storms
- Reduces network performance

---

## 4. Superior BPDU

### Definition
A Superior BPDU contains better spanning-tree information than the BPDU currently stored by a switch.

### A BPDU is Superior When It Has:
1. Lower Root Bridge ID
2. Lower Root Path Cost
3. Lower Sender Bridge ID
4. Lower Port ID

### Result
- Switch updates its STP database.
- Port roles may change.
- Network recalculates the spanning tree if necessary.

---

## 5. Root Bridge

### Definition
The Root Bridge is the central switch in an STP topology and serves as the reference point for all path calculations.

### Election Criteria
The switch with the lowest Bridge ID becomes the Root Bridge.

### Bridge ID Formula

Bridge ID = Priority + MAC Address

### Default Priority

32768

### Characteristics
- All ports are Designated Ports.
- No Root Port exists on the Root Bridge.
- Every other switch determines the best path toward it.

### Importance
- Central reference point for STP
- Determines traffic flow paths
- Maintains a loop-free network

---

## 6. RSTP (Rapid Spanning Tree Protocol)

### Definition
Rapid Spanning Tree Protocol (RSTP) is an improved version of STP that provides much faster convergence after topology changes.

### Standard
- IEEE 802.1w

### Benefits
- Faster convergence
- Reduced downtime
- Improved network availability

### RSTP Port Roles

| Port Role | Function |
|------------|----------|
| Root Port | Best path to Root Bridge |
| Designated Port | Forwards traffic on a segment |
| Alternate Port | Backup path to Root Bridge |
| Backup Port | Backup for Designated Port |

### RSTP Port States

| State | Function |
|---------|---------|
| Discarding | Not forwarding traffic |
| Learning | Learning MAC addresses |
| Forwarding | Sending and receiving frames |

### Convergence Time
- Usually less than 10 seconds
- Often 1–6 seconds in practical networks

---

## 7. Fast Ethernet

### Definition
Fast Ethernet is an Ethernet technology that operates at 100 Mbps.

### Standard
- IEEE 802.3u

### Features
- Speed of 100 Mbps
- Supports full-duplex communication
- Backward compatible with Ethernet
- Supports copper and fiber media

### Fast Ethernet Standards

| Standard | Medium | Maximum Distance |
|----------|---------|------------------|
| 100BASE-TX | Cat5 UTP Cable | 100 m |
| 100BASE-T4 | Cat3 UTP Cable | 100 m |
| 100BASE-FX | Fiber Optic Cable | Up to 2 km |

### Duplex Modes

#### Half Duplex
- Uses CSMA/CD
- Communication in one direction at a time

#### Full Duplex
- Simultaneous transmission and reception
- No collisions

### Advantages
- Faster than traditional Ethernet
- Cost-effective
- Easy implementation

---

# STP vs RSTP Comparison

| Feature | STP | RSTP |
|----------|-----|------|
| Standard | IEEE 802.1D | IEEE 802.1w |
| Convergence Time | 30–50 sec | <10 sec |
| Port States | 5 | 3 |
| Recovery Speed | Slow | Fast |
| Network Availability | Lower | Higher |
| Efficiency | Lower | Higher |

---


# Important Formulas and Values

Bridge ID = Priority + MAC Address

Default Bridge Priority = 32768

Broadcast MAC Address = FF:FF:FF:FF:FF:FF

STP Standard = IEEE 802.1D

RSTP Standard = IEEE 802.1w

Fast Ethernet Standard = IEEE 802.3u

Fast Ethernet Speed = 100 Mbps
