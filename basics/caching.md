Caching will enable you to make vastly better use of the resources **you already have** as well as making otherwise unattainable product requirement feasible. Caches take advantage of the **locality of reference principle**: recently requested data is likely to be requested again. 

They are used in almost every computing layer: hardware, operating systems, web browsers, web applications, and more. A cache is like short-term memory: it has a limited amount of space, but is typically faster than the original data source and contains the most recently accessed items.

Caches can exist at all levels in architecture, but are often found at the level nearest to the front end, where they are implemented to return data quickly without taxing downstream levels.

**Application server cache**: Placing a cache directly on a request layer node enables the local storage of response data. Each time a request is made to the service, the node will quickly return locally cached data if it exists. If it is not in the cache, the requesting node will fetch the data from the disk. The cache on one request layer node could also be located both in memory(which is very fast) and on the node's local disk(faster than going to network storage).

**What happens when you expand this to many nodes? If the request layer is expanded to multiple nodes, it's still quite possible to have each node host its own cache. However, if you load balancer randomly distributes requests across the nodes, the same request will go to different nodes, thus increasing cache misses. Two choices for overcoming this hurdle are global caches and distributed caches.**

**Content Delivery Network**: CDNs are a kind of cache that comes into play for sites serving large amount of static media. In a typical CDN setup, a request will first ask the CDN for a piece of static media; the CDN will serve that content if it has it locally available. If it isn't available, the CDN will query the back-end servers for the file, cache it locally and serve it to the requesting user.

If the system we are building is not large enough to have its own CDN, we can ease a future transition by serving the static media off a separate subdomain(e.g., static.yourservice.com) using a lightweight HTTP server like Nginx, and cut-over the DNS from your servers to a CDN later.

**Cache Invalidation**: While caching is fantastic, it requires some maintenance to keep the cache coherent with the source of truth. If the data is modified in the database, it should be invalidated in the cache; if not, this can cause inconsistent application behavior.

    1. **Write-through cache**: Under this scheme, data is written into the cache and the corresponding database simultaneously. The cached data allows for fast retrieval and since the same data get written in the permanent storage, we will complete data consistency between the cache and the storage. Also, this schema ensures that nothing will get lost in case of a crash, power failure, or system distruptions.

    Although, write-throught minimizes the risk of data loss, since every write operation must be done twice before returning success to the client, this scheme has the disadvantage of higher latency for the write operations.

    2. **Write-around cache**: This technique is similar to write-through cache, but data is written directly to the permanent storage, bypassing the cache. This can reduce the cache beging flood with write operations that will not subsequencetly be re-read, but has that disadvantage that a read request for recently written data will create a "cache-miss" and must be read from slower back-end storage and experience higher latency.

    3. **Write-back cache**: Under this scheme, data is written to cache alone, and completion is immediately confirmed to the client. This write to the permanent storage is done after specified intervals or under certain conditions. This results in low-latency and high throughput for write-intensive application; however this speed comes with the risk of data loss in case of a crash or other adverse event because the only copy of the written data is in the cache.

**Cache eviction policies**:

    1. FIFO:  The cache evicts the first block accessed first without any regard to how often or how many times it was accessed before
    2. LIFO: The cache evicts the block accessed most recently first without any regard to how often or how many times it as accessed before
    3. LRU: Discards the least recently used items first.
    4. MRU: Discards, the most recently used items first.
    5. LFU: Counts how often an item is needed.
    6. RR(Random replacement) Randomly selects a candidate item and discards it to make space when necessary.