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
![image](https://github.com/user-attachments/assets/5cbdbad9-1adf-4f41-9d31-7981d993f77c)

- Create a VPC:
    - Click on "Your VPCs" and then "Create VPC".
    - Enter a name, IPv4 CIDR block (e.g., 10.0.0.0/16), and any other desired settings.
    - Click "Create".
![image](https://github.com/user-attachments/assets/77123358-f090-4256-9b9f-75ef3e71a3f9)
![image](https://github.com/user-attachments/assets/511556c1-2138-46ef-bee5-86f515884c08)
![image](https://github.com/user-attachments/assets/a5cd9d08-c9af-442b-a7aa-13a113dfa374)

- Create a Subnet:
    - Click on "Subnets" and then "Create subnet".
    - Choose the VPC you created.
    - Enter a name, select an Availability Zone, and specify the IPv4 CIDR block (e.g., 10.0.1.0/28).
    - Click "Create".
![image](https://github.com/user-attachments/assets/71274c3e-796a-4840-9889-53ef0b5dab17)
![image](https://github.com/user-attachments/assets/530a9c2f-abf6-4db1-8b7c-c7c0114ebb91)
![image](https://github.com/user-attachments/assets/2d80e057-98b0-45df-9090-09cf9e395c35)

#### Route Tables
A route table contains a set of rules, called routes, that determine where network traffic is directed.

**Steps to Create and Associate a Route Table:**

- Open the VPC Dashboard.

- Create a Route Table:
    - Click on "Route Tables" and then "Create route table".
    - Enter a name and select the VPC.
    - Click "Create".
![image](https://github.com/user-attachments/assets/d694663c-1635-4ad0-a146-666a580fc0a5)
![image](https://github.com/user-attachments/assets/01b15598-3bf3-4b26-8ee8-8d3cdc64ddde)
![image](https://github.com/user-attachments/assets/2efa030d-8775-40e3-a133-54d587d0984e)

- Edit Routes:
    - Select the newly created route table.
    - Click on the "Routes" tab and then "Edit routes".
    - Add routes as needed (e.g., destination 0.0.0.0/0 with target as an Internet Gateway for public subnets).
![image](https://github.com/user-attachments/assets/2b673e44-45ad-46a9-ada5-183bacd2df08)
![image](https://github.com/user-attachments/assets/352bc08f-d103-469b-aefe-1413fe25095e)
![image](https://github.com/user-attachments/assets/1bb4ad47-8cc3-4bd9-b600-e0586c9afd67)
![image](https://github.com/user-attachments/assets/898ce769-3feb-4b2e-ad9e-77f67e6e366e)

- Associate with Subnet:
    - Click on the "Subnet associations" tab and then "Edit subnet associations".
    - Select the subnet to associate with the route table.
    - Click "Save".
![image](https://github.com/user-attachments/assets/a6d4bcb8-32d2-4674-bde6-dc9b70e3c7fb)
![image](https://github.com/user-attachments/assets/004cba0b-64e5-4981-8b72-db6213493b06)
![image](https://github.com/user-attachments/assets/86bcdf8a-5dd2-4c2c-8696-30c764720b36)

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
![image](https://github.com/user-attachments/assets/22217496-92c2-41d8-bce2-1ad069ed8bd6)
![image](https://github.com/user-attachments/assets/71c3901d-bfb4-4509-8d86-5e6376f0c582)
![image](https://github.com/user-attachments/assets/3b177995-754b-4890-a561-2c3d91e67d88)

- Attach to VPC:
    - Select the newly created internet gateway.
    - Click "Actions" and then "Attach to VPC".
    - Select your VPC and click "Attach internet gateway".
![image](https://github.com/user-attachments/assets/c3397632-275b-4b18-aa03-61e1fe674a4d)
![image](https://github.com/user-attachments/assets/4c3baa01-b344-4716-b6b0-42e3978e53e7)
![image](https://github.com/user-attachments/assets/941428b7-99dc-48de-bad6-4168b1ba19bb)
![image](https://github.com/user-attachments/assets/ead6a47b-0dff-4130-9270-9c3e08025938)

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
![image](https://github.com/user-attachments/assets/871a31a9-bac3-4349-8bc5-4fe10b731b95)
![image](https://github.com/user-attachments/assets/fde338ac-04cb-4907-91e6-506a278606e8)
![image](https://github.com/user-attachments/assets/4c21c2e9-de9e-4a0b-8cbd-caccde6d9481)
![image](https://github.com/user-attachments/assets/aeec52b2-6bc2-45b1-a58b-51fad3a5e1f3)
![image](https://github.com/user-attachments/assets/46a2a33c-5d74-49a9-ac27-972d35896488)
![image](https://github.com/user-attachments/assets/aea8778a-5c89-4f85-92c6-49ff86535e32)


#### Network ACLs (Access Control Lists)
Network ACLs are an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets.

**Steps to Create a Network ACL:**

- Open the VPC Dashboard.
- Create a Network ACL:
    - Click on "Network ACLs" and then "Create network ACL".
    - Enter a name and select the VPC.
    - Click "Create".
![image](https://github.com/user-attachments/assets/0a6ffa76-f73c-4f74-bcd5-2629a7d3325f)
![image](https://github.com/user-attachments/assets/47ef300b-09b7-4daa-a194-da2396971ac0)
![image](https://github.com/user-attachments/assets/ea8f79f5-0884-4b77-b4b8-943838376854)

- Edit Inbound and Outbound Rules:
    - Select the newly created network ACL.
    - Click on the "Inbound rules" tab and then "Edit inbound rules".
    - Add rules as needed (e.g., allow all traffic on port 80).
    - Click "Save".
    - Repeat for outbound rules.
![image](https://github.com/user-attachments/assets/d083eee0-286d-4c9a-9bee-af1185ec483c)
![image](https://github.com/user-attachments/assets/1f650baa-44e3-43d2-a2a1-be2278af5c4a)
![image](https://github.com/user-attachments/assets/b781c6da-ff1c-4110-a226-e51a5bb5abc7)
![image](https://github.com/user-attachments/assets/794a2712-85c2-41b1-91ac-08a2d5f405a6)
![image](https://github.com/user-attachments/assets/b89ed185-59c4-4d95-9c31-6249dd7b9d8a)

- Associate with Subnets:
    - Click on the "Subnet associations" tab and then "Edit subnet associations".
    - Select the subnet to associate with the network ACL.
    - Click "Save".
![image](https://github.com/user-attachments/assets/814ba45f-6b1b-41da-86d7-3aaa9210dffc)
![image](https://github.com/user-attachments/assets/ba212a2b-e253-4d8f-8633-4e489a7174d4)
![image](https://github.com/user-attachments/assets/f724f012-3efc-430a-a725-ce482a1e1a74)

## Summary
In this lesson, you learned about Amazon VPC, how to create and manage subnets, route tables, and gateways, and how to configure security groups and network ACLs. These components are crucial for setting up a secure and efficient network in AWS.
