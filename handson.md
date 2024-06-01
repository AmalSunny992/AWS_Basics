# Hands-On Project: Deploying a Web Application Using CI/CD Pipeline on AWS

This project will cover a range of skills essential for a DevOps engineer, including AWS services, CI/CD pipelines, infrastructure as code (IaC), containerization, and monitoring. 
You'll deploy a simple web application using Docker, set up a CI/CD pipeline using Jenkins, and manage the infrastructure with Terraform.

## Project Overview:

Web Application: A simple Node.js or Python web application.

Containerization: Dockerize the application.

Infrastructure as Code: Use Terraform to provision AWS resources.

CI/CD Pipeline: Set up a Jenkins pipeline to automate the build, test, and deployment process.

Monitoring and Logging: Use AWS CloudWatch for monitoring and logging.

## Step-by-Step Guide
### 1. Set Up the Web Application
Create a Simple Web Application: Write a basic web application in Node.js or Python.

Node.js Example:

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(port, () => {
  console.log(`App listening at http://localhost:${port}`);
});
```

Python Flask Example:

``` python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello World!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

### 2. Containerize the Application

Create a Dockerfile: Write a Dockerfile to containerize the application.

Node.js Dockerfile:

```Dockerfile
FROM node:14
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "app.js"]
```

Python Dockerfile:

```Dockerfile
FROM python:3.8
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

### 3. Set Up Infrastructure with Terraform

Install Terraform: Ensure Terraform is installed on your local machine.

Create Terraform Configuration: Write Terraform scripts to provision the necessary AWS resources (e.g., ECS cluster, VPC, security groups, IAM roles).

Example main.tf:
```hcl
provider "aws" {
  region = "us-west-2"
}

resource "aws_vpc" "main" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "subnet" {
  vpc_id     = aws_vpc.main.id
  cidr_block = "10.0.1.0/24"
}

resource "aws_security_group" "sg" {
  vpc_id = aws_vpc.main.id
  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

resource "aws_ecs_cluster" "main" {
  name = "main-cluster"
}
```

### 4. Set Up Jenkins for CI/CD

Install Jenkins: Install Jenkins on a local machine or an AWS EC2 instance.

Install Plugins: Ensure necessary plugins are installed (e.g., AWS, Docker, Git).

Create a Pipeline Job: Set up a Jenkins pipeline job to automate the build, test, and deployment process.

Example Jenkinsfile:
```groovy

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('myapp:latest')
                }
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                // Add test commands here
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def awsEcs = docker.image('amazon/amazon-ecs-cli')
                    awsEcs.inside {
                        sh 'ecs-cli configure --cluster myCluster --region us-west-2 --default-launch-type EC2'
                        sh 'ecs-cli compose --file docker-compose.yml service up'
                    }
                }
            }
        }
    }
}
```

## 5. Monitoring and Logging with AWS CloudWatch
Set Up CloudWatch: Use AWS CloudWatch to monitor your application and set up log groups.
Create Alarms and Dashboards: Create alarms for critical metrics (e.g., CPU usage, memory usage) and dashboards for visualizing application performance.

## 6. Deploy and Test the Application
Deploy the Application: Use the Jenkins pipeline to deploy the application to AWS.
Test the Deployment: Access the deployed application via its public URL and verify it's working correctly.
Check Logs and Metrics: Use CloudWatch to monitor logs and metrics, ensuring everything is functioning as expected.

## Resources and Tools
AWS Free Tier: Utilize AWS Free Tier to practice without incurring costs.
Docker Documentation: Learn about Docker and its commands.
Terraform Documentation: Explore Terraform configurations and best practices.
Jenkins Documentation: Understand Jenkins pipeline syntax and plugin usage.
AWS CloudWatch: Familiarize yourself with monitoring and logging in AWS.
