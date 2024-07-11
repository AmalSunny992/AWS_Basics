# S3 and CloudFront

## Objectives
- Understand Amazon S3 and its key features
- Learn how to create and manage S3 buckets
- Set up a CloudFront distribution to serve content from S3

## Concepts

### Introduction to S3
Amazon S3 (Simple Storage Service) is a scalable object storage service that provides industry-leading durability, availability, performance, security, and virtually unlimited storage capacity. S3 is ideal for storing and retrieving any amount of data at any time from anywhere on the web.

#### Key Features:
**Durability:** 99.999999999% (11 9's) durability for objects.

**Scalability:** Handles storage of virtually unlimited data.

**Security:** Supports data encryption and access controls.

**Performance:** High-speed data retrieval.

**Accessibility:** Accessible via HTTP/HTTPS protocols.

#### Creating and Managing S3 Buckets
An S3 bucket is a container for storing objects in S3.

**Steps to Create an S3 Bucket:**
- Open the S3 Dashboard:
    - Go to the AWS Management Console.
    - Select "S3" from the services menu.

- Create a Bucket:
    - Click on the "Create bucket" button.
    - Enter a unique bucket name and choose the AWS region.
    - Configure options such as versioning, encryption, and access permissions.
    - Click "Create bucket".

- Managing S3 Buckets:
    - Uploading Objects: Use the S3 console, AWS CLI, or SDKs to upload files.
    - Setting Permissions: Configure bucket policies, ACLs (Access Control Lists), and IAM policies to manage access.
    - Versioning: Enable versioning to keep multiple versions of objects.
    - Lifecycle Policies: Define rules to transition objects to different storage classes or delete them after a specified time.
    - Encryption: Use server-side encryption (SSE) to encrypt data at rest.

### CloudFront Distribution
Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds.

**Steps to Set Up CloudFront Distribution:**
- Open the CloudFront Dashboard:
    - Go to the AWS Management Console.
    - Select "CloudFront" from the services menu.

- Create a Distribution:
    - Click on the "Create Distribution" button.
    - Choose "Web" as the delivery method.

    - Specify the origin settings:
        - Origin Domain Name: Select the S3 bucket you created.
        - Origin Path: Optionally specify a directory path in the bucket.
        - Origin ID: Automatically generated or you can specify a custom ID.

    - Configure default cache behavior settings:
        - Viewer Protocol Policy: Choose between HTTP, HTTPS, or redirect HTTP to HTTPS.
        - Allowed HTTP Methods: Select the HTTP methods allowed (e.g., GET, HEAD).

    - Configure distribution settings:
        - Price Class: Select the regions where you want CloudFront to distribute your content.
        - Alternate Domain Names (CNAMEs): Optionally add custom domain names.
        - SSL Certificate: Choose default CloudFront certificate or add a custom SSL certificate.

    - Click "Create Distribution".

- Accessing Content via CloudFront:
    - Once the distribution is created, note the CloudFront domain name (e.g., d1234567890.cloudfront.net).
    - Use this domain name to access content stored in your S3 bucket.

## Summary
In this lesson, you learned about Amazon S3, how to create and manage S3 buckets, and how to set up a CloudFront distribution to serve content from S3. These services are essential for scalable, durable, and fast content delivery.