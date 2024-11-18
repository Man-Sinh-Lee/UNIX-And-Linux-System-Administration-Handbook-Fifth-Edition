### Chapter 19: Web Hosting - Summary with Example Commands

#### **19.1 HTTP: The Hypertext Transfer Protocol**
- **Overview**:
  - HTTP is the protocol that powers the web, involving stateless client-server communications.
  - Common features include requests for resources, responses, and optional encryption with HTTPS.
- **Tools**:
  - Use `curl` or `telnet` for debugging:
    ```bash
    curl -I https://example.com
    ```

---

#### **19.2 Web Software Basics**
- **Web Servers**:
  - Examples: Apache HTTPD and NGINX.
  - Functions include virtual hosting, TLS handling, logging, and dynamic content routing.
- **Proxies and Load Balancers**:
  - Enhance web application scalability and availability.
  - Cache servers can accelerate content delivery.

---

#### **19.3 Web Hosting in the Cloud**
- **Static Hosting**:
  - Example with AWS S3:
    ```bash
    aws s3 sync ./website s3://my-bucket --acl public-read
    ```
- **Serverless Applications**:
  - Combine AWS Lambda, API Gateway, and S3 for cost-efficient hosting.

---

#### **19.4 Apache HTTPD**
- **Configuration**:
  - Central file: `httpd.conf`.
  - Configure virtual hosts:
    ```apache
    <VirtualHost *:80>
        ServerName www.example.com
        DocumentRoot "/var/www/example"
    </VirtualHost>
    ```
- **TLS Setup**:
  ```apache
  SSLEngine on
  SSLCertificateFile "/etc/ssl/certs/example.crt"
  SSLCertificateKeyFile "/etc/ssl/private/example.key"
  ```

---

#### **19.5 NGINX**
- **Event-Driven Architecture**:
  - Optimized for high-concurrency environments.
- **Configuration**:
  ```nginx
  server {
      listen 80;
      server_name example.com;
      location / {
          root /var/www/example;
      }
  }
  ```
- **Load Balancing**:
  ```nginx
  upstream backend {
      server web1;
      server web2;
  }

  server {
      listen 80;
      location / {
          proxy_pass http://backend;
      }
  }
  ```

---

#### **19.6 HAProxy**
- **Load Balancing**:
  - Proxies HTTP/TCP with health checks and sticky sessions.
  ```haproxy
  frontend http-in
      bind *:80
      default_backend servers

  backend servers
      server web1 192.168.1.2:80 check
      server web2 192.168.1.3:80 check
  ```

---

#### **19.7 Recommended Reading**
- Suggested resources include configuration documentation for Apache HTTPD, NGINX, and HAProxy, alongside RFCs for HTTP standards.

This summary offers practical insights into web hosting and setup. Let me know if you need more details!