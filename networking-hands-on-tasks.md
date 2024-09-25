# Hands-on Tasks Documentation

## 1. Using `ping` and `traceroute` Commands

### `ping` Command

The `ping` command is used to test the reachability of a host on an IP network and measure the round-trip time for messages sent from the originating host to a destination computer.

Syntax:
```
ping [options] <destination>
```

Example:
```bash
$ ping google.com
PING google.com (172.217.16.142) 56(84) bytes of data.
64 bytes from ham02s14-in-f142.1e100.net (172.217.16.142): icmp_seq=1 ttl=115 time=15.2 ms
64 bytes from ham02s14-in-f142.1e100.net (172.217.16.142): icmp_seq=2 ttl=115 time=14.8 ms
64 bytes from ham02s14-in-f142.1e100.net (172.217.16.142): icmp_seq=3 ttl=115 time=15.0 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 14.805/15.021/15.245/0.180 ms
```

This output shows:
- The IP address of the destination (172.217.16.142)
- The size of the packets being sent (56 bytes of data + 28 bytes of header = 84 bytes)
- The round-trip time (RTT) for each packet
- A summary of the ping statistics

### `traceroute` Command

The `traceroute` command is used to display the route and measure transit delays of packets across an IP network.

Syntax:
```
traceroute [options] <destination>
```

Example:
```bash
$ traceroute google.com
traceroute to google.com (172.217.16.142), 30 hops max, 60 byte packets
 1  _gateway (192.168.1.1)  3.043 ms  2.915 ms  2.868 ms
 2  10.0.0.1 (10.0.0.1)  5.114 ms  5.095 ms  5.077 ms
 3  72.14.215.85 (72.14.215.85)  15.032 ms  15.007 ms  14.980 ms
 4  108.170.252.193 (108.170.252.193)  14.954 ms  14.930 ms  14.906 ms
 5  172.217.16.142 (172.217.16.142)  14.882 ms  14.858 ms  14.834 ms
```

This output shows:
- Each line represents a router or "hop" in the path to the destination
- The IP address and hostname (if available) of each hop
- The time it took for each of the three probes to reach that hop

## 2. Setting up Basic IP Configuration on Linux

### Using `ifconfig` (older systems)

The `ifconfig` command is used to configure network interfaces.

Viewing network interfaces:
```bash
$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::215:5dff:fe00:1234  prefixlen 64  scopeid 0x20<link>
        ether 00:15:5d:00:12:34  txqueuelen 1000  (Ethernet)
        RX packets 1234  bytes 1234567 (1.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5678  bytes 5678901 (5.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

Setting IP address:
```bash
$ sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0
```

### Using `ip addr` (modern systems)

The `ip addr` command is part of the `iproute2` suite and is the modern replacement for `ifconfig`.

Viewing network interfaces:
```bash
$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:15:5d:00:12:34 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.100/24 brd 192.168.1.255 scope global dynamic eth0
       valid_lft 86386sec preferred_lft 86386sec
```

Setting IP address:
```bash
$ sudo ip addr add 192.168.1.100/24 dev eth0
```

These commands allow you to view and configure network interfaces on a Linux system, which is essential for network troubleshooting and setup.
