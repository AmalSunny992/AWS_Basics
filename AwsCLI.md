# Learning AWS CLI Commands

This document provides an overview of common AWS CLI commands with examples to help you get started with managing AWS resources from the command line.

## Table of Contents

- [Introduction](#introduction)
- [AWS CLI Configuration](#aws-cli-configuration)
- [Common AWS CLI Commands](#common-aws-cli-commands)
  - [IAM](#iam)
    - [Create User](#create-user)
    - [List Users](#list-users)
  - [S3](#s3)
    - [Create Bucket](#create-bucket)
    - [List Buckets](#list-buckets)
    - [Upload File](#upload-file)
    - [Download File](#download-file)
  - [EC2](#ec2)
    - [Launch Instance](#launch-instance)
    - [List Instances](#list-instances)
    - [Stop Instance](#stop-instance)
    - [Terminate Instance](#terminate-instance)
  - [RDS](#rds)
    - [Create DB Instance](#create-db-instance)
    - [List DB Instances](#list-db-instances)
- [Useful Resources](#useful-resources)

## Introduction

The AWS Command Line Interface (CLI) is a unified tool to manage AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

## AWS CLI Configuration

Before using AWS CLI commands, you need to configure your AWS CLI with your credentials.

```bash
aws configure
```

You will be prompted to enter your AWS Access Key ID, Secret Access Key, default region, and default output format.

## Common AWS CLI Commands
### IAM
#### Create User

Create a new IAM user.

```bash
aws iam create-user --user-name USERNAME
```

Example:
bash
```
aws iam create-user --user-name devops-user
```
#### List Users
List all IAM users.

bash
```
aws iam list-users
```

Example:

```bash
aws iam list-users
```
### S3
#### Create Bucket
Create a new S3 bucket.

```bash
aws s3 mb s3://BUCKET_NAME
```
Example:

```bash
aws s3 mb s3://my-unique-bucket-name
```
#### List Buckets
List all S3 buckets.

```bash
aws s3 ls
```
Example:

```bash
aws s3 ls
```
#### Upload File
Upload a file to an S3 bucket.

```bash
aws s3 cp FILE_PATH s3://BUCKET_NAME
```
Example:

```bash
aws s3 cp myfile.txt s3://my-unique-bucket-name
```
#### Download File
Download a file from an S3 bucket.

```bash
aws s3 cp s3://BUCKET_NAME/FILE_PATH LOCAL_PATH
```
Example:

```bash
aws s3 cp s3://my-unique-bucket-name/myfile.txt ./myfile.txt
```
### EC2
#### Launch Instance
Launch a new EC2 instance.

```bash
aws ec2 run-instances --image-id IMAGE_ID --count 1 --instance-type INSTANCE_TYPE --key-name KEY_NAME --security-group-ids SECURITY_GROUP_ID --subnet-id SUBNET_ID
```
Example:

```bash
aws ec2 run-instances --image-id ami-0abcdef1234567890 --count 1 --instance-type t2.micro --key-name my-key-pair --security-group-ids sg-0123456789abcdef0 --subnet-id subnet-0123456789abcdef0
```
#### List Instances
List all EC2 instances.

```bash
aws ec2 describe-instances
```
Example:

```bash
aws ec2 describe-instances
```
#### Stop Instance
Stop a running EC2 instance.

```bash
aws ec2 stop-instances --instance-ids INSTANCE_ID
```
Example:
```bash
aws ec2 stop-instances --instance-ids i-0123456789abcdef0
```

#### Terminate Instance
Terminate an EC2 instance.

```bash
aws ec2 terminate-instances --instance-ids INSTANCE_ID
```
Example:
```bash
aws ec2 terminate-instances --instance-ids i-0123456789abcdef0
```
### RDS
#### Create DB Instance
Create a new RDS DB instance.

```bash
aws rds create-db-instance --db-instance-identifier DB_INSTANCE_IDENTIFIER --db-instance-class DB_INSTANCE_CLASS --engine ENGINE --master-username MASTER_USERNAME --master-user-password MASTER_USER_PASSWORD --allocated-storage ALLOCATED_STORAGE
```
Example:

```bash
aws rds create-db-instance --db-instance-identifier mydbinstance --db-instance-class db.t2.micro --engine mysql --master-username admin --master-user-password password123 --allocated-storage 20
```

#### List DB Instances
List all RDS DB instances.

```bash
aws rds describe-db-instances
```
Example:

```bash
aws rds describe-db-instances
```

## Useful Resources
- AWS CLI Documentation
- AWS CLI Command Reference

