# Database Service

## Relational Database Service (RDS)

**Amazon Relational Database** is a service that makes it easy to launch and manage relational databases. This managed service (PaaS) automates tasks like database configuration, patching, infrastructure provisioning and backups, allowing you to spend less time completing administrative tasks and more time using data to innovate your applications.

RDS offers **high availability** and **fault tolerance** using **Multi-AZ** deployment, and it is possible to launch **read replicas** across Regions in order to provide enhanced **performance** and **durability**. Read Replicas are a read-only copy of your database for fast querying.

### RDS Engines

**Amazon Aurora:** is a relational database compatible with **PostgreSQL** and **MySQL**. It is **five times** faster than standard MySQL and **three times** faster than standard PostgreSQL. Amazon Aurora is an **auto-scaling** service that helps you **reduce costs** while ensuring **high availability**. Consider it if your workloads require high availability. It replicates six copies of your data across three AZ and continuously backs up your data to Amazon S3.

Amazon RDS is compatible with other engines like **PostgreSQL**, **MySQL**, **MariaDB**, **Oracle Database**, and **Microsoft SQL Server**.

## Nonrelational Database (NoSQL DB)

### DynamoDB

A **serverless** database service which means you don't have to provision, patch, or manage servers, this stuff is managed by AWS. DynamoDB automatically scales to massive workloads while maintaining consistent performance, making it a suitable choice for use cases that require high performance while scaling.

### DocumentDB

Is a fast, reliable, and fully managed (**serverless**) database service, that makes it easy to set up, operate, and scale MongoDB-compatible databases in the AWS.

## Additional DB services

- **Amazon ElastiCache:** is a service that adds caching layers on top of your databases to help improve read times for regular requests, ensuring high performance and low latency. It supports **Redis** and **Memcached**, and data can be lost because it is an **in-memory** database.

- **Amazon Neptune:** is a fully managed (**serverless**) graph database service that support highly connected datasets. You can use **Neptune** to build and run applications that work with highly connected datasets, such as **recommendation engines**, **fraud detection**, and **knowledge graphs**.

- **Amazon DynamoDB Accelerator (DAX)** is an in-memory cache for DynamoDB. It helps improve response times from single-digit milliseconds to microseconds.
