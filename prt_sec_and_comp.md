# Security and Compliance

## Security

- **Shared Responsibilities:** In the public cloud, there is a shared respectability between AWS and us. AWS is responsible fot security **of** the cloud, they are responsible for **protecting** and **securing** their **infrastructure**, including hardware, networking, software (including patches of host OS) and the facilities to run AWS cloud services.
  
  We are responsible for security **in** the cloud, responsible for how the services are implemented and managing our application data including **encryption** options. We are responsible for securing our account, rotating credentials, **application security**, **identity** and **access management**. We are responsible for **guest OS** including **updates** and **security patches**. We are **restricting** internet access from VPCs, which include security group **firewall configurations**.

- **Well-Architected Framework:** This architecture is based on 6 pillars to focus on delivering optimum and resilient solutions at the least cost to the user.
  
  - **Operational Excellence:** focuses on creating applications that effectively support production workloads. Plan for and anticipate failure, learn from failure, deploy smaller, reversible changes, and script operations as code.
  
  - **Security:** focuses on putting mechanisms in place that help protect our system and data. It is important to automate security task. Encrypt data in transit and at rest, tack who did what and when, and ensure security at all application layers.
  
  - **Reliability:** focuses on designing systems that work consistently and recover quickly. Think how the app can recover automatically from failure. It's best practice to scale horizontally rather than vertically, and test recovery procedures.
  
  - **Performance Efficiency:** focuses on the effective use of computing resources to meet system and business requirements while removing bottlenecks. It's a best practice user *Serverless* architecture first, consider delegating task to a cloud vendor when appropriated, and use multi-region deployment because the end users may not get the best performance.

  - **Cost Optimization:** focuses on delivering optimum and resilient solutions at the best cost to the user. We should implement cloud financial management, measure our overall efficiency, and pay only for the resources our application requires.

  - **Sustainability:** focuses on environmental impacts, especially energy consumption and efficiency.

## Identity and Access Management (IAM)
