# Compute Services

## Elastic Computer Cloud (EC2)

**EC2** is the essential service for **managing virtual instances** (VMs). These instances can be provisioned by clicking a button, and a **preconfigured template** called **Amazon Machine Image (AMI)** can be used to launch the EC2 instances. In the **Free tier** plan, you get **750 compute hours** per month. You can use this service to deploy a database or a web application.

In the EC2 web dashboard, you will only be able to see the EC2s that are running in that region. If you have EC2s running in other regions, you will not be able to see them until you change to that region.

Example:
If I'm in Region A, I won't see EC2s running in Region B.

### Types

- **General purpose instances:** Provide a balance of compute, memory, and networking resources. You can use them for a variety of workloads, such as:

  - application servers
  - gaming servers
  - backend servers for enterprise applications
  - small and medium databases

- **Compute optimized instances:** These are ideal for compute-bound applications that benefit from high-performance processors. Like general purpose instances, you can use compute optimized instances for workloads such as web, application, and gaming servers. However, the difference is compute optimized applications are ideal for high-performance web servers, compute-intensive applications servers, and dedicated gaming servers. You can also use compute optimized instances for batch processing workloads that require processing many transactions in a single group.

- **Memory optimized instances:** These are designed to deliver fast performance for workloads that process large datasets in memory. Suppose that you have a workload that requires large amounts of data to be preloaded before running an application. This scenario might be a high-performance database or a workload that involves performing real-time processing of a large amount of unstructured data. In these types of use cases, consider using a memory optimized instance. Memory optimized instances enable you to run workloads with high memory needs and receive great performance.

- **Accelerated computing instances:** These use hardware accelerators, or coprocessors, to perform some functions more efficiently than is possible in software running on CPUs. Examples of these functions include floating-point number calculations, graphics processing, and data pattern matching. Accelerated computing instances are ideal for workloads such as graphics applications, game streaming, and application streaming.

- **Storage optimized instances:** These are designed for workloads that require high, sequential read and write access to large datasets on local storage. Examples of workloads suitable for storage optimized instances include distributed file systems, data warehousing applications, and high-frequency online transaction processing (OLTP) systems. Storage optimized instances are designed to deliver tens of thousands of low-latency, random IOPS to applications.

### Connectivity

You can have more methods to access an EC2 instance:

- **AWS Management Console:** You're able to configure and manage your instances via a web browser.
- **SSH:** Allows you to establish a secure connection to your instance from your local laptop. This is the most common way to connect to Linux EC2 instances.
- **EC2 Instance Connect (EIC):** Allows you to use IAM policies to control SSH access to your instances, removing the need to manage SSH keys.
- **AWS Systems Manager:** Allows you to manage your EC2 instances via a web browser or the AWS CLI.

### Pricing (*)

- **On-Demand:** A fixed price in which you are billed **down to the second** based on the instance type. You can increase or decrease your compute capacity depending on the demands of your application and pay only for what you use.
When you use:
  - You care about low cost and flexibility of Amazon EC2 without any upfront payment or long-term commitment.
  - Applications with short-term, spiky, or unpredictable workloads that **cannot** be interrupted.
  - Applications being developed or tested on Amazon EC2 for the first time.
  - Your workloads will **not** run longer than a year.

- **Spot (Cheapest Option):** Allows you to take advantage of **unused** EC2 capacity in the AWS cloud. Your request is attended to **only** when there is available capacity for your demand. You can **save up to 90%** compared to On-Demand pricing.
When you use:
  - Your workloads **can** be interrupted.
  - You are not concerned about the **start** or **stop** time of your app.

- **Reserved instances:** Allow you to commit to a specific Instance type in a particular region for 1 or 3 years. You can **save up to 75%** off On-Demand prices.
When you use:
  - Your app has **steady state usage**, and you can commit to 1 or 3 years.
  - You can pay money **upfront** in order to receive discounts on On-Demand prices.

