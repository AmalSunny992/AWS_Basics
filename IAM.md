# AWS IAM: Identity and Access Management

## Objectives
- Understand the key components of AWS IAM
- Learn how to set up IAM users, groups, roles, and policies
- Implement best practices for managing IAM

## Key Concepts

**Users**

IAM users represent individual people or applications that interact with AWS resources.

**Groups**

IAM groups are collections of users that share common permissions.

**Roles**

IAM roles are sets of permissions that can be assumed by users, services, or applications.

**Policies**

IAM policies are JSON documents that define permissions and specify what actions are allowed or denied.

## Setting Up IAM
1. Create an IAM User

- Open the IAM Dashboard:
    - Go to the AWS Management Console.
    - Select "IAM" from the services menu.
![image](https://github.com/user-attachments/assets/09fe0972-f443-4283-bdcf-7c6ad423ec17)

- Add a New User:
    - Click on "Users" in the left-hand menu and then click "Add user".
      ![image](https://github.com/user-attachments/assets/b643a247-1b92-4763-880c-543f8bb095e7)

    - Enter a username.
      ![image](https://github.com/user-attachments/assets/17c5da8c-0c17-4a5d-aecd-bfb1a8f8620f)

    - Select the type of access for the user:
        - Programmatic access: Provides access to AWS via the AWS CLI, SDKs, or APIs.
        - AWS Management Console access: Provides access to the AWS Management Console.

- Set Permissions:
    - Choose how to set the user's permissions:
    - Attach existing policies directly: Attach predefined policies.
    - Add user to group: Add the user to a group with predefined policies.
    - Copy permissions from existing user: Copy permissions from another user.
    - Attach custom policies: Attach custom policies created for specific needs.
![image](https://github.com/user-attachments/assets/52fc7170-cd08-4f09-9f0e-9fbefab12d6b)
![image](https://github.com/user-attachments/assets/99986faa-8323-4e8f-b336-a955078c0895)

- Review and Create:
    - Review the user details and click "Create user".
    - Download or copy the user credentials (Access Key ID and Secret Access Key) if programmatic access was selected.
![image](https://github.com/user-attachments/assets/91977fc8-5891-4c8b-b205-6ddc999aa837)

2. Create an IAM Group

- Open the IAM Dashboard:
    - Go to the AWS Management Console.
    - Select "IAM" from the services menu.
![image](https://github.com/user-attachments/assets/56c9e3cb-7277-42fc-8e06-801ffc6aa5e2)

- Create a Group:
    - Click on "User groups" in the left-hand menu and then click "Create group".
    - Enter a group name.
    - Attach policies to the group (e.g., AdministratorAccess, ReadOnlyAccess).
![image](https://github.com/user-attachments/assets/ba180229-0592-4fd1-9532-68db7e8d11d0)
![image](https://github.com/user-attachments/assets/8613fab5-d676-492f-aba4-a4fd1643e05a)
![image](https://github.com/user-attachments/assets/0f3232cf-0eb5-41bf-a5c2-b9b6a4280118)
![image](https://github.com/user-attachments/assets/38bf03bb-b406-4583-86bc-711ef892d833)

- Add Users to the Group:
    - Select users to add to the group.
    - Review and create the group.
![image](https://github.com/user-attachments/assets/a208acb7-c138-4f35-862b-a13d1ca50ef3)
![image](https://github.com/user-attachments/assets/038fbef2-8dfc-445d-8c30-f7c79209ec23)
![image](https://github.com/user-attachments/assets/891a2ba8-1109-4a48-8fe0-26a0b7970df5)

3. Create an IAM Role

- Open the IAM Dashboard:
    - Go to the AWS Management Console.
    - Select "IAM" from the services menu.

- Create a Role:
    - Click on "Roles" in the left-hand menu and then click "Create role".
![image](https://github.com/user-attachments/assets/ad9bec72-0d0c-4caa-9668-7e2a85013ec4)

    - Select the type of trusted entity:
        - AWS service: Select a service that will assume the role (e.g., EC2).
        - Another AWS account: Allow cross-account access.
        - Web identity: Allow external web identities (e.g., Facebook, Google).
        - SAML 2.0 federation: Allow SAML 2.0-based federation.
![image](https://github.com/user-attachments/assets/d29fc322-e117-49d1-accb-05d426f9260f)

- Attach Policies:
    - Attach policies that define the permissions for the role (e.g., AmazonS3FullAccess).
![image](https://github.com/user-attachments/assets/9e4cb1b1-e711-46a5-bf74-7421f740fa7f)
![image](https://github.com/user-attachments/assets/ace6047d-69e2-464b-867b-59edc621c0b1)

- Define Role Name:
    - Enter a name for the role and click "Create role".
![image](https://github.com/user-attachments/assets/b149aef3-40f0-4ece-8768-1758285ca33c)
![image](https://github.com/user-attachments/assets/fba70624-ce55-40cc-ba67-079de647fc25)

4. Attach Policies to Users, Groups, or Roles

- Open the IAM Dashboard:
    - Go to the AWS Management Console.
    - Select "IAM" from the services menu.

- Navigate to the Entity:
    - Go to "Users", "User groups", or "Roles" based on where you want to attach the policy.
![image](https://github.com/user-attachments/assets/97392b6a-a5b2-401d-9e42-f3918835f044)

- Attach Policy:
    - Select the user, group, or role.
    - Click on the "Permissions" tab and then click "Add permissions".
    - Attach existing policies or create a custom policy.
![image](https://github.com/user-attachments/assets/4827f3a7-8545-44fb-b3a4-2c09691ede2f)
![image](https://github.com/user-attachments/assets/916c36b0-c152-4782-8496-cf1ef6b8e4b3)
![image](https://github.com/user-attachments/assets/afa890ef-d930-4805-8e6a-5d066e480828)
![image](https://github.com/user-attachments/assets/0a0db56c-e097-4785-b663-b62886e114aa)

## Best Practices for IAM

1. Enable Multi-Factor Authentication (MFA):
    - Enhance account security by enabling MFA for all IAM users.

2. Use Groups to Assign Permissions:
    - Assign permissions to groups rather than individual users to simplify management.

3. Follow the Principle of Least Privilege:
    - Grant only the permissions required for users to perform their tasks.

4. Rotate Access Keys Regularly:
    - Regularly rotate access keys and avoid embedding them in code.

5. Use IAM Roles for Applications:
    - Use IAM roles for applications running on AWS services (e.g., EC2) to securely access other services.

## Summary
In this guide, you learned how to set up IAM users, groups, roles, and policies in AWS. Following best practices ensures secure and efficient management of AWS resources.
