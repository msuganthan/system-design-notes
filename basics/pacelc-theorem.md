**PACELC Theorem**:

**Background:** We cannot avoid partition in a distributed system therefore, according to the CAP theorem, a distributed system should choose between consistency or availability. **ACID databases chose consistency** while **BASE(Basically available, Soft-state, Eventually consistent) databases such as MongoDB, Cassandra and Redis chose availability.**

One place where the CAP theoram is silient is what happens when there is no network partition? What choices does a distributed system have when there is not partition?

**Solution:**

**PACELC theorem states that in a system that replicates data**:

If there is a partition(P) a distributed system can trade off between availability and consistency(i.e. `A` and `C`)
    
Else when the system is running normally in the absence of partitions the system can tradeoff between Latency(`L`) and consistency(`C`).

The first part of the theorem(PAC) is the same as the CAP theorem, and the ELC is the extension. The whole thesis is **assuming we maintain high availability by replication.** So, **where there is a failure, CAP theorem prevails**. But if not, we still have to consider the tradeoff between consistency and latency of a replicated system.

**Examples:**

**Dynamo and Cassandra are PA/EL system**: They choose availability over consistency when partition occurs; otherwise they choose lower latency.

**BigTable and HBase are PC/EC system:** They will always choose consistency, giving up availability and lower latency.

**MongoDB can be considered PA/EC:** MongoDB works in a primary/secondaries configuration. In the default configuration, all writes and read are performed on the primary. As all replication is done asynchronously, when there is a network partition in which primary is lost or becomes isolated on the minority side, there is a chance of losing data that is unreplicated to secondaries, hence there is a loss of consistency during partitions. Therefore it can concluded that in the case of a network partition, MongoDB chooses availability, but otherwise guarantees consistency. Alternately, when MongoDB is configured to write on majority replicas and read from the primary, it could be categorized as PC/EC.


