# Hands-On Tasks Documentation

## 1. Calculate subnet masks and IP ranges

### Using an Online Subnet Calculator

1. Visit a subnet calculator website (e.g., https://www.subnet-calculator.com/)
2. Enter the network address and CIDR notation (e.g., 192.168.1.0/24)
3. Click "Calculate" or "Submit"
4. Analyze the results, including:
   - Subnet mask
   - Network address
   - Broadcast address
   - First and last usable IP addresses
   - Total number of usable hosts

### Example Calculation

Network: 192.168.1.0/24
Subnets required: 4

1. Determine bits needed for subnets: 2 bits (2^2 = 4 subnets)
2. New subnet mask: 255.255.255.192 (/26)
3. Subnets:
   - 192.168.1.0/26 (Network: 192.168.1.0, Broadcast: 192.168.1.63)
   - 192.168.1.64/26 (Network: 192.168.1.64, Broadcast: 192.168.1.127)
   - 192.168.1.128/26 (Network: 192.168.1.128, Broadcast: 192.168.1.191)
   - 192.168.1.192/26 (Network: 192.168.1.192, Broadcast: 192.168.1.255)

## 2. Configure static IP addresses and subnet masks

### On Linux

1. Open a terminal
2. Use the `ip` command to view current network configuration:
   ```
   ip addr show
   ```
3. Identify the network interface (e.g., eth0, ens33)
4. Edit the network configuration file:
   ```
   sudo nano /etc/netplan/01-netcfg.yaml
   ```
5. Add or modify the configuration:
   ```yaml
   network:
     version: 2
     renderer: networkd
     ethernets:
       eth0:
         addresses:
           - 192.168.1.100/24
         gateway4: 192.168.1.1
         nameservers:
           addresses: [8.8.8.8, 8.8.4.4]
   ```
6. Save the file and exit the editor
7. Apply the changes:
   ```
   sudo netplan apply
   ```

### On Windows

1. Open Network and Sharing Center
2. Click on "Change adapter settings"
3. Right-click on the network interface and select "Properties"
4. Select "Internet Protocol Version 4 (TCP/IPv4)" and click "Properties"
5. Choose "Use the following IP address" and enter:
   - IP address: 192.168.1.100
   - Subnet mask: 255.255.255.0
   - Default gateway: 192.168.1.1
6. Click "OK" to save changes

## 3. Test network connectivity

### Using ping

1. Open a terminal or command prompt
2. Ping the default gateway:
   ```
   ping 192.168.1.1
   ```
3. Ping an external IP address:
   ```
   ping 8.8.8.8
   ```
4. Ping a domain name:
   ```
   ping google.com
   ```

### Using ifconfig (Linux) or ipconfig (Windows)

On Linux:
```
ifconfig
```

On Windows:
```
ipconfig /all
```

Analyze the output to verify IP address, subnet mask, and default gateway settings.

These hands-on tasks will help reinforce your understanding of subnetting, IP addressing, and basic network configuration. Remember to document your results and any challenges encountered during the process.
