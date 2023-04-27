# Cloud Practitioner (CLF-C01)

## The Cloud Computing

Cloud computing is the *on-demand delivery* of compute power, database, storage, applications, and other IT resources through a cloud services platform via the internet with *pay-as-you-go pricing*. With cloud computing, you don’t need to make large upfront *investments in hardware* and spend a lot of time on the heavy lifting of *managing that hardware*. Instead, you can provision exactly the *right type and size* of computing resources you need to power your newest bright idea or operate your IT department. You can access as many resources as you need, almost *instantly*, and only *pay for what you use*. The cloud services platform provides *rapid access to flexible and low-cost* IT resources.

### Advantages of cloud computing

- **Go global in minutes:** Put your application in multiple regions around the world. This means you can provide lower latency and a better experience for your customers at minimal cost.
- **Benefit from massive economies of scale:** By using cloud computing, you can achieve a lower variable cost than you can get on your own.
- **Stop spending money running and maintaining data centers:** Cloud computing lets you focus on your own customers, rather than on the heavy lifting of racking, stacking, and powering servers. Focus on your business, not the infrastructure.
- **Trade fixed expense for variable expense:** Instead of having to invest heavily in data centers and servers, you can pay only when you consume computing resources, and pay only for how much you consume.
- **Stop guessing capacity:** Eliminate guessing about your infrastructure capacity needs. With cloud computing, these problems go away. You can access as much or as little capacity as you need and scale up and down as required in only a few minutes.
- **Increase speed and agility:** In a cloud computing environment, new IT resources are only a click away, which means that you reduce the time to make those resources available to your developers from weeks to just minutes.

### Concepts

- **High Availability:** Systems are designed to operate continuously without failure for a long time. These systems avoid loss of service by reducing or managing failures.
- **Elasticity:** With it, you don't have to plan ahead of time how much capacity you need. You can provision only what you need, and then grow and shrink based on demand.
- **Agility:** It is defined as the ability to quickly build, test, and deploy applications and software in the cloud as you need it, often in response to market changes.
- **Durability:** Is all about long-term data protection. This means your data will remain intact without corruption.
- **CapEx:** Refers to the costs the organization must incur to purchase fixed assets that will offer ongoing, long-term benefits well past the current tax year.
- **OpEx:** Instead of revolving around one big bill up front, OpEx purchases are typically pay-per-use or subscription-based. With that, OpEx assets are not the exclusive property of the organization that uses them, but of the service provider.

### Cloud Computing Models

- **IaaS:** Contains the building blocks for cloud IT, typically providing access to **network** functions, **computers** (virtual or bare metal), and data **storage** space. OS, configurations, and maintenance are the responsibility of the user.
- **PaaS:** Removes the need for the user to manage the underlying infrastructure (hardware & OS) and allows you to focus on deploying and managing your **applications** (**Data** and **Access**).
- **SaaS:** Gives you a complete solution managed and executed by the service provider, where you don't have to think about how the service is maintained or the underlying infrastructure is managed. Just provide the **data** to the application.

### Cloud Deployment Models

- **Private:** Services and computing resources used exclusively by users from one business or organization. It can be located in the organization (on-premises) or, it can be hosted in the cloud (dedicated cloud offered by cloud providers).
- **Public:** Services offered over the public Internet to individuals and organizations who wish to purchase. Cloud resources (computer, storage, network, and others) are operated by external providers (the owners) and delivered on demand.
- **Hybrid:** Is a combination of **public** and **private** clouds. The most common method of hybrid deployment is between the cloud and existing on-premises infrastructure to extend, and grow, an organization's infrastructure into the cloud while connecting cloud resources to the internal system.

### Regions

A *Region* is a physical location in the world that contains 2 or more Availability Zones. Each region is isolated and fully independent, so if one of them is affected, the others are not. Regions are grouped in geographically isolated locations around the globe, called *Geographical Locations*, On the other hand, most of the resources are tied to a specific Region, and you should set up resources in Regions closest to your users.

