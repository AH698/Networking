# Networking Notes

These are my notes from the networking module, covering the main concepts I learnt and revised throughout the course.

## Networking Basics

A computer network allows devices to connect and communicate with each other. This allows things like file sharing, browsing the internet and applications communicating with other systems.

**LAN (Local Area Network)** - A network covering a small area, for example devices connected to the same home Wi-Fi.

**WAN (Wide Area Network)** - Covers a much larger area and can connect multiple LANs together. The internet is the biggest example of a WAN.

**Switch** - Connects devices together within the same local network and helps send data to the correct device.

**Router** - Connects different networks together and directs traffic between them.

**Firewall** - Monitors incoming and outgoing network traffic and can allow or block traffic based on its rules.

---

## IP and MAC Addresses

An IP address allows devices on a network to locate and communicate with each other.

IPv4 addresses are 32 bits long and are split into four 8-bit sections called octets.

For example:

`192.168.1.10`

IPv6 addresses are 128 bits long, which allows for far more addresses than IPv4.

A MAC address is used to identify a network interface on a local network. One of the main differences I learnt is that MAC addresses are used for local network communication, while IP addresses allow traffic to be sent between networks.

---

## Ports and Protocols

Ports are logical endpoints that identify which service or application traffic is meant for.

Some of the main ports to remember are:

- SSH - 22
- DNS - 53
- HTTP - 80
- HTTPS - 443

Protocols are basically rules for how data is communicated between devices.

### TCP

TCP is connection-oriented and focuses on making sure data is delivered reliably and in the correct order.

Before sending data, TCP establishes a connection. If data is lost during transmission it can be retransmitted.

### UDP

UDP is connectionless and doesn't provide the same delivery guarantees as TCP.

Because it doesn't have the same checks as TCP, it has less overhead and can be faster. This makes it useful when speed is more important than making sure every piece of data arrives.

---

## OSI Model

The OSI model breaks network communication down into seven layers.

### 1. Physical
Deals with the actual transmission of raw bits. This includes things like cables, NICs, hubs, repeaters and signals.

### 2. Data Link
Handles communication on the local network. This is where MAC addresses and frames come in. Switches mainly work at this layer.

### 3. Network
Handles IP addresses and routing. Routers use this layer to move packets between different networks.

### 4. Transport
Handles end-to-end communication. TCP and UDP work here, along with ports. Data can also be broken into smaller segments and put back together.

### 5. Session
Starts, manages and ends communication sessions between devices.

### 6. Presentation
Deals with how the data is presented. This includes formatting, encryption/decryption and compression.

### 7. Application
The layer closest to the applications we actually use. Protocols and services such as HTTP, HTTPS, DNS and SSH work here.

---

## TCP/IP Model

The TCP/IP model has four layers instead of seven:

- **Application** - Includes things such as HTTP, TLS and DNS.
- **Transport** - TCP and UDP.
- **Internet** - IP addressing and routing.
- **Network Access** - Handles communication over the actual network, such as Ethernet and Wi-Fi.

The TCP/IP model groups some of the OSI layers together but covers the same general process of getting data from one device to another.

---

## DNS

DNS stands for Domain Name System. Its job is to translate domain names that humans can easily remember into IP addresses that computers can use.

For example, when someone enters a website domain, DNS is used to find the IP address associated with it.

There are a few important parts involved in a DNS lookup:

**DNS Resolver** - Receives the request and checks whether it already has the answer cached. If it doesn't, it starts looking for the answer.

**Root Server** - Points the resolver towards the correct TLD server.

**TLD Server** - Deals with top-level domains such as `.com`, `.org` and `.co.uk` and points the resolver towards the correct authoritative name server.

**Authoritative Name Server** - Stores the DNS records for the domain and provides the requested information.

### DNS Records

Some of the main DNS records I covered were:

- **A** - Maps a domain to an IPv4 address
- **AAAA** - Maps a domain to an IPv6 address
- **CNAME** - Creates an alias that points to another hostname
- **MX** - Specifies the mail server for a domain
- **TXT** - Stores text information such as verification information
- **NS** - Identifies the authoritative name servers for a domain

---

## Routing

Routing is how data finds its way between different networks.

A router looks at the destination IP address and uses its routing table to decide where the packet should be sent next.

A routing table contains the available routes the device knows about.

The **next hop** is the next router or destination the packet needs to be sent to.

A **default route** is used when there isn't a more specific route available. For IPv4 this is written as `0.0.0.0/0`.

The **default gateway** is normally the router that a device sends traffic to when it needs to communicate outside its own local network.

I also covered two types of routing:

**Static routing** - Routes are manually configured and stay fixed.

**Dynamic routing** - Routes can change automatically using routing protocols.

OSPF and BGP are examples of dynamic routing protocols. OSPF calculates routes based on network information and costs, while BGP exchanges routing information between networks and can make decisions based on paths and policies.

---

## Binary

Binary uses just `0` and `1`, with each individual number being called a bit.

IPv4 has 32 bits in total, split into four groups of 8 bits.

The values for an 8-bit octet are:

`128 64 32 16 8 4 2 1`

For example, decimal 192 in binary is:

`11000000`

Learning binary helped make CIDR and subnetting make more sense because the prefix length is really describing how many bits belong to the network.

---

## CIDR

CIDR stands for Classless Inter-Domain Routing.

An example of CIDR notation is:

`192.168.1.0/24`

The `/24` means that 24 of the 32 bits are being used for the network part of the address. This leaves 8 bits for hosts.

To work out the host bits:

`32 - prefix length`

So for a `/24`:

`32 - 24 = 8 host bits`

---

## Subnetting

Subnetting means taking a larger network and dividing it into smaller networks.

The main things I needed to understand when working with a subnet were:

- Network address
- Broadcast address
- Usable host addresses
- Prefix length

The network address is the first address in the subnet and the broadcast address is the last.

The formulas I used were:

`Host bits = 32 - prefix length`

`Total addresses = 2 ^ host bits`

`Usable hosts = total addresses - 2`

---

## NAT

NAT stands for Network Address Translation.

It allows devices using private IP addresses to communicate with networks outside their private network by translating between private and public IP addresses.

This is useful because devices inside a home or office network can have their own private IP addresses while still being able to access the internet.

I covered three types:

**Static NAT** - One private IP is permanently mapped to one public IP.

**Dynamic NAT** - Private IPs can be translated using a pool of available public IP addresses.

**PAT (Port Address Translation)** - Multiple devices can share the same public IP address. Different port mappings are used to keep track of the different connections.

PAT is commonly how multiple devices on the same private network can access the internet through one public IPv4 address.

---

## Network Troubleshooting

Network troubleshooting is about finding the cause of a networking problem and then fixing it in a logical way rather than randomly changing things.

Some common problems include:

- No connectivity
- Slow network performance
- IP conflicts
- DNS failures

For example, if there is no connectivity I could start by checking the physical/network connection and IP configuration before moving on to checking whether other devices or destinations can be reached.

The main thing I took from troubleshooting was to work through the network step-by-step so I can narrow down where the problem is happening.

---

## Cloud Networking

The final area I covered was cloud networking.

Cloud networking uses the same networking fundamentals but applies them to resources running in cloud environments.

Some of the main components I learnt about were:

**VPC (Virtual Private Cloud)** - A virtual network used to organise and isolate cloud resources.

**Subnets** - Smaller networks created inside a larger network.

**Gateways** - Allow traffic to move between different networks.

This helped bring together topics like IP addressing, subnetting, routing and network access before moving onto the AWS practical.
