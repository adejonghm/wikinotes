# Security and Compliance

## Security

- **Shared Responsibilities:** In the public cloud, there is a shared respectability between AWS and us. AWS is responsible for the security **of** the cloud, they are responsible for **protecting** and **securing** their **infrastructure**, including hardware, networking, software (including patches of host OS), and the facilities to run AWS cloud services.
  
  We are responsible for security **in** the cloud, responsible for how the services are implemented, and managing our application data including **encryption** options. We are responsible for securing our account, rotating credentials, **application security**, **identity**, and **access management**. We are responsible for **guest OS** including **updates** and **security patches**. We are **restricting** internet access from VPCs, which include security group **firewall configurations**.

- **Well-Architected Framework:** This architecture is based on 6 pillars to focus on delivering optimum and resilient solutions at the least cost to the user.
  
  - **Operational Excellence:** focuses on creating applications that effectively support production workloads. Plan for and anticipate failure, learn from failure, deploy smaller, reversible changes, and script operations as code.
  
  - **Security:** focuses on putting mechanisms in place that help protect our system and data. It is important to automate security tasks. Encrypt data in transit and at rest, tack who did what and when, and ensure security at all application layers.
  
  - **Reliability:** focuses on designing systems that work consistently and recover quickly. Think about how the app can recover automatically from failure. It's best practice to scale horizontally rather than vertically and test recovery procedures.
  
  - **Performance Efficiency:** focuses on the effective use of computing resources to meet system and business requirements while removing bottlenecks. It's a best practice to use *Serverless* architecture first, consider delegating tasks to a cloud vendor when appropriate, and use multi-region deployment because the end users may not get the best performance.

  - **Cost Optimization:** focuses on delivering optimum and resilient solutions at the best cost to the user. We should implement cloud financial management, measure our overall efficiency, and pay only for the resources our application requires.

  - **Sustainability:** focuses on environmental impacts, especially energy consumption and efficiency.

## Identity and Access Management (IAM)

IAM allows us to control access to our AWS services and helping **secure** our cloud resources. We define **who** (*Identities*) has access and **what** (*Access*) can they do. We can create Roles, give permissions, and integrate with MFA. IAM is a **free global** service.

- **Identity:** Define **who** can access our resources, it's considered Root User, individual users, groups, and roles.
  - **Authentication:** is when we present our **identity** (**username**) and provide a **verification** method like our **password**.

- **Access:** defines **what** resources they can access once they have access to our account, and typically we control the access through policies, customer-managed policies, AWS-managed policies, and permissions boundaries. Permission boundaries limit the scope of what a user can do.
  - **Authorization:** determines which services and resources the authenticated identity has **access** to.

### Users

- **Root user:** Things that only the root user can do. This user is not meant to be used for day-to-day tasks.
  - Close our account
  - Change the email address
  - Modify our support  plan

- **Individual Users:** They are created in IAM and are used for everyday tasks. Individual users can do this.
  - Perform admin tasks
  - Launch resources
  - Access application code

If we need to grant access to users that uses the AWS CLI, create an ssh key pair.

### Groups

Groups are a collection of **IAM** users that help us apply common access control to all group members. When we use groups, we save time when we need to define access permissions for a large number of users. This way, if we need to remove permissions for a specific user, we only remove them from the group.
