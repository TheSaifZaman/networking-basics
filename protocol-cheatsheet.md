## HTTPS (HTTP Secure)

### Key Concepts
- HTTP over TLS/SSL
- Encrypts all communication
- Uses TCP port 443

### SSL/TLS Handshake Process
1. Client Hello
2. Server Hello
3. Certificate Exchange
4. Key Exchange
5. Secure Communication

### Benefits
- Data Encryption
- Data Integrity
- Authentication

### HTTP vs HTTPS Comparison
| Feature | HTTP | HTTPS |
|---------|------|-------|
| Encryption | No | Yes |
| Port | 80 | 443 |
| URL Prefix | http:// | https:// |
| Certificate | Not required | Required |
| SEO Impact | Lower | Higher |

## Useful Commands and Tools

### curl
- Basic GET: `curl http://example.com`
- View headers: `curl -I http://example.com`
- Verbose output: `curl -v https://example.com`
- POST request: `curl -X POST -d "data" http://example.com`

### Wireshark Filters
- DNS: `dns`
- DHCP: `dhcp`
- HTTP: `http`
- HTTPS: `ssl` or `tls`

### OpenSSL
- Test HTTPS connection: `openssl s_client -connect example.com:443`
- View certificate: `openssl x509 -in certificate.crt -text -noout`

### Networking
- Check IP configuration: `ipconfig` (Windows) or `ifconfig` (Linux/Mac)
- Trace route: `tracert` (Windows) or `traceroute` (Linux/Mac)
- Check open ports: `netstat -an`

Remember: Always use these tools responsibly and with permission on networks and systems you own or are authorized to test.
