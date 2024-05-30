# Difference b/w 4 types of EC2 instances : On demand/Spot/Standard reserved/Convertible reserved Instances

AWS offers different types of EC2 instances to provide flexibility in cost and usage. Here's a detailed comparison of the four primary instance types: On-Demand, Spot, Standard Reserved, and Convertible Reserved Instances.

## On-Demand Instances

### Description:

On-Demand Instances allow you to pay for compute capacity by the hour or second (depending on the instance type), with no long-term commitments.

### Key Features:

Flexibility: Suitable for applications with unpredictable workloads that cannot be interrupted.

No Upfront Payment: Pay only for what you use.

Scalability: Quickly scale up or down based on current needs.

### Use Cases:
Short-term, spiky, or unpredictable workloads.

Development and testing applications.

Applications that need high availability and cannot be interrupted.

### Examples:

Development and Testing: Easily start and stop instances as needed without long-term commitments.

Short-Term Applications: Projects or applications that run for a short duration or have uncertain timelines.

## Spot Instances

### Description:

Spot Instances let you bid for unused EC2 capacity at potentially lower prices than On-Demand Instances.

### Key Features:

Cost Savings: Up to 90% cheaper than On-Demand Instances.

Variable Pricing: Prices vary based on supply and demand.

Interruption: Instances can be terminated by AWS with a two-minute warning if the Spot price exceeds your bid or capacity is no longer available.

### Use Cases:

Batch processing jobs.

Data analysis.

Workloads that can tolerate interruptions.

CI/CD workloads.

### Examples:

Big Data Processing: Large-scale data processing tasks like Hadoop and Spark.

Batch Jobs: Jobs that can be interrupted and resumed, such as media transcoding or scientific computations.

## Standard Reserved Instances

### Description:
Standard Reserved Instances provide a significant discount (up to 75%) compared to On-Demand pricing in exchange for a one-year or three-year commitment.

### Key Features:
Cost Savings: Predictable savings on EC2 costs.

Commitment: Requires a one-year or three-year commitment.

Less Flexibility: Cannot change the instance family, OS, or tenancy.

### Use Cases:
Steady-state usage applications.

Applications with predictable usage patterns.

Enterprise applications.

### Examples:
Enterprise Applications: Long-running applications like databases or internal business applications.

Production Workloads: Applications with consistent and predictable usage patterns.

## Convertible Reserved Instances

### Description:
Convertible Reserved Instances offer up to 54% savings over On-Demand pricing and provide the flexibility to change the instance attributes during the term.

### Key Features:
Flexibility: Allows changing instance family, operating system, and tenancy during the commitment term.

Cost Savings: Significant discounts over On-Demand Instances.

Commitment: Requires a one-year or three-year commitment.

### Use Cases:
Applications with predictable usage but uncertain future requirements.

Environments that may need to evolve in terms of instance types.

### Examples:
Evolving Workloads: Applications where future requirements might involve changes in instance types.

Long-Term Projects: Projects with long-term commitments but where specific instance types might not be fixed.

## Summary of Differences
![image](https://github.com/AmalSunny992/AWS/assets/169422802/d350a466-80e8-475b-8299-c74b3d8e3f33)

## Key Points to Consider

On-Demand Instances are best for flexibility and workloads that cannot tolerate interruptions.

Spot Instances offer the lowest cost but are suitable only for fault-tolerant and flexible applications.

Standard Reserved Instances provide the highest cost savings for predictable and steady-state workloads but with less flexibility.

Convertible Reserved Instances strike a balance between cost savings and flexibility, allowing for changes in instance attributes over time.

