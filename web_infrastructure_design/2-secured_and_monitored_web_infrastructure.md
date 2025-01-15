https://i.imgur.com/O5VDKXg.png

Secured and Monitored Web Infrastructure Design

Description of the Infrastructure

This infrastructure builds upon the previous distributed design and includes security and monitoring 
enhancements to ensure secure and reliable operations of the website www.foobar.com.

Components Added
1. Firewalls (3):

    - Why added:

          - Protects each server (load balancer, web server, and database server) by filtering traffic.
          - Prevents unauthorized access and ensures only legitimate requests reach the servers.

    - What firewalls do:

          - Define rules to allow or deny traffic based on IP addresses, ports, and protocols.
          - Block malicious activities like Distributed Denial-of-Service (DDoS) attacks.

2. SSL Certificate:

    - Why added:

          - Encrypts all traffic between the user and the server, ensuring secure data transfer.
          - Protects sensitive user information (e.g., login credentials, payment data).

    - Why traffic is served over HTTPS:

          - Ensures data integrity and confidentiality.
          - Builds trust with users by displaying a secure padlock in the browser.

3.Monitoring Clients (3):

    - Why added:

          - Monitor system performance, detect failures, and collect metrics like CPU usage, memory, and traffic.
          - Helps identify and resolve issues before they impact users.

    - What monitoring does:

          - Collects data in real-time and sends it to a central monitoring tool (e.g., Sumologic).
          - Alerts administrators when thresholds are exceeded (e.g., high server load).

    - How monitoring tools collect data:

        - Agents installed on each server collect logs and performance metrics.
        - Metrics are sent to a centralized dashboard for analysis and visualization.

4. Additional Enhancements:

    - SSL Termination:

        - SSL traffic is terminated at the load balancer for performance optimization.

    - Monitoring Web Server QPS (Queries Per Second):

        - Logs and metrics from the web server are analyzed to monitor the number of requests per second.
        - Helps detect traffic surges and plan for scalability.


How the Infrastructure Works

1. User Access:

    - The user accesses the website via https://www.foobar.com.
    - The DNS resolves the domain to the load balancer’s IP address.

2. Traffic Handling:

    - The load balancer terminates SSL and forwards traffic to the appropriate web server or application server.
    - Each server is protected by a firewall to filter traffic.

3. Data Processing:

    - The web server serves static content or forwards dynamic requests to the application server.
    - The application server interacts with the Primary Database for write operations and the Replica Database for read operations.

4. Monitoring:

    - Monitoring clients on each server collect data (logs, CPU, memory, etc.) and send it to a monitoring tool like Sumologic for real-time analysis.


Issues with This Infrastructure

1.SSL Termination at the Load Balancer:

    - Issue: Data between the load balancer and the backend servers is not encrypted, which can be a vulnerability.
    - Mitigation: Enable end-to-end encryption by encrypting traffic between the load balancer and backend servers.

2. Single Write Node in MySQL:

    - Issue: The primary database is a bottleneck for write operations. If it fails, write operations are not possible.
    - Mitigation: Implement a failover mechanism with a standby replica to take over as primary in case of failure.

3. Homogeneous Server Components:

    - Issue: Servers hosting multiple components (e.g., database, web server, application server) can lead to resource contention.
    - Mitigation: Use dedicated servers for specific roles to improve performance and scalability.