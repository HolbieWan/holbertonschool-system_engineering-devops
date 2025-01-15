https://i.imgur.com/RgRxcrU.png

Scale Up Web Infrastructure Design

Components Added

1 Additional Load Balancer (HAProxy):

    - Why added:
          - Creates a clustered load balancer setup, improving fault tolerance.

          - Ensures high availability: if one load balancer fails, the other takes over.

Cluster Configuration:

      - Uses an Active-Passive setup: one load balancer actively handles traffic while the other remains in standby mode.

Benefit:

      - Eliminates the load balancer as a Single Point of Failure (SPOF).

2. Dedicated Servers for Components:

     - Web Server (Nginx):
         - Why split: Isolating the web server ensures it focuses solely on serving static content and routing dynamic requests, improving performance.

     - Application Server:
          - Why split: Separating the application server reduces resource contention and improves the scalability of the logic processing layer.

     - Database (MySQL):
          - Why split: Isolating the database ensures optimal performance for data storage and retrieval operations.


How the Infrastructure Works:

1. User Access:

    - The user accesses the website via www.foobar.com.
    - The DNS resolves the domain to the clustered load balancers' IP addresses.

2. Load Balancer Cluster:

    - The active load balancer distributes incoming traffic across the web servers.
    - If the active load balancer fails, the standby load balancer takes over automatically.

3.Web Servers:

    - Handle HTTP/HTTPS requests and serve static files.
    - Forward dynamic requests to the application servers.

4.Application Servers:

    - Process dynamic requests and execute the business logic.
    - Communicate with the database for data storage and retrieval.

5.Database Cluster:

    - The primary database handles write operations.
    - The replica database handles read operations, reducing the load on the primary node.


Advantages of Scaling Up:

1.Improved Fault Tolerance:

    - The clustered load balancers eliminate the load balancer SPOF.
    - Dedicated servers ensure that failures in one component do not affect others.

2.Enhanced Scalability:

    - Isolating components allows each server to scale independently based on demand.
    - Traffic spikes can be handled more efficiently by adding more web or application servers.

3.Resource Optimization:

    - Dedicated servers prevent resource contention, ensuring optimal performance for each component.