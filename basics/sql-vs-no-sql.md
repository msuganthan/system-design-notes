**SQL:** Relational databases stores data in rows and columns. Each row contains all the information about one entity and each column contains all the separate data points. Some of the most popular databases are **MySQL, Oracle, MS SQL server, SQLite, Postgres, and MariaDB**

**NoSQL:** Following are the most common types of NoSQL:

**Key-Value Stores:** Data is stored in an array of key-value pairs. The `key` is an attribute name which is linked to a `value`. Well known key-value stores include **Redis, Voldemort, and Dynamo.**

**Document Databases:** In these databases, data is stored in document and these document are grouped together in collections. Each document can have an entirely different structure. Document databases include the `CouchDB` and `MongoDB`.

**Wide-Column Databases:** Instread of tables, in columnar database we have column families, which are containers for rows. Unlike relation databases, we don't need to know all the columns up front and each row doesn't have to have the same number of columns. Columnar databases are best suited for analyzing large datasets-big name include Cassandra and HBase.

**Graph Databases:** These databases are used to store data which relations are best represented in a graph. Data is saved in graph structures with nodes, properties, and lines. Example of graph database include Neo4J and InfiniteGraph.

**High level difference between SQL and NoSQL:** 

**Storage:** SQL stores data in tables where each row represents and entity and each column represents a data point about that entity; for example, if we are storing a car entity in a tables, different columns could be `Color`, `Make`, `Model` and so on.

NoSQL databases have different data storage models. The main ones are key-value, document, graph and columnar. We will discuss differences between these databases below.

**Schema:** In SQL, each recode conforms to a fixed schema, meaning the columns must be decided and chosen before data entry and each row must have data for each column. The schema can be altered later, but it involved modifying the whole database and going offline.

In **NoSQL,** schemas are dynamic. Columns can be added on the fly and each `row` doesn't have to contain data for each `column.`

**Querying:** SQL database use SQL for defining and manipulating the data, which is very powerful. In a NoSQL database, queries are focused on a collection of documents. Sometimes it is also call Unstructured Query Languange. Different databases have different syntax for using UnQL.

**Scalability:** In most common situation, SQL databases are vertically scalable. It is possible to scale a relational database across multiple servers, but this is a challenging and time-consuming process.

On the other hand, NoSQL databases are horizontally scalable.

**Reliability or ACID compliancy:** The vast majority of relation databases are ACID compliant. So, when it comes to data reliability and safe quarantee of performing transaction, SQL databases are still the better bet.

Most of the **NoSQL** solution sacrifice ACID compliance for performance and scalability.

**Reasons for SQL database:** 

    1. We need to ensure ACID compliance.
    2. Your data is structured and unchanging.

**Reason for NoSQL database:** When all the other components of our applications are fast and seamless, NoSQL database prevent data from being bottleneck. Big data is contribution to a large success for NoSQL databases, mainly because it handles data differently than the traditional relation databases.

    1. Storing large volumes of data that often have little to no strucuture. A NoSQL database sets no limits on the types of data we can store together and allows us to add new types of data we can store together and allows us to add new types as the need changes. With document-bases databases you store data in one place without having to define what "types" of data those are in advance.
    2. Making the most of cloud computing and storage. Cloud based storage is an excellent cost-saving solution but requires data to be easily spread across multiple servers to scale up. Using commodity hardware on-site or in the cloud saves you the hassle of additional software and NoSQL database like **Cassandra are designed to be scaled across multiple data centers out of the box without a lot of headaches.**
    3. Rapid development.