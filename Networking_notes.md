# Networking Notes

This document summarises the key networking concepts covered throughout the Networking module.

---

## 1. Networking Fundamentals

A **computer network** is a group of connected devices that can communicate and exchange data.

Networks allow devices to:

- Communicate with each other
- Share files and resources
- Access websites and online services
- Connect to applications and transfer data

### LAN

A **Local Area Network (LAN)** connects devices within a relatively small area, such as a home, office or school.

### WAN

A **Wide Area Network (WAN)** covers a much larger geographical area and can connect multiple LANs together.

The Internet is an example of a WAN.

### Switch

A switch connects devices within the same local network.

It uses **MAC addresses** to help send data to the correct device within the LAN.

### Router

A router connects different networks together and directs traffic between them.

Routers use **IP addresses** to determine where packets need to be sent.

### Firewall

A firewall monitors and controls incoming and outgoing network traffic.

It acts as a security layer by allowing or blocking traffic based on configured rules.

---

## 2. IP Addresses

An **IP address** is used to identify a device on a network so that devices can locate and communicate with each other.

There are two main versions of IP:

### IPv4

IPv4 addresses contain **32 bits**.

They are divided into four sections called **octets**, with each octet containing 8 bits.

Example:

```text
192.168.1.10
```

### IPv6

IPv6 addresses contain **128 bits**, providing a much larger number of available addresses than IPv4.

### MAC Addresses

A **MAC address** identifies a device's network interface and is mainly used for communication within a local network.

A simple way of distinguishing the two is:

- **IP address** → identifies and routes devices across networks
- **MAC address** → identifies devices/interfaces on the local network

---

## 3. Ports and Protocols

### Ports

Ports are logical endpoints used to identify which application or service network traffic should be delivered to.

Some common ports include:

| Port | Service |
|---|---|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |

### Protocols

Protocols are sets of rules that determine how data is transmitted between devices.

Two important transport protocols are **TCP** and **UDP**.

### TCP

**Transmission Control Protocol (TCP)** is connection-oriented and focuses on reliable communication.

TCP:

- Establishes a connection before sending data
- Ensures data arrives in the correct order
- Retransmits lost data
- Provides error and flow control

### UDP

**User Datagram Protocol (UDP)** is connectionless.

Unlike TCP, UDP does not establish a connection beforehand or guarantee that every piece of data will arrive.

This reduces overhead and makes UDP faster for applications where speed is important.

---

## 4. The OSI Model

The **OSI model** explains network communication using seven different layers.

Each layer has a specific responsibility.

### Layer 7 - Application

Provides network services to applications.

Examples include:

- HTTP/HTTPS
- DNS
- SSH

### Layer 6 - Presentation

Handles how data is represented.

Responsibilities include:

- Data formatting
- Encryption and decryption
- Compression

### Layer 5 - Session

Establishes, manages and terminates communication sessions between devices.

### Layer 4 - Transport

Provides end-to-end communication.

This layer includes:

- TCP
- UDP
- Ports
- Segmentation and reassembly

### Layer 3 - Network

Responsible for moving packets between different networks.

This layer handles:

- IP addressing
- Routing

Routers operate at this layer.

### Layer 2 - Data Link

Handles communication across the local network.

This layer uses:

- MAC addresses
- Frames

Switches mainly operate at this layer.

### Layer 1 - Physical

Responsible for physically transmitting raw bits.

This includes:

- Cables
- NICs
- Hubs
- Repeaters
- Physical signals

---

## 5. TCP/IP Model

The **TCP/IP model** is another model used to describe network communication.

It contains four layers:

### Application

Provides network services to applications.

Examples include HTTP, TLS and DNS.

### Transport

Handles end-to-end communication using protocols such as TCP and UDP.

### Internet

Responsible for IP addressing and routing packets between networks.

### Network Access

Handles communication across the physical/local network using technologies such as Ethernet and WLAN.

---

## 6. DNS

**DNS (Domain Name System)** translates human-readable domain names into IP addresses.

Instead of users having to remember an IP address, they can use a domain name.

For example:

```text
example.com → IP address
```

### DNS Resolution

A DNS request can pass through several different servers before the correct IP address is returned.

A simplified process is:

```text
Client
  ↓
DNS Resolver
  ↓
Root Server
  ↓
TLD Server
  ↓
Authoritative Name Server
```

### DNS Resolver

The resolver receives the request from the client.

It can first check its cache to see if it already knows the answer.

If not, it continues the DNS lookup process.

### Root Server

The root server directs the resolver towards the appropriate **Top-Level Domain (TLD)** server.

### TLD Server

