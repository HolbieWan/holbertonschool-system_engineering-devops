# holbertonschool-system_engineering-devops

# Web Development Basics - Essential Concepts

## Learning Objectives
By the end of this document, you should be able to:

+ Explain the core concepts of networking, servers, DNS, load balancers, monitoring, and databases.
+ Understand the difference between web servers and application servers.
+ Identify different DNS record types and their functions.
+ Explain what a single point of failure (SPOF) is and how to avoid it.
+ Describe strategies to prevent downtime during code deployment.
+ Understand high availability clusters (active-active and active-passive).
+ Explain what HTTPS and firewalls are, and their importance in web development.
+ Draw and explain a diagram of a web stack, describing the role of each component.
+ Know the following acronyms: LAMP, SPOF, QPS.

---

## Topics Overview

### 1. Network Basics Concept Page
A network is a group of interconnected devices that communicate with each other. Key elements include:

+ **IP Address**: A unique identifier for devices on a network.
+ **Subnet**: A segment of a network.
+ **Router**: Directs traffic between different networks.
+ **Switch**: Connects devices within the same network.

### 2. Server Concept Page
A **server** is a computer or software that provides services to other devices or applications, called clients. Types of servers:

+ **Web Server**: Serves web content.
+ **Database Server**: Stores and manages data.
+ **Application Server**: Runs specific applications.

### 3. Web Server Concept Page
A **web server** handles HTTP requests from clients (usually browsers) and serves HTML pages, CSS, JavaScript, and media files. Popular web servers:

+ Apache
+ Nginx

### 4. DNS Concept Page
**DNS (Domain Name System)** translates human-readable domain names (e.g., `example.com`) into IP addresses. Main DNS record types:

+ **A Record**: Maps a domain to an IPv4 address.
+ **AAAA Record**: Maps a domain to an IPv6 address.
+ **CNAME Record**: Alias of one domain to another.
+ **MX Record**: Specifies mail servers for a domain.
+ **TXT Record**: Provides text information to external sources.

### 5. Load Balancer Concept Page
A **load balancer** distributes incoming network traffic across multiple servers to ensure reliability and availability.

+ **Types**:
  - **Layer 4 Load Balancing**: Operates at the transport layer (TCP/UDP).
  - **Layer 7 Load Balancing**: Operates at the application layer (HTTP/HTTPS).
+ **Benefits**:
  - Improves fault tolerance.
  - Increases scalability.

### 6. Monitoring Concept Page
**Monitoring** involves tracking the performance and health of servers, applications, and networks.

+ **Tools**:
  - Prometheus
  - Nagios
  - Grafana
+ **Metrics to Monitor**:
  - CPU usage
  - Memory usage
  - Response time

### 7. What is a Database
A **database** is an organized collection of data that can be easily accessed, managed, and updated. Types of databases:

+ **Relational Databases** (SQL): Use structured tables (e.g., MySQL, PostgreSQL).
+ **NoSQL Databases**: Use non-tabular data models (e.g., MongoDB, Redis).

### 8. What’s the Difference Between a Web Server and an App Server?
+ **Web Server**: Handles HTTP requests and serves static content.
+ **Application Server**: Runs application logic and generates dynamic content.

### 9. DNS Record Types
+ **A Record**: IPv4 address mapping.
+ **AAAA Record**: IPv6 address mapping.
+ **CNAME Record**: Alias to another domain.
+ **MX Record**: Mail exchange server.
+ **TXT Record**: Miscellaneous text-based information.

### 10. Single Point of Failure (SPOF)
A **single point of failure** is a part of a system that, if it fails, will stop the entire system from working. Strategies to avoid SPOF:

+ Use redundancy (e.g., multiple servers).
+ Implement load balancing.
+ Use failover mechanisms.

### 11. How to Avoid Downtime When Deploying New Code
+ **Blue-Green Deployment**: Use two environments (one live, one idle).
+ **Rolling Deployment**: Gradually replace old versions with new ones.
+ **Canary Deployment**: Deploy new code to a small subset of users first.

### 12. High Availability Cluster (Active-Active/Active-Passive)
+ **Active-Active**: All nodes are active and share the load.
+ **Active-Passive**: One node is active, while the other remains on standby.

### 13. What is HTTPS
**HTTPS (Hypertext Transfer Protocol Secure)** is an extension of HTTP that uses encryption (SSL/TLS) to secure communication between a client and a server.

+ **Benefits**:
  - Data encryption
  - Data integrity
  - Authentication

### 14. What is a Firewall
A **firewall** is a network security device or software that monitors and controls incoming and outgoing traffic based on security rules.

+ **Types**:
  - Hardware firewalls
  - Software firewalls
+ **Benefits**:
  - Protects against unauthorized access.
  - Filters malicious traffic.

---

## Acronyms
+ **LAMP**: Linux, Apache, MySQL, PHP/Python/Perl
+ **SPOF**: Single Point of Failure
+ **QPS**: Queries Per Second

---

## Diagram of a Basic Web Stack
A typical web stack might include:

1. **Load Balancer**: Distributes traffic across multiple web servers.
2. **Web Servers**: Serve static and dynamic content.
3. **Application Servers**: Handle business logic.
4. **Database Servers**: Store and manage data.
5. **Monitoring Tools**: Track system performance.

Example:
```
        [ Load Balancer ]
             /    \
     [ Web Server ] [ Web Server ]
             |            |
     [ Application Server ]
             |
     [ Database Server ]
```

---

This document provides a foundational understanding of essential web development concepts. Mastery of these topics is crucial for any web developer working in modern web infrastructure.

