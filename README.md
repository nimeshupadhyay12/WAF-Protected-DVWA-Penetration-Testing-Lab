# WAF-Protected-DVWA-Penetration-Testing-Lab
A hands-on enterprise-style web security lab built using Kali Linux and Ubuntu, where DVWA is protected using a Docker-based SafeLine Web Application Firewall configured in reverse proxy mode with HTTPS enforcement and real-world attack simulation.

## Enterprise Web Security Architecture using SafeLine WAF
This project demonstrates a complete enterprise-style web security lab built using VirtualBox with two virtual machines: Kali Linux (attacker) and Ubuntu (web server). Both systems were configured using a Bridged Network Adapter to simulate a real-world LAN environment within the same subnet (192.168.1.x).

On the Ubuntu server, a full LAMP stack was deployed, including Apache2, MySQL, and PHP. DVWA (Damn Vulnerable Web Application) was installed inside /var/www/html/DVWA, configured with proper database credentials, and successfully tested after resolving Apache VirtualHost and MySQL authentication issues.

To secure the vulnerable application, SafeLine Web Application Firewall (WAF) was deployed using Docker. SafeLine was configured in reverse proxy mode, listening on HTTPS (port 443) and forwarding legitimate traffic to the backend Apache server (port 80). A custom domain was mapped using /etc/hosts, and an SSL certificate was generated and integrated into the WAF interface.

The final architecture simulates an enterprise defensive security setup:

Kali → HTTPS (443) → SafeLine WAF → Apache → DVWA → MySQL

This lab demonstrates hands-on experience in web security, reverse proxy configuration, Docker-based deployments, SSL implementation, attack simulation, and real-world infrastructure troubleshooting.


## Project Walkthrough

This project demonstrates a Security Operations Center (SOC) style home lab built to simulate real-world web attacks and defensive security controls. The lab was created using VirtualBox, where two virtual machines were deployed: Kali Linux as the attacker machine and Ubuntu as the target web server. Both machines were configured using a bridged network adapter, allowing them to obtain IP addresses from the same network and communicate with each other as if they were part of a real organizational infrastructure.

On the Ubuntu machine, a complete web server stack was deployed using Apache, PHP, and MySQL to host a vulnerable application. The application used in this lab was DVWA (Damn Vulnerable Web Application), which is intentionally designed with security vulnerabilities such as SQL Injection, Cross-Site Scripting (XSS), and other web attacks for educational purposes. The DVWA application was configured to run on port 8080, allowing it to be accessed from the attacker machine through the browser. To simplify domain access, manual DNS resolution was configured by editing the /etc/hosts file and mapping the Ubuntu server IP to a custom domain name.

To simulate a defensive security layer similar to a production environment, SafeLine Web Application Firewall (WAF) was installed on the Ubuntu server. The WAF was configured in reverse proxy mode, where all incoming traffic first passes through the firewall before reaching the web application. An SSL/TLS certificate was generated using OpenSSL and configured in the WAF to enforce secure HTTPS communication on port 443, replacing insecure HTTP traffic. This setup allowed the firewall to inspect incoming requests and block malicious activities before they reached the web server.

Once the environment was configured, various attack simulations were performed from the Kali Linux machine to test the effectiveness of the WAF. These included SQL Injection attempts, HTTP flood (DoS) simulations, and rapid access requests to trigger rate-limiting protections. The WAF was configured with multiple security controls such as HTTP flood protection, authentication enforcement, and custom firewall rules to block specific IP addresses. The SafeLine dashboard was used to monitor traffic statistics, blocked attacks, and request logs, providing insights into how the firewall detects and mitigates malicious traffic.

Through this lab, the project demonstrates how offensive security testing and defensive monitoring can be combined in a controlled environment to better understand web application security. It highlights practical skills such as WAF deployment, reverse proxy configuration, attack simulation, traffic monitoring, and security rule implementation, which are essential for roles in SOC analysis, web security, and cybersecurity engineering.
