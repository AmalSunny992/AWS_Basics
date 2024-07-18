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
![image](https://github.com/user-attachments/assets/ac0eb1eb-75cb-4607-9972-0a28aa78c1f5)

- Create a Bucket:
    - Click on the "Create bucket" button.
    - Enter a unique bucket name and choose the AWS region.
    - Configure options such as versioning, encryption, and access permissions.
    - Click "Create bucket".
![image](https://github.com/user-attachments/assets/ccf71c4f-fb87-4aaa-9440-928183eb55c6)
![image](https://github.com/user-attachments/assets/bd2a94ea-fd0a-41fc-ac05-64cbc1697f7a)
![image](https://github.com/user-attachments/assets/38341bb0-e51f-4ec9-9ce5-a0cc0c0a40ac)
![image](https://github.com/user-attachments/assets/fc8ae6fb-9358-4433-b236-a32033a2c090)
![image](https://github.com/user-attachments/assets/44278996-4ef2-4c66-8bf7-22c1f8cf6bac)

- Managing S3 Buckets:
    - Uploading Objects: Use the S3 console, AWS CLI, or SDKs to upload files.
    - Setting Permissions: Configure bucket policies, ACLs (Access Control Lists), and IAM policies to manage access.
    - Versioning: Enable versioning to keep multiple versions of objects.
    - Lifecycle Policies: Define rules to transition objects to different storage classes or delete them after a specified time.
    - Encryption: Use server-side encryption (SSE) to encrypt data at rest.
![image](https://github.com/user-attachments/assets/6153f640-cae6-4c92-b9ce-3612c449081a)
![image](https://github.com/user-attachments/assets/17864d9d-c3fe-4f13-ba1a-5d7f3efd265b)
![image](https://github.com/user-attachments/assets/0db2348d-8ac2-4395-8b5d-1f496c626bbb)
![image](https://github.com/user-attachments/assets/424594f6-c67b-4178-91bd-3659280a977b)

### CloudFront Distribution
Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds.

**Steps to Set Up CloudFront Distribution:**
- Open the CloudFront Dashboard:
    - Go to the AWS Management Console.
    - Select "CloudFront" from the services menu.
![image](https://github.com/user-attachments/assets/4d9d5066-f1ba-4c02-bd1a-1f970a398737)

- Create a Distribution:
    - Click on the "Create Distribution" button.
    - Choose "Web" as the delivery method.

    - Specify the origin settings:
        - Origin Domain Name: Select the S3 bucket you created.
        - Origin Path: Optionally specify a directory path in the bucket.
        - Origin ID: Automatically generated or you can specify a custom ID.
![image](https://github.com/user-attachments/assets/4c7b1206-b508-4e42-9021-6e17f34e36a5)

    - Configure default cache behavior settings:
        - Viewer Protocol Policy: Choose between HTTP, HTTPS, or redirect HTTP to HTTPS.
        - Allowed HTTP Methods: Select the HTTP methods allowed (e.g., GET, HEAD).
![image](https://github.com/user-attachments/assets/8a78d636-18fd-4f2c-85e9-8e3cef5b963b)
![image](https://github.com/user-attachments/assets/60f0cf76-40a1-4003-9a9d-145696053651)
![image](https://github.com/user-attachments/assets/fdf54e10-8925-43d1-9ab2-2f2677c64559)

    - Configure distribution settings:
        - Price Class: Select the regions where you want CloudFront to distribute your content.
        - Alternate Domain Names (CNAMEs): Optionally add custom domain names.
        - SSL Certificate: Choose default CloudFront certificate or add a custom SSL certificate.
![image](https://github.com/user-attachments/assets/6aba32ab-6688-4eed-90ab-085eb2980b72)
![image](https://github.com/user-attachments/assets/0d1d6fa1-5d91-4a08-a81f-1d7818fcf9cb)

    - Click "Create Distribution".
![image](https://github.com/user-attachments/assets/3050897c-2fb0-4c07-a718-4d10492f1f17)
![image](https://github.com/user-attachments/assets/605984e5-1713-4c7c-b34c-94a53129d9ae)
![image](https://github.com/user-attachments/assets/f4d502a8-df0e-4403-94f0-e87a1262e82e)

- Accessing Content via CloudFront:
    - Once the distribution is created, note the CloudFront domain name (e.g., d1234567890.cloudfront.net).
    - Use this domain name to access content stored in your S3 bucket.

## Summary
In this lesson, you learned about Amazon S3, how to create and manage S3 buckets, and how to set up a CloudFront distribution to serve content from S3. These services are essential for scalable, durable, and fast content delivery.
