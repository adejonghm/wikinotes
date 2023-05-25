# Storage Services

## Simple Storage Service (S3)

S3 is an Object Storage Service that is highly available. It uses **Buckets** to store **Objects** (or files), and you can configure them to be public or private.

S3 is essentially unlimited storage that can hold millions of objects per bucket, and you can upload objects via the console, the CLI, or programmatically from within code using SDKs.

In S3, you can configure security at the **bucket** or individual **object level** using ACLs, bucket policies, or access point policies. Also, you can **enable versioning** to create multiple versions of your files to protect against accidental deletion. Another option is to enable **S3 access logs** to track access to your bucket or objects.

Regarding data accessibility, there are two significant aspects **Durability** and **Availability**. Durability is important so your objects are never lost or compromised. S3 Standard is designed for 99.999999999% (Eleven 9's). Availability is important so you can access your data quickly when you need it.S3 Standard is designed for 99.99%.

### Classes

|S3 Standard|S3 Intelligent-Tiering|S3 Standard-Infrequent Access (IA)|S3 One Zone-Infrequent Access (IA)|S3 Glacier|S3 Glacier Deep Archive|S3 Outposts|
|---|---|---|---|---|---|---|
|- General purpose.<br>- Data stored across multiple AZs.<br>- Low latency & high throughput.|- Automatically moves your data to the most cross-effective storage class.<br>- Automatic cost saving.<br>- Data stored across multiple AZs.|- Data accessed less frequently but require rapid access.<br>- Data stored across multiple AZs.<br>- Cheaper than S3 Standard.|- Like S3 Standard-IA but stored in a single AZ.<br>- Costs 20% less than S3 Standard-IA|- Long-term data storage and archival for lower costs.<br>- Data stored across multiple AZs.<br>- Data retrieval takes longer. Options: 1-5 minutes, 3-5 hours, or 5-12 hours.|- Like Glacier but longer access times. Options: 12 hours or 48 hours.<br>- Cheapest of all S3 options.<br>- Data stored across multiple AZs.|- Provides object storage on-premises.<br>- A single storage class.<br>- Store across multiple devices and servers.|
|**Recommended for:** Frequently accessed data.|**Recommended for:** Data with unknown or changing access pattern.|**Recommended for:** Long-live data. Infrequently accessed. Millisecond access when needed.|**Recommended for:** Re-creatable data. Infrequently access with millisecond access. Availability and Durability are not essential.|**Recommended for:** Long-term backups. Cheaper storage option.|**Recommended for:** Long-term data archival accessed once or twice a year. Retaining data for regulatory compliance requirements.|**Recommended for:** Data that needs to kept local. Demanding application.|
|**Durability:** 99.999999999% <br> **Availability:** 99.99%|**Durability:** 99.999999999% <br> **Availability:** 99.9%|**Durability:** 99.999999999% <br> **Availability:** 99.9%|**Durability:** 99.999999999% <br> **Availability:** 99.5%|**Durability:** 99.999999999%|**Durability:** 99.999999999%| |

## Additional Storage Services

- **Instance Store:** is a *local* storage that is *physically* attached to the host computer and cannot be removed (basically, the HDD or a flash drive that you select when creating a EC2). They have *low latency* and are *faster* with higher I/O speeds, but they are *temporary*, as data is lost when the EC2 Instance stops. It is Recommended for temporary storage, and data replicated across multiple instances.
  
- **Elastic Block Storage (*EBS*):** is a storage that can be *attached* to the EC2 Instances. The *data persist* when the instances are not running or even when they are deleted. This type of storage is tied to *one* AZ and can only be attached to *one* Instance in the *same* AZ. It is recommended for quickly accessible data, running a db on an Instance, and long-term data storage.

- **Elastic Files system (*EFS*):** is a *serverless* network file system for sharing files. They are only supports Linux file system and are accessible *across different AZs* in the *same Region*. This type of storage is more *expensive* than EBS, so it is recommended when business-critical apps *need shared directories* and when you are doing a *lift-and-shift migration* on an existing enterprise app.

- **Storage Gateway:** is a hybrid storage service that can you use to store data in the cloud and keep some data locally with low latency. With this, you can connect on-premises and cloud data, that is useful to moving backups to the cloud, reduce costs by picking and choosing what data you host in the cloud, and keeping latency low by deciding what data you want to access directly in you local network.

- **AWS Backup:** helps to you manage data backups across multiple AWS services. This service is used to schedule, execute and access backed up data across many AWS services EBS, EFS, EC2 Instance Store and other. In it, you create a backup plan when you determine what data you're backing up, how frequently you could like to back it up, and how long you'd like to retain that data.
