
In Amazon Web Services (AWS), databases play a critical role in supporting various applications and services by storing, organizing, and managing data. AWS provides a range of database services catering to different types of data, workloads, and performance requirements. Here are some key database services in AWS:

## Amazon RDS: Relational Database Service 🗃️

Amazon RDS is a managed relational database service that supports several popular database engines, including MySQL, PostgreSQL, MariaDB, Oracle, and Microsoft SQL Server. It simplifies database administration tasks such as hardware provisioning, patching, and backups, allowing you to focus on your application.

**Use Cases:** Suitable for applications requiring a traditional relational database structure.

## Amazon DynamoDB: NoSQL Database 📊

DynamoDB is a fully managed NoSQL database service designed for high-performance, low-latency applications. It provides seamless scalability, automatic partitioning, and supports both document and key-value data models.

**Use Cases:** Ideal for applications with unpredictable workloads, where fast and scalable access to data is crucial.

## Amazon Aurora: MySQL and PostgreSQL-Compatible Relational Database 🌌

Amazon Aurora is a high-performance, fully managed relational database engine compatible with MySQL and PostgreSQL. It provides the performance and availability of commercial databases with the simplicity and cost-effectiveness of open-source databases.

**Use Cases:** Well-suited for applications that require the performance of commercial-grade databases but with the cost-effectiveness of open-source databases.

## Amazon Redshift: Data Warehouse 📊

Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud. It is designed for high-performance analysis using standard SQL queries. Redshift can handle large datasets and is optimized for analytics and business intelligence workloads.

**Use Cases:** Ideal for data warehousing and business intelligence applications with large datasets.

## Amazon ElastiCache: In-Memory Caching 🚀

ElastiCache is a fully managed in-memory caching service. It supports popular in-memory data stores like Redis and Memcached, helping to improve the performance of applications by caching frequently accessed data.

**Use Cases:** Useful for applications that require low-latency access to frequently accessed data.

## Amazon Neptune: Graph Database 🌐

Amazon Neptune is a fully managed graph database service that supports two popular graph models: Property Graph and RDF (Resource Description Framework). It is designed to efficiently navigate and query highly connected datasets.

**Use Cases:** Suitable for applications that require querying and analyzing highly connected data, such as social networks and fraud detection.

These are just a few examples of the many database services available in AWS. The choice of a database service depends on factors such as the nature of the data, scalability requirements, and the specific needs of your application. AWS provides a comprehensive set of tools to help you manage and scale your databases efficiently in the cloud. 🚀

Read More  `ris:ArrowDown`
# Explore Databases on AWS

## UNDERSTANDING THE HISTORY BEHIND ENTERPRISE DATABASES

Choosing a database used to be a straightforward decision. There were only a few options to choose from. In the past, you likely considered a few vendors and then inevitably chose one for all of your applications.

Businesses often selected the database technology they were going to use, even before they fully understood their use case. Since the 1970s, the database most commonly selected by businesses was a **relational database**.

## WHAT IS A RELATIONAL DATABASE?

A relational database organizes data into tables. Data in one table can be linked to data in other tables to create relationships—hence, the relational part of the name.

A table stores data in rows and columns. A row, often called a record, contains all information about a specific entry. Columns describe attributes of that entry. Here’s an example of three tables in a relational database.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/arXzkhNQSCCbBISQO0ZRaQ_3c6b85c478ca431b80171bd0640c72f1_image.png?expiry=1701388800000&hmac=pUACKrPjwN6AlM0CkN5Arg73hoBFDNRp9jQXlEe-VoY)

This shows a table for books, a table for sales, and a table for authors. In the books table, each row includes the book ISBN, the title, the author, and the format. Each of these attributes is stored in its own column. The books table has something in common with the other two tables: the author attribute. That common column creates a relationship between the tables.

The tables, rows, columns, and relationships between them is referred to as a **logical schema**. With relational databases, a schema is fixed. Once the database is operational, it becomes difficult to change the schema. This requires most of the data modeling to be done upfront before the database is active.

## WHAT IS A RELATIONAL DATABASE MANAGEMENT SYSTEM?

