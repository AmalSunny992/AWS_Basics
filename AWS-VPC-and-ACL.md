# AWS VPC and Networking in AWS

## Objectives
- Understand Amazon VPC and its key components
- Learn how to create and manage subnets, route tables, and gateways
- Understand and configure security groups and network ACLs

## Concepts

### Introduction to VPC
Amazon VPC (Virtual Private Cloud) allows you to provision a logically isolated section of the AWS cloud where you can launch AWS resources in a virtual network that you define.

**Key Features:**
- Isolation: Complete control over your virtual networking environment.
- Customization: Customize your VPC's IP address range, create subnets, and configure route tables.
- Security: Use security groups and network ACLs to control inbound and outbound traffic.

### Differences Between Amazon VPC and Other VPCs
While the concept of a VPC is not unique to AWS and is offered by other cloud providers such as Google Cloud Platform (VPC) and Microsoft Azure (Virtual Network), Amazon VPC has specific features and integration with other AWS services that differentiate it:

#### Integration with AWS Services:

Amazon VPC integrates seamlessly with other AWS services like EC2, RDS, Lambda, and S3.

Provides advanced features like VPC endpoints, enabling private connectivity to AWS services without using the internet.

#### Networking Features:

Offers extensive networking capabilities such as VPC Peering, Transit Gateway, and AWS PrivateLink.

Provides advanced traffic control features, including security groups and network ACLs.

#### Management and Monitoring:

Includes tools like Amazon CloudWatch and AWS CloudTrail for monitoring and logging VPC activity.

Offers VPC Flow Logs to capture information about IP traffic going to and from network interfaces in the VPC.

#### Security and Compliance:

Provides built-in security features, including encryption in transit and at rest, security groups, and IAM policies.

Complies with various regulatory standards and certifications, enhancing security and governance.


### Cost of Amazon VPC
Amazon VPC itself does not incur charges directly, but there are costs associated with certain features and resources within a VPC:

Data Transfer: Charges apply for data transferred out of the VPC to the internet.

NAT Gateway: Priced hourly and based on data processed.

VPN Connections: Charged based on hourly usage and data transfer.

VPC Endpoints: Priced per hour and per GB of data processed.

Elastic IPs: Charged when not associated with a running instance.

### When to Use Amazon VPC

Amazon VPC is ideal for:

**Isolated Network Environments**: When you need a private, isolated section of the AWS cloud.

**Enhanced Security**:
When you require fine-grained control over network traffic, including security groups and network ACLs.

**Regulatory Compliance**:
When you must comply with specific regulatory and compliance requirements that necessitate a secure and isolated environment.

**Complex Network Architectures**:
For complex network topologies, such as multi-tier applications or hybrid cloud environments.

**Custom Networking**:
When you need custom IP address ranges, subnets, route tables, and gateways.

**Integration with On-Premises Networks**:
When you need to extend your on-premises network to the cloud using VPN or AWS Direct Connect.


### Subnets, Route Tables, and Gateways

#### Subnets
A subnet is a range of IP addresses in your VPC. You can launch AWS resources into a specified subnet.

**Steps to Create a Subnet:**

- Open the VPC Dashboard:
    - Go to the AWS Management Console.
    - Select "VPC" from the services menu.

- Create a VPC:
    - Click on "Your VPCs" and then "Create VPC".
    - Enter a name, IPv4 CIDR block (e.g., 10.0.0.0/16), and any other desired settings.
    - Click "Create".

- Create a Subnet:
    - Click on "Subnets" and then "Create subnet".
    - Choose the VPC you created.
    - Enter a name, select an Availability Zone, and specify the IPv4 CIDR block (e.g., 10.0.1.0/24).
    - Click "Create".

#### Route Tables
A route table contains a set of rules, called routes, that determine where network traffic is directed.

**Steps to Create and Associate a Route Table:**

- Open the VPC Dashboard.

- Create a Route Table:
    - Click on "Route Tables" and then "Create route table".
    - Enter a name and select the VPC.
    - Click "Create".

- Edit Routes:
    - Select the newly created route table.
    - Click on the "Routes" tab and then "Edit routes".
    - Add routes as needed (e.g., destination 0.0.0.0/0 with target as an Internet Gateway for public subnets).

- Associate with Subnet:
    - Click on the "Subnet associations" tab and then "Edit subnet associations".
    - Select the subnet to associate with the route table.
    - Click "Save".

#### Gateways
Gateways allow your VPC to communicate with the Internet and other AWS services.

**Types of Gateways:**

Internet Gateway (IGW): Allows communication between instances in your VPC and the internet.

NAT Gateway: Enables instances in a private subnet to connect to the internet while preventing inbound traffic from the internet.

**Steps to Create an Internet Gateway:**

- Open the VPC Dashboard.
- Create an Internet Gateway:
    - Click on "Internet Gateways" and then "Create internet gateway".
    - Enter a name and click "Create".

- Attach to VPC:
    - Select the newly created internet gateway.
    - Click "Actions" and then "Attach to VPC".
    - Select your VPC and click "Attach internet gateway".

### Security Groups and Network ACLs

#### Security Groups
A security group acts as a virtual firewall for your instance to control inbound and outbound traffic.

**Steps to Create a Security Group:**

- Open the VPC Dashboard.
- Create a Security Group:
    - Click on "Security Groups" and then "Create security group".
    - Enter a name, description, and select the VPC.
    - Add inbound and outbound rules as needed.
    - Click "Create".


#### Network ACLs (Access Control Lists)
Network ACLs are an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets.

**Steps to Create a Network ACL:**

- Open the VPC Dashboard.
- Create a Network ACL:
    - Click on "Network ACLs" and then "Create network ACL".
    - Enter a name and select the VPC.
    - Click "Create".

- Edit Inbound and Outbound Rules:
    - Select the newly created network ACL.
    - Click on the "Inbound rules" tab and then "Edit inbound rules".
    - Add rules as needed (e.g., allow all traffic on port 80).
    - Click "Save".
    - Repeat for outbound rules.

- Associate with Subnets:
    - Click on the "Subnet associations" tab and then "Edit subnet associations".
    - Select the subnet to associate with the network ACL.
    - Click "Save".


## Summary
In this lesson, you learned about Amazon VPC, how to create and manage subnets, route tables, and gateways, and how to configure security groups and network ACLs. These components are crucial for setting up a secure and efficient network in AWS.