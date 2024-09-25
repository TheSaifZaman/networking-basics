# Networking Basics Cheatsheet

## OSI Model Layers

1. **Physical**: Hardware, cables, signals
2. **Data Link**: Frames, MAC addresses, switches
3. **Network**: IP addresses, routers
4. **Transport**: TCP, UDP, ports
5. **Session**: Session establishment, maintenance, termination
6. **Presentation**: Data formatting, encryption
7. **Application**: HTTP, FTP, SMTP

## TCP/IP Model Layers

1. **Network Access**: Ethernet, Wi-Fi
2. **Internet**: IP, ICMP
3. **Transport**: TCP, UDP
4. **Application**: HTTP, FTP, SMTP

## TCP vs UDP

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable | Unreliable |
| Ordering | Ordered delivery | No guaranteed order |
| Speed | Slower | Faster |
| Use case | Accuracy-critical apps | Speed-critical apps |
| Header size | 20 bytes | 8 bytes |

## Common Networking Commands

- `ping`: Test reachability of a host
  ```
  ping google.com
  ```

- `traceroute`: Display route to a host
  ```
  traceroute google.com
  ```

- `ifconfig`: Configure network interface (old)
  ```
  ifconfig eth0 192.168.1.100 netmask 255.255.255.0
  ```

- `ip addr`: Configure network interface (modern)
  ```
  ip addr add 192.168.1.100/24 dev eth0
  ```

- `netstat`: Display network connections
  ```
  netstat -tuln
  ```

- `nslookup`: Query DNS
  ```
  nslookup google.com
  ```

## Common Ports

- HTTP: 80
- HTTPS: 443
- FTP: 21
- SSH: 22
- SMTP: 25
- POP3: 110
- IMAP: 143
- DNS: 53
- DHCP: 67 (server), 68 (client)
- RDP: 3389
- MySQL: 3306
- PostgreSQL: 5432

## IP Addressing

- IPv4: 32-bit address (e.g., 192.168.1.1)
- IPv6: 128-bit address (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334)
- Subnet mask: Defines network and host portions (e.g., 255.255.255.0)
- CIDR notation: Combines IP and subnet mask (e.g., 192.168.1.0/24)

## Network Address Translation (NAT)

- Translates private IP addresses to public IP addresses
- Helps conserve IPv4 addresses
- Types: Static NAT, Dynamic NAT, PAT (Port Address Translation)

## DHCP (Dynamic Host Configuration Protocol)

- Automatically assigns IP addresses to devices on a network
- DHCP Discover -> DHCP Offer -> DHCP Request -> DHCP Acknowledge

## DNS (Domain Name System)

- Translates domain names to IP addresses
- Hierarchy: Root -> TLD -> Domain -> Subdomain
- Record types: A, AAAA, CNAME, MX, NS, PTR, SOA, TXT

## Firewall Basics

- Stateful: Tracks the state of network connections
- Stateless: Filters packets based on rules without tracking connections
- Application layer firewall: Operates at OSI layer 7, can inspect packet contents

## VLANs (Virtual Local Area Networks)

- Logically separate networks within a physical network
- Improve security and reduce broadcast domains
- Configured on switches and routers

## Troubleshooting Steps

1. Identify the problem
2. Gather information
3. Consider possible causes
4. Test potential solutions
5. Implement the solution
6. Verify system functionality
7. Document the solution

Remember: Always start troubleshooting from the Physical layer and work your way up the OSI model!