A relational database management system (RDBMS) lets you create, update, and administer a relational database. Here are some common examples of relational database management systems:

- MySQL
    
- PostgresQL
    
- Oracle
    
- SQL server
    
- Amazon Aurora
    

You communicate with most RDBMS by using Structured Query Language (SQL) queries. Here’s an example: SELECT * FROM table_name.

This query selects all of the data from a particular table. However, the real power of SQL queries is in creating more complex queries that let you pull data from several tables to piece together patterns and answers to business problems. For example, querying the sales table and the book table together to see sales in relation to an author’s books. This is made possible by a join, which we talk about next.

## THE BENEFITS OF USING A RELATIONAL DATABASE

There are many benefits to using a relational database. A few of them are listed here.

- **Joins:** You can join tables, enabling you to better understand relationships between your data.
    
- **Reduced redundancy:** You can store data in one table and reference it from other tables instead of saving the same data in different places.
    
- **Familiarity:** Relational databases have been a popular choice since the 1970s. Due to this popularity, technical professionals often have familiarity and experience with this type of database.
    
- **Accuracy:** Relational databases ensure that your data is persisted with high integrity and adheres to the ACID (atomicity, consistency, isolation, durability) principle.
    

## USE CASES FOR RELATIONAL DATABASES

Much of the world runs on relational databases. In fact, they’re at the core of many mission-critical applications, some of which you may use in your day to day life. Here are some common use cases for relational databases.Applications that have a solid schema that doesn’t change often, such as:

- Lift and shift applications that lifts an app from on-premises and shifts it to the cloud, with little or no modifications.
    

Applications that need persistent storage that follows the ACID principle, such as:

- Enterprise Resource Planning (ERP) applications
    
- Customer Relationship Management (CRM) applications
    
- Commerce and financial applications
    

## CHOOSE BETWEEN UNMANAGED AND MANAGED DATABASES

If you want to run a relational database on AWS, you first need to select how you want to run it: the unmanaged way or the managed way.

The paradigm of managed versus unmanaged services is similar to the Shared Responsibility Model. The Shared Responsibility Model distinguishes between AWS’s and the customer’s security responsibility over a service. Similarly, managed versus unmanaged can be understood as a tradeoff between convenience and control.

**On-Premises Database**

Let’s say you operate a relational database on-premises (in your own data center). In this scenario, you are responsible for all aspects of operation, including the security and electricity of the data center, the management of the host machine, the management of the database on that host, as well as optimizing queries and managing customer data. You are responsible for absolutely everything, which means you have control over absolutely everything.

**Unmanaged Database**

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/OonHLsR5RQif5MJkTfbIMw_0aa67d834275415d80ddd2de009c5ef1_image.png?expiry=1701388800000&hmac=YhYkgfKUHGmFG8fdGpR1nIP6EkHYRH1bAmeUU2tQRGM)

Now, let’s say you want to shift some of this work to AWS by running your relational database on Amazon EC2. If you host a database on Amazon EC2, AWS takes care of implementing and maintaining the physical infrastructure and hardware and installing the operating system of the EC2 instance. However, you’re still responsible for managing the EC2 instance, managing the database on that host, optimizing queries, and managing customer data.

This is what is often referred to as the **unmanaged database** option on AWS. AWS is responsible for and has control over the hardware and underlying infrastructure, and you are responsible and have control over management of the host and database.**Managed Database**

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/aSMN48saSWKSPaVJaQ7pow_922b2935f3dd441cb37409c4562a64f1_image.png?expiry=1701388800000&hmac=OF8Wu57GOKq-nVm2rw_pyDGbqennoMDVJZYqRdrS7Hs)

If you want to shift even more of the work to AWS, you can use a **managed database** service. These services provide the setup of both the EC2 instance and the database, and they provide systems for high availability, scalability, patching, and backups. However, you’re still responsible for database tuning, query optimization, and of course, ensuring that your customer data is secure. This provides you ultimate convenience, but you have the least amount of control compared to the two previous options.

**Resources**:

- [_External Site:_ AWS: What Is a Relational Database?](https://aws.amazon.com/relational-database/)
    
- [_External Site:_ AWS: Databases on AWS](https://aws.amazon.com/products/databases/)