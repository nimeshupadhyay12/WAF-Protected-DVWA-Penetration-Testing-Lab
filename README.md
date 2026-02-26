# WAF-Protected-DVWA-Penetration-Testing-Lab
A hands-on enterprise-style web security lab built using Kali Linux and Ubuntu, where DVWA is protected using a Docker-based SafeLine Web Application Firewall configured in reverse proxy mode with HTTPS enforcement and real-world attack simulation.

## Enterprise Web Security Architecture using SafeLine WAF
This project demonstrates a complete enterprise-style web security lab built using VirtualBox with two virtual machines: Kali Linux (attacker) and Ubuntu (web server). Both systems were configured using a Bridged Network Adapter to simulate a real-world LAN environment within the same subnet (192.168.1.x).

On the Ubuntu server, a full LAMP stack was deployed, including Apache2, MySQL, and PHP. DVWA (Damn Vulnerable Web Application) was installed inside /var/www/html/DVWA, configured with proper database credentials, and successfully tested after resolving Apache VirtualHost and MySQL authentication issues.

To secure the vulnerable application, SafeLine Web Application Firewall (WAF) was deployed using Docker. SafeLine was configured in reverse proxy mode, listening on HTTPS (port 443) and forwarding legitimate traffic to the backend Apache server (port 80). A custom domain was mapped using /etc/hosts, and an SSL certificate was generated and integrated into the WAF interface.

The final architecture simulates an enterprise defensive security setup:

Kali → HTTPS (443) → SafeLine WAF → Apache → DVWA → MySQL

This lab demonstrates hands-on experience in web security, reverse proxy configuration, Docker-based deployments, SSL implementation, attack simulation, and real-world infrastructure troubleshooting.