The TLD server handles extensions such as `.com`, `.org` and `.co.uk`.

It directs the resolver towards the correct authoritative name server.

### Authoritative Name Server

The authoritative name server stores the actual DNS records for a domain and provides the requested information.

---

## 7. DNS Records

DNS information is stored as records within zone files.

Important DNS records include:

### A Record

Maps a domain or hostname to an **IPv4 address**.

### AAAA Record

Maps a domain or hostname to an **IPv6 address**.

### CNAME Record

Creates an alias by pointing one hostname to another hostname.

### MX Record

Specifies which mail server is responsible for receiving email for a domain.

### TXT Record

Stores text-based information for a domain and can be used for verification, SPF and other metadata.

### NS Record

Identifies the authoritative name servers responsible for a DNS zone.

---

## 8. Routing

**Routing** is the process of determining the path data should take across networks.

A router examines the destination IP address and uses its **routing table** to decide where a packet should be sent next.

### Routing Table

A routing table contains routes that a router or device can use to reach different networks.

### Next Hop

The **next hop** is the next router or destination that a packet should be forwarded to.

### Default Route

A default route is used when there is no more specific route available.

IPv4 default route:

```text
0.0.0.0/0
```

### Default Gateway

The default gateway is normally the router a device sends traffic to when the destination is outside its local network.

### Static vs Dynamic Routing

**Static routing** uses routes that are manually configured and remain fixed.

**Dynamic routing** allows routes to be learned and adjusted automatically using routing protocols.

Examples covered include:

- **OSPF** - Uses network information and costs to calculate routes.
- **BGP** - Exchanges routing information and allows routing decisions based on paths and policies.

---

## 9. Binary

Computers represent data using **binary**, which consists of:

```text
0 and 1
```

Each individual binary digit is called a **bit**.

An IPv4 address contains 32 bits divided into four 8-bit octets.

The values of the eight positions within an octet are:

```text
128  64  32  16  8  4  2  1
```

For example:

```text
192 = 11000000
```

Understanding binary helps explain how IP addressing, subnet masks and subnetting work.

---

## 10. CIDR

**CIDR (Classless Inter-Domain Routing)** is used for allocating IP addresses and routing networks.

CIDR notation includes an IP address followed by a prefix length.

Example:

```text
192.168.1.0/24
```

The `/24` means that the first **24 bits** represent the network portion of the address.

Since IPv4 contains 32 bits:

```text
Host bits = 32 - prefix length
```

Therefore a `/24` leaves 8 bits for the host portion.

---

## 11. Subnetting

**Subnetting** is the process of dividing a larger network into smaller networks.

This allows IP address ranges to be organised into separate subnets.

Important parts of a subnet include:

- Network address
- Host addresses
- Broadcast address
- Prefix length

The network address is the first address within the subnet.

The broadcast address is traditionally the final address within the subnet.

Addresses between these can be used for hosts.

### Subnetting Formulas

```text
Host bits = 32 - prefix length

Total addresses = 2 ^ host bits

Usable hosts = total addresses - 2
```

---

## 12. NAT

**Network Address Translation (NAT)** translates between private and public IP addresses.

Devices inside a private network can use private IP addresses while NAT allows them to communicate with external networks such as the Internet.

A simplified example is:

```text
Private Network
      ↓
     NAT
      ↓
Public IP Address
      ↓
   Internet
```

### Static NAT

Static NAT creates a fixed mapping between one private IP address and one public IP address.

### Dynamic NAT

Dynamic NAT can map private addresses to available addresses from a pool of public IP addresses.

### PAT

**Port Address Translation (PAT)** allows multiple devices to share a single public IP address.

Different port mappings allow the router to keep track of which internal connection the traffic belongs to.

---

## 13. Network Troubleshooting

Network troubleshooting is the process of identifying, diagnosing and resolving network problems.

Common network issues can include:

- Loss of connectivity
- Slow network performance
- IP address conflicts
- DNS failures

Troubleshooting should be approached logically rather than randomly changing configurations.

For a connectivity problem, checks can include:

1. Check physical/network connections
2. Check network configuration
3. Check IP addressing
4. Test whether the destination can be reached
5. Check the route traffic is taking
6. Check whether DNS is resolving correctly

---

## 14. Cloud Networking

Cloud networking applies networking concepts within cloud environments.

It allows cloud resources such as servers to communicate with each other, private networks and the Internet.

Some important cloud networking components include:

### VPC

A **Virtual Private Cloud (VPC)** provides an isolated virtual network within a cloud environment.

### Subnets

Subnets divide a larger cloud network into smaller network ranges.

### Gateways

Gateways allow traffic to move between different networks.
