**Scalability**: **Scalability is the capability of a system, process, or a network to grow and manage increased demand. Any distributed system that can continuously evolve in order to support the growing amount of work is considered to be scalable**

A system may have to scale because of many reasons like increased data volume or increased amount of work. e.g., number of transactions. A scalable system would like to achieve this scaling without performance loss.

**Horizontal vs Vertical Scaling**: 
1. Horizontal scaling means that you scale by adding **more servers into your pool of resources** whereas **Vertical scaling means that you scale by adding more power**.
2. Horizontal scaling it is often easier to scale dynamically by **adding more machines into the existing pool** e.g.; cassandra and mongodb; Vertical-scaling is usually limited to the capacity of a single server and scaling beyond the **capacity often involves downtime and comes with an upper limit.** e.g; MySQL.

**Reliability**: Reliability is the probability a system will fail in a given period. In simple terms, **a distributed system is considered reliable if it keeps delivering its service even when one or several of its software or hardware components fail**. Reliability represents one of the main characteristics of any distributed system, since in such systems any **failing machine can always be replaced by another healthy one**, ensuring the completion of the requested task. 
    
**Example**: In **Amazon**, where one of the primary requirement is that any user transaction should never be canceled due to a failure of the machine that is running that transaction. For instance, if a user has added an item to their shopping cart, the system is expected not to lose it. A reliable distributed system achieves this through redundancy of both the software components and data. If the server carrying the user's shopping cart fails, another server that has the exact replica of the shopping cart should replace it.

Obviously, redundancy has a cost and reliable system has to pay that to achieve such resilience for services by eliminating every single point of failure.

**Availability**: Availability is the time a system remains operational to perform its required function in a specific period. It is a simple measure of the percentage of time that a system, service or a machine remains operational under normal conditions.

**Reliability vs Availability**: If a system is reliable, it is available. However, if it available it is not necessarily reliable. In other words, **high reliability contributes to high availability, but is possible to achieve a high availability even with an unreliable product by minimizing repair time and ensuring that spares are always available when they are needed**

**Efficiency**: To measure the efficiency of a distributed system, let's assume we have an operation that runs in a distributed manner and delivers a set of items as result. **Two standard measures of its efficiency are the response time and the throughput which denotes the number of items delivered in a given time unit.** The two measures correspond to the following unit costs:

    1. Number of messages globally sent by the nodes of the system regardless of the message size.
    2. Size of messages representing the volume of data exchanges.

**Serviceability or Manageability**: Serviceability or manageability is the simplicity and speed with which a system can be repaired or maintained; if the time to fix a failed system increases, then availability will decrease. 