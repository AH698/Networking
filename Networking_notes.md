# Networking Notes

## Networking Fundamentals

- **LAN** - Connects devices within a local area such as a home or office.
- **WAN** - Connects networks across larger geographical areas.
- **Switch** - Connects devices within the same network and uses MAC addresses.
- **Router** - Connects different networks and routes traffic using IP addresses.
- **Firewall** - Controls incoming and outgoing network traffic based on rules.

## IP and MAC Addresses

- **IP address** - Logical address used to identify and communicate with devices across networks.
- **MAC address** - Identifies a network interface and is mainly used for communication within a local network.
- IPv4 contains **32 bits**, split into four 8-bit octets.
- IPv6 contains **128 bits**.
- Private IP addresses are used within private networks, while public IP addresses can be used across the Internet.

## Ports and Protocols

Ports identify the service/application that network traffic should reach.

Common ports:

- SSH - 22
- DNS - 53
- HTTP - 80
- HTTPS - 443

**TCP** prioritises reliable delivery of data.

**UDP** prioritises speed and does not provide the same delivery guarantees as TCP.

## OSI Model

The OSI model contains seven layers:

1. Physical - Bits and physical transmission
2. Data Link - MAC addresses and frames
3. Network - IP addresses and routing
4. Transport - TCP, UDP and ports
5. Session - Starts, manages and ends sessions
6. Presentation - Formatting, encryption and compression
7. Application - Network services such as HTTP, DNS and SSH

## DNS

DNS translates human-readable domain names into IP addresses.

A typical DNS lookup can involve:

DNS Resolver → Root Server → TLD Server → Authoritative Name Server

Important DNS records:

- **A** - Domain/hostname → IPv4 address
- **AAAA** - Domain/hostname → IPv6 address
- **CNAME** - Maps one hostname to another
- **MX** - Specifies mail servers
- **TXT** - Stores text information

## CIDR and Subnetting

CIDR notation shows how many bits identify the network.

Example:

`192.168.1.0/24`

IPv4 contains 32 bits, therefore:

`Host bits = 32 - prefix length`

Subnetting allows a larger network to be divided into smaller networks.

Important addresses include:

- Network address
- Usable host addresses
- Broadcast address

## NAT

NAT translates between private and public IP addresses, allowing devices on private networks to communicate with the Internet.

PAT allows multiple devices to share one public IPv4 address by using port mappings.

## Troubleshooting

Network troubleshooting means systematically identifying and fixing connectivity problems.

Useful commands include:

- `ping` - Test connectivity
- `ip addr` - View IP/interface information
- `traceroute` - View the route to a destination
- `nslookup` - Test DNS resolution
- `ss` - Inspect network connections and ports
