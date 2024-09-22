# Hands-On Tasks Documentation

## 1. Using `dig` for DNS Queries

The `dig` (Domain Information Groper) command is a powerful tool for performing DNS lookups and troubleshooting DNS issues.

### Basic Usage
To perform a simple DNS lookup:

```bash
dig example.com
```

This will return the A record (IPv4 address) for example.com.

### Querying Specific Record Types
To query for a specific DNS record type:

```bash
dig example.com MX  # Query for MX records
dig example.com NS  # Query for NS records
dig example.com AAAA  # Query for IPv6 address
```

### Tracing DNS Resolution
To see the full DNS resolution process:

```bash
dig +trace example.com
```

This shows the queries to root servers, TLD servers, and authoritative servers.

### Querying a Specific DNS Server
To query a specific DNS server:

```bash
dig @8.8.8.8 example.com
```

This queries Google's public DNS server (8.8.8.8) for the A record of example.com.

### Analyzing DNS Response
Key parts of a `dig` response:

1. **QUESTION SECTION**: Shows the query that was sent.
2. **ANSWER SECTION**: Contains the answer to the query.
3. **AUTHORITY SECTION**: Lists the authoritative nameservers.
4. **ADDITIONAL SECTION**: Provides additional helpful information.

## 2. Setting Up a Basic Web Server

We'll set up a basic Nginx server to observe HTTP/HTTPS handling.

### Installing Nginx
On Ubuntu or Debian:

```bash
sudo apt update
sudo apt install nginx
```

### Basic Nginx Configuration
Edit the default configuration file:

```bash
sudo nano /etc/nginx/sites-available/default
```

A basic configuration:

```nginx
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/html;
    index index.html index.htm;

    server_name _;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

### Creating a Sample HTML Page
Create a simple HTML file:

```bash
echo "<html><body><h1>Hello, World!</h1></body></html>" | sudo tee /var/www/html/index.html
```

### Restarting Nginx
After making changes:

```bash
sudo systemctl restart nginx
```

### Setting Up HTTPS
1. Install Certbot:
   ```bash
   sudo apt install certbot python3-certbot-nginx
   ```

2. Obtain and install a certificate:
   ```bash
   sudo certbot --nginx -d yourdomain.com
   ```

3. Certbot will modify your Nginx configuration to enable HTTPS.

## 3. Using `curl` for HTTP/HTTPS Requests

`curl` is a command-line tool for transferring data using various protocols, including HTTP and HTTPS.

### Basic GET Request
```bash
curl http://localhost
```

This will display the HTML content of your Nginx server's default page.

### Viewing Headers
To see the response headers:

```bash
curl -I http://localhost
```

### Making a POST Request
```bash
curl -X POST -d "param1=value1&param2=value2" http://localhost
```

### Using HTTPS
```bash
curl https://localhost
```

### Verbose Output
For detailed information about the request and response:

```bash
curl -v https://localhost
```

This will show the entire HTTPS handshake process, headers, and response body.

### Comparing HTTP and HTTPS
You can observe the differences in headers and connection establishment between HTTP and HTTPS by using the `-v` flag with both protocols:

```bash
curl -v http://localhost
curl -v https://localhost
```

Key differences you'll notice:
- HTTPS establishes a TLS connection before sending the HTTP request
- HTTPS response includes security-related headers like `Strict-Transport-Security`

These hands-on tasks provide practical experience with DNS resolution, web server setup, and HTTP/HTTPS communication, reinforcing the theoretical concepts covered in the learning materials.