- **Dedicated Hosts:** Allow you to pay for a physical server that is fully dedicated to running your instances, meaning the server isn't share with others. You can **save up to 70%** off On-Demand prices.
When you use:
  - You want to **bring your** server-bound **license** from vendors like Microsoft or others, helping to cut costs.
  - You have regulatory or corporate compliance requirements around tenancy model.

- **Saving Plans:** Allow you to commit to compute usage (measured per hour) for 1 or 3 years. You can **save up to 72%** off On-Demand prices, but this doesn't provide a capacity reservation.
When you use:
  - You want to **lower bill** across multiple compute services.
  - You want the **flexibility** to change compute services, instances type, Operating Systems or Regions.

## Lambda

Lambda is a **serverless** compute service that allows you to run code without managing servers. **Serverless** means you don't worry about managing servers as with EC2. In Lambda, you create the application code called functions using many popular languages like Java, Go, PowerShell, Node.js, C#, Python, and Ruby without worrying about the rest. Also, Lambda can execute your code in response to events.

Lambda functions have a timeout of 15 minutes, which allows you to optimize code execution time and performance with the proper function memory size. Respond to high demand in double-digit milliseconds with provisioned concurrency.

### Pricing

- **Compute time:** Save costs by **paying** only for computing **time used** — there is no charge if your code is not running.
- **Request count:** A request is **counted** each time it **starts execution**. Test invokes in the console count as well.
- **Always free:** The free usage tier includes **1 million** free requests each month.

## Additional Compute Services

### Services that you can use with EC2

- **Elastic Load Balancing (ELB):** It is the service that automatically distributes your incoming application traffic across multiple EC2 instances. This acts as a single entry point for your **Auto Scaling Group** distributing the workload across your instances so that no one has to carry the bulk of it. You have different types of balancing: *CLASSIC LOAD BALANCERS, APPLICATION LOAD BALANCERS, GATEWAY LOAD BALANCERS, NETWORK LOAD BALANCERS*.

- **Auto Scaling Group (Horizontal Scaling/Scaling Out): Add** or **replace** EC2 instances **automatically** across AZs, based on need and changing demand. This feature reduces the impact of system failures and improves the availability of your applications.
When you create an **Auto Scaling Group**, you can set the **minimum number** of Amazon EC2 instances. This is the number of EC2 instances that launch immediately after you have created the group. Next, you can set the **desired capacity**, the number of instances your application will use by default. When you don't define the **desired capacity** in your Auto Scaling Group, the **minimum number** is used as the **desired capacity**. Finally, you can set the **maximum capacity**, which is the maximum number of EC2 Instances that will run when your Auto Scaling Group reaches the critical moment. In this case, you only pay for the instances when you use them, that is, when the instances are not running, you don't pay for them.

*Note:* **Vertical Scaling/Scaling Up** is when you upgrade your existing EC2 Instance with more power (RAM and CPU) in an existing server.

### Other Services

- **Simple Queue Service (SQS):** Allows to send, store, and receive messages between software components at any volume, without losing messages or requiring other services to be available.
- **Simple Notification Service (SNS):** Allows you to *send emails* and *text messages* from your applications. You can use it to send notifications about your infrastructure or other incident.
- **Elastic Container Service (ECS):**
- **Elastic Kubernetes Service (EKS):**
- **Fargate:** is the *serverless* compute engine for containers. It is autoscaling.
- **Lightsail:** is a *compute service* that allows you to quickly launch all the resources you need for small projects. You can deploy preconfigured applications at the click of a button, including a virtual machine, SSD-based storage, data transfer, DNS management, and a static IP. This serviceProvides a low monthly fee, as low as $3.50.
- **Outposts:** allows you to run cloud services in your internal data center supporting workloads that need to remain on-premises due to latency or data sovereignty needs. This service is used for a *hybrid deployment model*.
- **Batch:** is a *compute service* that allows you to process large workloads, running hundreds and thousands of smaller batch processing jobs. This service provisions instances dynamically based on volume.
