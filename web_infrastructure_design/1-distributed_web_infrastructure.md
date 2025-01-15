https://i.imgur.com/WR1v22o.png

## Description of the Infrastructure
This distributed web infrastructure is designed to host the website www.foobar.com. 
It improves availability and scalability compared to a single-server setup.

## Components Added

1. Load Balancer (HAProxy):

    - Why added:

          - Distributes traffic across multiple servers to prevent overloading a single server.
          - Improves system availability by ensuring traffic is handled even if one server fails.
    
    - Distribution Algorithm:

          - Round-robin: Each incoming request is distributed 
          sequentially across all available servers.

    - Active-Active Setup:

            - Both servers are actively handling traffic simultaneously, maximizing resource usage and minimizing downtime.
            - Difference with Active-Passive: In an Active-Passive setup, one server is on standby and only takes over if the active server fails.

2. Web Server (Nginx):

    - Why added:

          - Handles HTTP/HTTPS requests and serves static content (HTML, CSS, JS).
          - Forwards dynamic requests to the application server.

    - Improves modularity by separating static content serving from business logic.
  

3. Application Server:

     - Why added:

          - Processes business logic and dynamic requests.
          - Executes the code base to generate dynamic content.

4. Database Cluster (Primary-Replica):

    -Why added:

          - Improves scalability by separating read and write operations.
          - Increases data availability with redundancy.

    - How it works:

          - Primary Node: Handles all write operations and serves as the source of truth for data.
          - Replica Node: Synchronizes with the primary node and handles read operations, reducing the load on the primary.

    - Difference:
          
          - Primary Node: Responsible for ensuring data consistency and handling all changes to the database.
          - Replica Node: Optimized for performance by responding only to read queries.


Issues with the Infrastructure

1. Single Point of Failure (SPOF):

    - The load balancer is a SPOF. If it fails, the entire infrastructure becomes inaccessible.
    - The primary database is critical for all write operations. Its failure impacts data integrity.

2. Security Issues:

    - No firewalls are configured to block unauthorized access.
    - Lack of HTTPS means data is transmitted in plain text, which is vulnerable to interception.

3.No Monitoring:

    The infrastructure lacks tools to detect server failures, traffic spikes, or performance bottlenecks.


How the Infrastructure Works

1. User Access:

    - A user accesses the website by typing www.foobar.com.
    - The DNS resolves the domain to the IP address of the load balancer.

2. Load Balancer:

    - The load balancer (HAProxy) distributes the incoming traffic to the available servers (Web Server or Application Server) using the round-robin algorithm.

3. Web and Application Servers:

    - The web server handles static files or forwards requests to the application server.
    - The application server processes dynamic requests, interacts with the database cluster, and returns the response to the user.

4. Database Cluster:

    - The application server interacts with the Primary Database for write operations and the Replica Database for read operations.
    - The replica database ensures scalability and redundancy by replicating data from the primary node.