# Network Services

## Virtual Private Cloud (VPC)

**VPC** is a foundational service that allows you to provision a secure and isolated section in the AWS Cloud where you launch your resources, like EC2 instances. Within a VPC, you can organize the resources into subnets, you can specify thinks like IP address range, security groups, and configure route tables. VPCs spans AZs in a Single Region. When you use VPCs, if you have a public subnet, it is necessary to create an Internet Gateway.

A subnet is a section of a VPC in which you can group resources based on security or operational needs. Subnets can be public or private:

- **Public** subnets contain resources that need to be accessible by the public, such as an online store’s website.
- **Private** subnets contain resources that should be accessible only through your private network, such as a database that contains customers’ personal information and order histories.

### Components

- **Network ACL (NACL):** Is a virtual firewall that controls inbound and outbound traffic at the subnet level. Each AWS account includes a default network ACL. When configuring your VPC, you can use your account’s default network ACL or create custom network ACLs. By default, this ACL allows all inbound and outbound traffic. ACLs perform **stateless** packet filtering. They remember nothing and check packets that cross the subnet border each way: inbound and outbound.
- **Security Group:** is a virtual firewall that controls inbound and outbound traffic for an Amazon EC2 instance. By default, a Security Group denies all inbound traffic and allows all outbound traffic. Security groups perform **stateful** packet filtering. They remember previous decisions made for incoming packets.
- **Internet Gateway:** Is a connection between a VPC and the internet that allowing public traffic to access your resources inside the VPC.
- **Route Table:** Contains a set of rules, called routes, that determine where network traffic from your subnet or gateway is directed. Each subnet in a VPC must be associated with a **Route Table**, which controls the routing for the subnet.
- **VPC Peering Connection:** is a networking connection **between** two VPCs that enables you to route traffic between them privately. You can create a connection between your VPCs, with a VPC in another AWS account, or with a VPC in a different AWS Region.

### Creating a VPC, Public Subnet, Route Table & Internet Gateway

1. Create a VPC
   1. CIDRs: 10.0.0.0/16
2. Create a public subnet
   1. Associate with the VPC
   2. Select the AZ in your Region
   3. CIDRs: 10.0.0.0/24
3. Create a Route
   1. Select the subnet and edit the subnet setting. In Auto-assign IP setting, enable auto-assign public IPv4 address to set automatically a public IP addresses for instances launched in this subnet.
4. Create an Internet Gateway
   1. Attach this IG to a VPC (Action button)
5. Create Route tables
   1. Associate with the VPC
   2. After created, Edit Routes in the Routes tab.
   3. Add new route. As a destination, select 0.0.0.0/0 and target internet gateway (created before).
   4. Select Subnet Association tab, then Edit subnet associations, and finally, select the subnet you want to associate.

## Additional Network Services

- **Route 53:** Is a DNS service that routes users to apps. Performs health checks on AWS resources, and support hybrid cloud architecture.
- **Direct Connect:** Is a dedicated private connection between you on-premises data center and a VPC (this connection is over a dedicated physical network and not use your internet service provider). This private connection helps you to reduce network cost and increase the amount of bandwidth.
- **Site-to-Site VPN:** Is a service that create a secure connection **between** your **Internal Network** and AWS, similar to a Direct Connection, but the traffic is over the public internet. In this service, the data is automatically encrypted. When you use VPN you have a Virtual Private Gateway in you AWS and a Customer Gateway in the other side (On-Premises).
- **API Gateway:** Allows you to build and manage your APIs to share data between systems. This service can be integrated with services like Lambda.
