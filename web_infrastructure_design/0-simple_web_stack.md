https://i.imgur.com/A9zg3WD.png

## Description
This simple web stack is designed to host a website accessible at `www.foobar.com`. It consists of the following components:

1. **1 Server**
   - A single server with IP `8.8.8.8` that hosts all the required components (web server, application server, and database).

2. **1 Web Server (Nginx)**
   - Handles HTTP/HTTPS requests and serves static files (e.g., HTML, CSS, JS).
   - Redirects dynamic requests to the application server.

3. **1 Application Server**
   - Processes the business logic of the website.
   - Executes the code base to generate dynamic content.

4. **1 Database (MySQL)**
   - Stores and manages the application data.
   - Used for querying and retrieving information.

5. **1 Domain Name (foobar.com)**
   - Linked to the server's IP address `8.8.8.8` using an `A` DNS record.
   - The `www` subdomain is configured as a `CNAME` record pointing to `foobar.com`.

## Infrastructure Workflow
1. A user opens a browser and enters `www.foobar.com`.
2. The browser sends a request to the DNS server to resolve `www.foobar.com` into an IP address (`8.8.8.8`).
3. The request is routed to the server.
4. The **web server (Nginx)** receives the request and:\n
   - Serves static files directly, or\n
   - Forwards the request to the **application server** if dynamic processing is needed.
5. The **application server** processes the request, interacts with the **database**, and generates a response.
6. The response is sent back to the user’s browser.

## Issues with the Infrastructure

1. **Single Point of Failure (SPOF):**
   - If the server fails, the entire website becomes unavailable.
2. **Downtime during Maintenance:**
   - Restarting the web server or deploying new code results in temporary unavailability.
3. **Scalability Issues:**
   - The single server cannot handle high traffic loads efficiently.
