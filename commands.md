# Networking Commands

This file contains the key commands used throughout the Networking module and AWS practical.

---

## IP Address Information

### `ip addr`

Displays network interfaces and their IP addresses.

```bash
ip addr
```

---

## Ping

Tests connectivity between your device and another device or server.

```bash
ping <IP-ADDRESS-OR-DOMAIN>
```

Example:

```bash
ping example.com
```

Stop the ping using:

```text
Ctrl + C
```

---

## Traceroute

Shows the path packets take towards a destination.

```bash
traceroute <DOMAIN>
```

Example:

```bash
traceroute example.com
```

---

## DNS Lookup

### `nslookup`

Queries DNS information for a domain.

```bash
nslookup <DOMAIN>
```

Example:

```bash
nslookup example.com
```

---

## DNS Records

### `dig`

Queries DNS records for a domain.

```bash
dig ns <DOMAIN>
```

For a shorter output:

```bash
dig +short ns <DOMAIN>
```

---

## Network Connections

### `ss`

Displays information about network sockets and connections.

```bash
ss
```

To display listening TCP and UDP ports:

```bash
ss -tuln
```

---

## Netstat

Displays network connections and networking information.

```bash
netstat
```

---

# AWS EC2 & NGINX Commands

## Set SSH Key Permissions

Restricts permissions on an SSH private key.

```bash
chmod 400 <KEY-FILE>.pem
```

> Private SSH keys should never be committed or uploaded to a public GitHub repository.

---

## Connect to an EC2 Instance

Connect to a remote EC2 instance using SSH:

```bash
ssh -i "<KEY-FILE>.pem" ubuntu@<EC2-PUBLIC-DNS>
```

---

## Update Package Information

Refresh the available Ubuntu package information:

```bash
sudo apt update
```

---

## Install NGINX

Install the NGINX web server:

```bash
sudo apt install nginx
```

---

## Enable NGINX

Configure NGINX to automatically start when the server boots:

```bash
sudo systemctl enable nginx
```

---

## Start NGINX

Start the NGINX service:

```bash
sudo systemctl start nginx
```

---

## Check NGINX Status

Check whether NGINX is running:

```bash
sudo systemctl status nginx
```

A running service should display:

```text
Active: active (running)
```

---


