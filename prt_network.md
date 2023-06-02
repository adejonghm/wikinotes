# Network Services

## Virtual Private Cloud (VPC)

Specify thinks like IP address range, subnet, security groups, configure route tables.

VPCs can span multiple AZs in a single Region.

When creating a public subnet, it is necessary to create an Internet Gateway.

### Components

- **Network ACL (NACL):**
- **Router & Route Table:**
- **Internet Gateway:**
- **VPC Peering:**

### Creating a VPC, Public Subnet, Route Table & Internet Gatweway

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

- **Route 53:** Is a DNS service that routes users to apps
- **Direct Connect:** Is a dedicated physical network connection from you on-premises data center to AWS (Hybrid connection).
- **Site-to-Site VPN:** Is a service that create a secure  connection between your internet network and you AWS VPCs. When you use VPN you have a Virtual Private Gateway in you AWS and a Customer Gateway in the ohter side (On-Premises).
- **API Gateway:** Allows you to build and manage your APIs.
