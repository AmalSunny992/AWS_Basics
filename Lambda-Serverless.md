# AWS Lambda and Serverless Computing

## Objectives
- Understand AWS Lambda and its key features
- Learn how to create and deploy Lambda functions

## Concepts

### Introduction to AWS Lambda
AWS Lambda is a serverless computing service that lets you run code without provisioning or managing servers. You only pay for the compute time you consume.

**Key Features:**

**Serverless:** No servers to manage.

**Automatic Scaling:** Scales automatically from a few requests per day to thousands per second.

**Pay-per-use:** Charges only for the compute time you consume.

**Supports Multiple Languages:** Including Node.js, Python, Ruby, Java, Go, and .NET.


### Creating and Deploying Lambda Functions

**Steps to Create a Lambda Function:**

- Open the Lambda Dashboard:
    - Go to the AWS Management Console.
    - Select "Lambda" from the services menu.
![image](https://github.com/user-attachments/assets/426eaf16-13f8-465a-af4d-f8c43fb7fe8e)

- Create a Function:
    - Click on "Create function".
![image](https://github.com/user-attachments/assets/95be14a6-4b02-4ec0-98e2-e50fd51e53dd)

- Choose an authoring method:
    - Author from scratch: Create a new function from scratch.
    - Use a blueprint: Use a pre-configured blueprint for common use cases.
    - Browse serverless app repository: Deploy a pre-built application from the AWS Serverless Application Repository.
![image](https://github.com/user-attachments/assets/54b4de51-2b71-4f82-9c34-10c4ccabef97)

- Configure Function Settings:
    - Function name: Enter a name for your function.
    - Runtime: Choose the runtime (e.g., Node.js, Python).
    - Role: Choose an execution role:
        - Create a new role with basic Lambda permissions.
        - Use an existing role: If you already have an IAM role with the necessary permissions.
![image](https://github.com/user-attachments/assets/33e9fc47-68af-4179-bfaf-cdd8e5798e5b)

- Write the Code:
    - Use the inline code editor or upload a .zip file with your code.
    - Example: A simple Python function to return "Hello, World!"

```python
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': 'Hello, World!'
    }
```
![image](https://github.com/user-attachments/assets/1c74906d-65a3-4cb2-a0af-cf3a655fa745)

- Configure Function:
    - Set environment variables, configure memory and timeout settings, and add any required layers.
![image](https://github.com/user-attachments/assets/28030367-7d89-4155-93d0-1cfa4e32e50d)

- Deploy the Function:
    - Click "Deploy" to save the function.

- Testing the Lambda Function:
    - Create a Test Event:
        - In the Lambda console, click on "Test".
        - Configure a test event with a sample payload.
        - Save the test event with a name.
    - Run the Test:
        - Click on "Test" to execute the function with the test event.
        - Check the execution results, including logs and response.
![image](https://github.com/user-attachments/assets/ac63331d-1279-4abb-a2f1-78014a53bfb9)

- Setting up Triggers:
    - Add a Trigger:
        - In the Lambda console, click on the "Add trigger" button.
        - Select a trigger type (e.g., API Gateway, S3, DynamoDB, CloudWatch Events).
        - Configure the trigger settings.
    - Deploy and Test:
        - Once the trigger is configured, deploy the changes.
        - Test the trigger to ensure it invokes the Lambda function correctly.

**Example: Creating a Lambda Function with S3 Trigger**

Scenario:
Automatically generate a thumbnail for images uploaded to an S3 bucket.

- Create an S3 Bucket:
    - Go to the S3 console and create a new bucket (e.g., my-image-uploads).

- Create the Lambda Function:
    - Follow the steps above to create a new Lambda function (e.g., GenerateThumbnail).
    - Use the following Python code for the Lambda function:

```python

import boto3
from PIL import Image
import io

s3 = boto3.client('s3')

def lambda_handler(event, context):
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']

    # Get the image from S3
    response = s3.get_object(Bucket=bucket, Key=key)
    image_content = response['Body'].read()

    # Generate thumbnail
    image = Image.open(io.BytesIO(image_content))
    image.thumbnail((128, 128))
    
    # Save thumbnail to a BytesIO object
    thumb_io = io.BytesIO()
    image.save(thumb_io, format='JPEG')

    # Upload thumbnail to S3
    thumb_key = f'thumbnails/{key}'
    s3.put_object(Bucket=bucket, Key=thumb_key, Body=thumb_io.getvalue())

    return {
        'statusCode': 200,
        'body': f'Thumbnail created at {thumb_key}'
    }
```

- Add S3 Trigger:
    - In the Lambda console, go to the "Add trigger" section.
    - Select "S3" as the trigger type.
    - Configure the S3 bucket and event type (e.g., ObjectCreated).
    - Save the trigger.

- Test the Function:
    - Upload an image to the S3 bucket.
    - Check the thumbnails folder in the S3 bucket for the generated thumbnail


## Summary
In this lesson, you learned about AWS Lambda, how to create and deploy Lambda functions, and how to set up triggers to automate serverless workflows. AWS Lambda allows you to run code without provisioning or managing servers, making it an essential service for serverless computing.
