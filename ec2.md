# Amazon EC2 Instance

## What is an Amazon EC2 Instance?
Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable compute capacity in the cloud. It allows users to launch and manage virtual servers, known as instances, on AWS infrastructure. EC2 instances provide secure, resizable compute capacity, designed to make web-scale cloud computing easier for developers.

## Uses of Amazon EC2 Instances

### Web Hosting:
Host dynamic websites and web applications.
Scale web server resources up or down based on traffic.

### Big Data Analytics:
Process large data sets using Hadoop, Spark, or other big data frameworks.
Perform data warehousing with Amazon Redshift.

### Machine Learning and AI:
Train machine learning models using frameworks like TensorFlow or PyTorch.
Deploy AI inference models in production environments.

### High-Performance Computing (HPC):
Run complex simulations and calculations for scientific research.
Perform large-scale computations for engineering and financial services.

### Development and Testing:
Create isolated environments for software development and testing.
Use pre-configured development environments with tools and dependencies.

### Gaming:
Host game servers to provide a seamless gaming experience to players.
Scale resources to meet peak demand during gaming events.

### Backup and Disaster Recovery:
Implement backup solutions for critical data and applications.
Create disaster recovery plans to ensure business continuity.


## Cost of Amazon EC2 Instances
The cost of EC2 instances depends on several factors:

### Instance Type:
Different instance types (e.g., t2.micro, m5.large, p3.2xlarge) have different pricing.

### Pricing Model:
On-Demand Instances: Pay per hour or second with no long-term commitments.

Spot Instances: Bid for unused capacity, often at a significantly lower cost.

Reserved Instances: One-year or three-year commitments with up to 75% savings.

Savings Plans: Flexible pricing model offering significant savings on AWS usage.

### Region: 
Costs vary based on the AWS region where the instance is launched.

### Storage:
Costs for attached storage volumes (e.g., Elastic Block Store - EBS).

### Data Transfer: 
Costs for data transfer out to the internet or between AWS regions.

## Examples of Amazon EC2 Instances

### General Purpose Instances:

**t3.micro**: Suitable for low-traffic web applications and development environments.

**m5.large**: Balanced CPU, memory, and networking for web servers and small databases.

### Compute Optimized Instances:

**c5.xlarge**: Ideal for compute-intensive tasks such as batch processing, machine learning inference, and high-performance web servers.
Memory Optimized Instances:

**r5.large**: Designed for memory-intensive applications such as in-memory databases, big data analytics, and real-time processing of large datasets.
Storage Optimized Instances:

**i3.large**: Optimized for applications requiring high, sequential read and write access to large data sets on local storage.
Accelerated Computing Instances:

**p3.2xlarge**: Equipped with GPUs, ideal for machine learning training, HPC, and graphics rendering.

## Example Scenario

### E-commerce Website Hosting:
**Instance Type**: m5.large

**Region**: US East (N. Virginia)

**Pricing Model**: On-Demand

**Usage**:

Front-end servers to handle web traffic.

Backend servers for database management and transaction processing.

**Cost Consideration**:

Hourly rate for m5.large instance.

Storage costs for EBS volumes.

Data transfer costs for serving content to users.

## Cost Example Calculation

Assuming the use of an m5.large instance for an e-commerce website:

Instance Cost (On-Demand, US East - N. Virginia): $0.096 per hour.

Monthly Cost: $0.096/hour * 24 hours/day * 30 days/month = $69.12/month.

This calculation only covers the instance cost. Additional costs for storage, data transfer, and other AWS services used by the application will also apply.


## Creating an Amazon EC2 instance and connecting to it through SSH using PuTTY involves several steps. Below is a step-by-step guide.

### Step 1: Sign in to the AWS Management Console
Go to the AWS Management Console.

Sign in with your AWS account credentials.

### Step 2: Launch an EC2 Instance

#### Navigate to the EC2 Dashboard:

In the AWS Management Console, select "Services" from the top menu, then select "EC2" under the "Compute" category.

#### Launch an Instance:
Click the "Launch Instance" button.

#### Choose an Amazon Machine Image (AMI):
Select an appropriate AMI. For example, choose "Amazon Linux 2 AMI" for a standard Linux distribution.

#### Choose an Instance Type:
Select an instance type based on your requirements (e.g., t2.micro for free tier eligible).

#### Configure Instance Details:
Leave the default settings or configure the instance details as needed.

Click "Next: Add Storage."

#### Add Storage:

Configure the storage settings as required. The default settings are usually sufficient for a basic setup.

Click "Next: Add Tags."

#### Add Tags:

(Optional) Add any tags to help manage your instances.

#### Click "Next: Configure Security Group."
Configure Security Group:

Create a new security group or select an existing one.

#### Add a rule to allow SSH access:

Type: SSH

Protocol: TCP

Port Range: 22

Source: Custom (or My IP to restrict access to your IP address)

#### Review and Launch:

Review your instance configuration.

Click "Launch."

#### Select a Key Pair:

Create a new key pair or select an existing one.

Download the key pair file (.ppk) and store it securely. You will need this file to connect to your instance.

Click "Launch Instances."

#### View Instances:

Click "View Instances" to see your running instances.


### Step 3: Connect to Your EC2 Instance Using PuTTY

#### Download and Install PuTTY:

Download PuTTY and install it.

#### Get Your Instance’s Public DNS:

In the EC2 Dashboard, select "Instances" and choose your running instance.

Note the Public DNS (e.g., ec2-198-51-100-1.compute-1.amazonaws.com).

#### Configure PuTTY:

Open PuTTY.

In the "Host Name" field, enter ec2-user@<Public DNS> (e.g., ec2-user@ec2-198-51-100-1.compute-1.amazonaws.com).

#### Add the Key Pair:

In the PuTTY configuration window, navigate to "SSH" > "Auth."

Click "Browse" and select your .ppk file.

#### Connect to the Instance:

Click "Open" to start the SSH session.

If prompted, accept the security alert to trust the server's host key.

## Summary

Sign in to AWS Management Console.

Launch an EC2 instance.

Configure security group to allow SSH access.

Download the key pair file (.pem).

Convert the key pair file to .ppk using PuTTYgen.

Use PuTTY to connect to the instance via SSH.

By following these steps, you can create an EC2 instance and connect to it securely using SSH with PuTTY.




