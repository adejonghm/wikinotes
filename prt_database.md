# Database Service

## Relational Database Service (RDS)

**Amazon Relational Database** is a service that makes it easy to launch and manage relational databases. This managed service (PaaS) automates tasks like database configuration, patching, infrastructure provisioning and backups, allowing you to spend less time completing administrative tasks and more time using data to innovate your applications.

RDS offers **high availability** and **fault tolerance** using **Multi-AZ** deployment, and it is possible to launch **read replicas** across Regions in order to provide enhanced **performance** and **durability**. Read Replicas are a read-only copy of your database for fast querying.

### RDS Engines

**Amazon Aurora:** is a relational database compatible with **PostgreSQL** and **MySQL**. It is **five times** faster than standard MySQL and **three times** faster than standard PostgreSQL. Amazon Aurora is an **auto-scaling** service that helps you **reduce costs** while ensuring **high availability**. Consider it if your workloads require high availability. It replicates six copies of your data across three AZ and continuously backs up your data to Amazon S3.

Amazon RDS is compatible with other engines like **PostgreSQL**, **MySQL**, **MariaDB**, **Oracle Database**, and **Microsoft SQL Server**.

## Nonrelational Database (NoSQL DB)

### Amazon DynamoDB

A **serverless** database service which means you don't have to provision, patch, or manage servers, this stuff is managed by AWS. DynamoDB automatically scales to massive workloads while maintaining consistent performance, making it a suitable choice for use cases that require high performance while scaling.

### Amazon DocumentDB

Is a fast, reliable, and fully managed (**serverless**) database service, that makes it easy to set up, operate, and scale MongoDB-compatible databases in the AWS.

## Additional Database services

- **Amazon ElastiCache:** is a service that adds caching layers on top of your databases to help improve read times for regular requests, ensuring high performance and low latency. It supports **Redis** and **Memcached**, and data can be lost because it is an **in-memory** database.

- **Amazon Neptune:** is a fully managed (**serverless**) graph database service that support highly connected datasets. You can use **Neptune** to build and run applications that work with highly connected datasets, such as **recommendation engines**, **fraud detection**, and **knowledge graphs**.

- **Amazon DynamoDB Accelerator (DAX)** is an in-memory cache for DynamoDB. It helps improve response times from single-digit milliseconds to microseconds.

- **Amazon Database Migration Service (DMS):** enables you to migrate relational databases, nonrelational databases, and other types of data stores. You can migrate your data into the AWS Cloud or between combinations of cloud and on-premises setups. **DMS** provides virtually no downtime, which means your source database remains operational and provides continuous data replication.

- **Amazon Server Migration Service (SMS):** Allows to migrate your on-premises server, or group of servers to AWS. When you migrate your server, automatically is saved as a New Amazon Image (AMI) and then you can use this AMI to launch your server as a EC2 Instance.

- **Amazon Snow Family:** Allows you to transfer large amounts of on-premises data to AWS using a physical device.
  
  - **Snowcone:** Is the smallest member that allows you to transport up to 8TB of data using HDD and 14TB using SSD. You can use **Snowcone** either **offline** by shipping the device to AWS, or **online** by using AWS DataSync.
  - **Snowball Edge:** Can do local processing and edge-computing workloads in addition to transferring data between your local environment and the AWS Cloud. It is a device with a Petabyte-scale data transport solution that can transfer data **in** and **out**, and it is cheaper than internet transfer. This Snow member is compatible with **EC2** and **Lambda**.
  - **Snowmobile:** Allows you to transfer data on a scale of multi-petabytes or exabytes. The data is loaded to S3 and it is secured transported.

- **Amazon DataSync:** Is an online data movement and discovery service that simplifies data migration and helps you quickly, easily, and securely transfer your file or object data from on-premises to AWS and between AWS storage services. DataSync copies the data over **Direct Connect** or on the **Internet**, and it is possible to replicate data cross-Region or cross-account.
