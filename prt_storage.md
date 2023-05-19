# Storage Services

## Simple Storage Service (S3)

S3 is an Object Storage Service that is highly available. It uses **Buckets** to store **Objects** (or files), and you can configure them to be public or private.

S3 is essentially unlimited storage that can hold millions of objects per bucket, and you can upload objects via the console, the CLI, or programmatically from within code using SDKs.

In S3, you can configure security at the **bucket** or individual **object level** using ACLs, bucket policies, or access point policies. Also, you can **enable versioning** to create multiple versions of your files to protect against accidental deletion. Another option is to enable **S3 access logs** to track access to your bucket or objects.

Regarding data accessibility, there are two significant aspects **Durability** and **Availability**. Durability is important so your objects are never lost or compromised. S3 Standard is designed for 99.999999999% (Eleven 9's). Availability is important so you can access your data quickly when you need it.S3 Standard is designed for 99.99%.

### S3 Classes

- **S3 Standard:**
  - General purpose
  - Data stored across multiple AZs
  - Low latency & high throughput
  - Recommended for Frequently accessed data.
  - Durability: 99.999999999% & Availability: 99.99%
- **S3 Intelligent-Tiering:**
  - Automatically moves your data to the most cross-effective storage class.
  - Automatic cost saving.
  - Data stored across multiple AZs.
  - Recommended for Data with unknown or changing access pattern.
  - Durability: 99.999999999% & Availability: 99.9%
- **S3 Standard-Infrequent Access (IA):**
  - Data accessed less frequently but require rapid access.
  - Data stored across multiple AZs.
  - Cheaper than S3 Standard.
  - Recommended for Long-live data. Infrequently accessed. Millisecond access when needed.
  - Durability: 99.999999999% & Availability: 99.9%
- **S3 One Zone-Infrequent Access (IA):**
  - Like S3 Standard-IA but stored in a single AZ.
  - Costs 20% less than S3 Standard-IA
  - Recommended for Re-creatable data. Infrequently access with millisecond access. Availability and Durability are not essential.
  - Durability: 99.999999999% & Availability: 99.5%
- **S3 Glacier:**
  - Long-term data storage and archival for lower costs.
  - Data stored across multiple AZs.
  - Data retrieval takes longer. Options: 1-5 minutes, 3-5 hours, or 5-12 hours.
  - Recommended for Long-term backups. Cheaper storage option.
  - Durability: 99.999999999%
- **S3 Glacier Deep Archive:**
  - Like Glacier but longer access times. Options: 12 hours or 48 hours.
  - Cheapest of all S3 options.
  - Data stored across multiple AZs.
  - Recommended for Long-term data archival accessed once or twice a year. Retaining data for regulatory compliance requirements.
  - Durability: 99.999999999%
- **S3 Outposts:**
  - Provides object storage on-premises.
  - A single storage class.
  - Store across multiple devices and servers.
  - Recommended for Data that needs to kept local. Demanding application

## Additional Storage Services
