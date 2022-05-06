**Load Balancing**: Helps to spread the traffic across a cluster of servers to improve responsiveness and availability of applications, websites or databases. **LB also keeps track of the status of all the resources while distributing requests**. If a server is not available to take a new requests or is not responding or has elevated error rate, LB will stop sending traffic to such a server.

* LB sits between **the client and the server accepting incoming network** and application traffic and distributing the traffic across multiple backend servers using various algorithms. By balancing application requests across multiple servers, a load balancer reduces individual server load and prevents anyone application server from becoming a single point of failure thus improving overall application availability and responsiveness.

**We can add LBs at three places**:

    1. Between the user and the web server
    2. Between web servers and an internal platform layer, like application servers or cache servers.
    3. Between internal platform layer and datbase.

**Benefits of Load balancing**:

    1. User experience faster, uninterrupted service. Users won't have to wait for a single struggling server to finish its previous tasks. Instead, their requests are immediately passed on to a more readily available resource.
    2. Service providers experience less downtime and higher throughput. Even a full server failure won't affect the end user experience as the load balance will simply route around it to a health server.
    3. Load balancing makes it easier for system administrator to handle incoming requests while decreasing wait time for users.
    4. Smart load balancers provide benefits like preditive analytics that determine traffic bottlenecks before they happen. As a result, the smart load balancer gives an organization actionable insights. These are key to automation and can help drive business decisions.
    5. System adminitrators experience fewer failed or stressed components. Instead of a single device performing a lot of work, load balancing have several devices perform a little bit of work.

**Load balancing algorithms**:

**Health Checks**: Load balancers should only forward traffic to "healthy" backend servers. To monitor the health of a backedn server, "health checks" regularly attempt to connect to backend servers to ensure that servers are listening. If a server fails a health check, it is automatically removed from the pool, and traffic will not be forwarded to it until it respond to the health checks again.

    1. Least connection Method: **This method directs traffic to the server with the fewest active connections.** This approach is quite useful when there are a large number of persistent client connections which are unevenly ditributed between the servers.

    2. Least Response Time Method: This algorithm directs traffic to the server with fewest active connections and lowest average response time.
    3. Least Bandwidth Method: This method selects the server that is currently serving the least amount of traffic measured in megabits per second(Mbps)
    4. Round Robin Method: This method cycles through a list of server and send each new request to the next server. When it reaches the end of the list, it starts over at the beginning. It is most useful when the servers are of equal specification and there are not many **persistent connections.**
    5. Weighted Round Robin Method: The weighted round-robin scheduling is designed to better handle servers with different processing capacities. Each server is assigned a weight(an integer value that indicates the processing capacity). Server with higher weights receive new connections before those with less weights and servers with higher weights get more connections than those with less weights.
    6. IP Hash: Under this method, a hash of the IP address of the client is calculated to redirect the request to the server.

**Redundant Load Balancer**: The load balancer can be a single point of failure; to overcome this, a second load balancer can be connection to the first to form cluster. Each LB monitors the health of the other and, since both of them are equally capable of serving traffic and failure detection, in the event of main load balancer fails, the second load balancer takes over.