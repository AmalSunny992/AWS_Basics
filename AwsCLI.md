# AWS CLI 
## Essential Commands
Configures your AWS CLI with your AWS access key, secret key, default region, and output format. 

```aws configure```

Displays information about available AWS CLI commands and their usage. 

```aws help```

## Identity and Access Management (IAM) Commands:
Creates a new IAM user. 

```aws iam create-user```

Creates a new IAM group. 

```aws iam create-group```

Creates a new IAM role. 

```aws iam create-role```

Attaches an IAM policy to a user. 

```aws iam attach-user-policy```

Attaches an IAM policy to a group. 

```aws iam attach-group-policy'''

Attaches an IAM policy to a role. aws iam attach-role-policy

Lists all IAM users in your account. aws iam list-users

List all IAM groups in your account aws iam list-groups

Lists all IAM roles in your account. aws iam list-roles

EC2 (Elastic Compute Cloud) Commands:
Lists all EC2 instances in your account. aws ec2 describe-instances

Launches a new EC2 instance. aws ec2 run-instances

Starts an existing EC2 instance. aws ec2 start-instances

Stops a running EC2 instance. aws ec2 stop-instances

Terminates an EC2 instance. aws ec2 terminate-instances

S3 (Simple Storage Service) Commands:
Lists all S3 buckets in your account. aws s3 ls

Creates a new S3 bucket. aws s3 mb

Copies files or directories to/from S3. aws s3 cp

Synchronizes files and directories to S3. aws s3 sync

Deletes files or objects from S3. aws s3 rm

CloudFormation Commands:
Creates a new CloudFormation stack. aws cloudformation create-stack

Updates an existing CloudFormation stack. aws cloudformation update-stack

Deletes a CloudFormation stack. aws cloudformation delete-stack

Lambda Commands:
Lists all Lambda functions in your account. aws lambda list-functions

Creates a new Lambda function. aws lambda create-function

Invokes a Lambda function. aws lambda invoke

These commands are just the basics and cover a wide range of AWS services. For specific command options and syntax, you can always refer to the official AWS CLI documentation or use the aws help command followed by the service name, e.g., aws ec2 help.

Kubernetes Contexts
Managing Kubernetes contexts is vital for multiple cluster management:

Get available contexts:

kubectl config get-contexts

Switch context:

kubectl config use-context <context-name>

Updating Cluster Configuration
Update Kubernetes configuration to connect to an AWS EKS cluster:

Update cluster configuration:

aws eks update-kubeconfig --region <region-name> --name <cluster-name>

Switch to the updated context:

kubectl config use-context arn:aws:eks:<region-name>:<arn-id>:cluster/<cluster-name>


