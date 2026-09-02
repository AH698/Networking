# Networking

This directory documents my work from the Networking module of my DevOps learning journey. It covers the networking fundamentals I studied, the commands I worked with, and a practical AWS project where I deployed an NGINX web server and connected it to a domain using Route 53.

## What I Covered

Throughout the module I worked through the main concepts behind how devices communicate across networks, including:

- LANs and WANs
- Switches, routers and firewalls
- IPv4, IPv6 and MAC addresses
- Ports and protocols
- TCP and UDP
- The OSI and TCP/IP models
- DNS and DNS records
- Routing and routing tables
- Binary and CIDR notation
- Subnetting
- NAT and PAT
- Network troubleshooting
- Cloud networking

One of the biggest things I took from the module was understanding how these topics connect rather than seeing them as completely separate concepts.

For example, accessing a website can involve DNS resolving the domain, IP addressing and routing getting the traffic to the correct server, TCP establishing reliable communication and ports identifying the service the traffic needs to reach.

My more detailed notes can be found in [`networking-notes.md`](networking-notes.md).

---

## Commands

Alongside the theory, I worked with networking and Linux commands for checking network information, testing connectivity, investigating routes and working with remote servers.

Some of the areas I practised included:

- Checking network interfaces and IP information
- Testing connectivity
- Tracing network routes
- Querying DNS
- Checking network connections and ports
- Connecting to remote servers using SSH
- Managing an NGINX service on Linux

The commands and explanations are documented separately in [`commands.md`](commands.md).

---

# AWS Route 53 & EC2 Project

To put the networking theory into practice, I completed an AWS project where I deployed an NGINX web server on an Ubuntu EC2 instance and connected it to a domain using Amazon Route 53.

The aim was to understand what actually happens between entering a domain name in a browser and reaching a web server running in the cloud.

## What I Built

For the project I:

1. Launched an Ubuntu EC2 instance.
2. Configured the EC2 Security Group to allow the required network traffic.
3. Connected remotely to the server using SSH.
4. Installed and started NGINX.
5. Used Amazon Route 53 to manage the DNS configuration.
6. Created an A record pointing the domain to the EC2 instance's public IPv4 address.
7. Tested the domain in a browser and successfully reached the NGINX web server.

The finished setup connected several of the concepts covered during the module:

**Domain → Route 53 DNS → A Record → EC2 Public IPv4 → NGINX**

---

## AWS Services and Technologies Used

### Amazon EC2

EC2 was used to create the Ubuntu virtual server that hosted NGINX.

### Amazon Route 53

Route 53 was used for DNS. I created an A record that mapped the domain to the public IPv4 address of the EC2 instance.

### Security Groups

The EC2 Security Group controlled which traffic could reach the instance.

The main ports involved in the project were:

| Port | Service | Use |
|---|---|---|
| 22 | SSH | Remote access to the EC2 instance |
| 80 | HTTP | Access to the NGINX web server |
| 443 | HTTPS | HTTPS traffic |

### NGINX

NGINX was installed on the Ubuntu EC2 instance and used as the web server.

---

## Troubleshooting

The project also gave me some useful troubleshooting experience.

### SSH Connection

Before I could configure the server, I needed to make sure SSH access was correctly set up.

This helped reinforce the relationship between SSH, port 22, EC2 Security Groups and private key authentication.

### NGINX Installation

When I first tried to install NGINX, I received `404 Not Found` errors while Ubuntu was trying to retrieve packages.

I initially had to work out whether the issue was related to the EC2 networking configuration or the package manager.

The problem was outdated package information. Running:

```bash
sudo apt update
```

refreshed the available package information, after which NGINX installed successfully.

This was a good example of troubleshooting the actual cause of a problem rather than assuming it was a networking issue.

### Security Group Configuration

I also had to make sure the correct inbound rules were configured for the services I wanted to access.

This gave me practical experience of how ports are used to control access to services running on a cloud server.

---

## Project Result

After configuring EC2, NGINX, the Security Group and Route 53, I was able to enter the domain into a browser and successfully reach the NGINX welcome page hosted on the EC2 instance.

This confirmed that the DNS record was resolving to the server and that HTTP traffic could reach NGINX.

## Key Takeaways

This module helped me understand networking beyond just memorising definitions.

Working through IP addressing, ports, DNS, routing, subnetting and NAT gave me a better understanding of how data moves through a network.

The AWS project then gave me the opportunity to apply some of those concepts in practice by configuring a cloud server, controlling network access, working with DNS and making a web server accessible through a domain.

It also reinforced how important troubleshooting is in DevOps. Being able to work through a problem, identify where it is occurring and understand why it happened is just as important as knowing the commands needed to fix it.

