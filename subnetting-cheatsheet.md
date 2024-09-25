# Subnetting and IP Addressing Cheatsheet

## IP Address Basics

- IPv4: 32-bit address (e.g., 192.168.1.1)
- IPv6: 128-bit address (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334)

## IP Address Classes

- Class A: 1.0.0.0 to 126.255.255.255
- Class B: 128.0.0.0 to 191.255.255.255
- Class C: 192.0.0.0 to 223.255.255.255
- Class D (Multicast): 224.0.0.0 to 239.255.255.255
- Class E (Reserved): 240.0.0.0 to 255.255.255.255

## Special IP Addresses

- Loopback: 127.0.0.1
- Private IP Ranges:
  - 10.0.0.0 to 10.255.255.255 (Class A)
  - 172.16.0.0 to 172.31.255.255 (Class B)
  - 192.168.0.0 to 192.168.255.255 (Class C)

## Subnet Mask Quick Reference

| CIDR | Subnet Mask     | Usable Hosts |
|------|-----------------|--------------|
| /24  | 255.255.255.0   | 254          |
| /25  | 255.255.255.128 | 126          |
| /26  | 255.255.255.192 | 62           |
| /27  | 255.255.255.224 | 30           |
| /28  | 255.255.255.240 | 14           |
| /29  | 255.255.255.248 | 6            |
| /30  | 255.255.255.252 | 2            |

## Subnetting Steps

1. Determine required subnets and hosts
2. Choose appropriate subnet mask
3. Calculate network, broadcast, and host range for each subnet

## Subnet Calculation Formulas

- Number of subnets = 2^n (n = borrowed bits)
- Number of hosts per subnet = 2^m - 2 (m = remaining host bits)
- Network address = First address in subnet range
- Broadcast address = Last address in subnet range

## Common Networking Commands

- Linux:
  - `ifconfig` or `ip addr show`: Display network configuration
  - `route -n` or `ip route show`: Display routing table
- Windows:
  - `ipconfig /all`: Display network configuration
  - `route print`: Display routing table
- Both:
  - `ping [IP or hostname]`: Test network connectivity
  - `traceroute` (Linux) or `tracert` (Windows): Trace route to destination

## Quick Subnet Math

- To find subnet size: 256 - last octet of subnet mask
- To find next subnet: Add subnet size to current