### Availability Zones(AZs)

They are a collection of *one* or *more* physically separate *data centers*, each with redundant power, networking, and connectivity housed in different facilities. AZs are connected through *low latency* links, are *fault-tolerant*, and allow *high availability*. An AZ is associated with a single Region.

### Edge Locations

An edge location is used to *cache content* for *fast delivery* to your users, using the **Content Delivery Network(CDN)**, thereby ensuring *low latency*. There are more edge locations than Regions and AZs.


## Services

### Compute

#### Elastic Computer Cloud (EC2)

**EC2** is the essential service for *managing virtual instances* (VMs). These instances can be provisioned by clicking a button, and a *preconfigured template* called **Amazon Machine Image (AMI)** can be used to launch the EC2 instances. In the *Free tier* plan, you get *750 compute hours* per month. You can use this service to deploy a database or a web application.

##### Features

- **Load Balancing:** automatically distributes your incoming application traffic across multiple EC2 instances. You have different types of balancing: *CLASSIC LOAD BALANCERS, APPLICATION LOAD BALANCERS, GATEWAY LOAD BALANCERS, NETWORK LOAD BALANCERS*.
- **Auto Scaling (Horizontal Scaling/Scaling Out):** *adds* or *replaces* EC2 instances *automatically* across AZs, based on need and changing demand. This feature reduces the impact of system failures and improves the availability of your applications.

*Note:* **Vertical Scaling/Scaling Up** is when you upgrade your existing EC2 Instance with more power (RAM and CPU) in an existing server.

##### Connectivity

You can have more methods to access an EC2 instance:

- **AWS Management Console:** You're able to configure and manage your instances via a web browser.
- **SSH:** Allows you to establish a secure connection to your instance from your local laptop. This is the most common way to connect to Linux EC2 instances.
- **EC2 Instance Connect (EIC):** Allows you to use IAM policies to control SSH access to your instances, removing the need to manage SSH keys.
- **AWS Systems Manager:** Allows you to manage your EC2 instances via a web browser or the AWS CLI.

##### Pricing (*)
- **On-Demand:** A fixed price in which you are billed *down to the second* based on the instance type. You can increase or decrease your compute capacity depending on the demands of your application and pay only for what you use.
When you use:
	- You care about low cost and flexibility of Amazon EC2 without any upfront payment or long-term commitment.
	- Applications with short-term, spiky, or unpredictable workloads that *cannot* be interrupted.
	- Applications being developed or tested on Amazon EC2 for the first time.
	- Your workloads will *not* run longer than a year.

- **Spot (Cheapest Option):** Allows you to take advantage of *unused* EC2 capacity in the AWS cloud. Your request is attended to *only* when there is available capacity for your demand. You can *save up to 90%* compared to On-Demand pricing.
When you use:
	- Your workloads *can* be interrupted.
	- You are not concerned about the *start* or *stop* time of your app.

- **Reserved instances:** Allow you to commit to a specific Instance type in a particular region for 1 or 3 years. You can *save up to 75%* off On-Demand prices.
When you use:
	- Your app has *steady state usage*, and you can commit to 1 or 3 years.
	- You can pay money *upfront* in order to receive discounts on On-Demand prices.

- **Dedicated Hosts:** Allow you to pay for a physical server that is fully dedicated to running your instances, meaning the server isn't share with others. You can *save up to 70%* off On-Demand prices.
When you use:
	- You want to *bring your* server-bound *license* from vendors like Microsoft or others, helping to cut costs.
	- You have regulatory or corporate compliance requirements around tenancy model.

- **Saving Plans:** Allow you to commit to compute usage (measured per hour) for 1 or 3 years. You can *save up to 72%* off On-Demand prices, but this doesn't provide a capacity reservation.
When you use:
	- You want to *lower bill* across multiple compute services.
	- You want the *flexibility* to change compute services, instances type, Operating Systems or Regions.
