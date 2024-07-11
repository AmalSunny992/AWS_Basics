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

- Add a New User:
    - Click on "Users" in the left-hand menu and then click "Add user".
    - Enter a username.
    - Select the type of access for the user:
        - Programmatic access: Provides access to AWS via the AWS CLI, SDKs, or APIs.
        - AWS Management Console access: Provides access to the AWS Management Console.

- Set Permissions:
    - Choose how to set the user's permissions:
    - Attach existing policies directly: Attach predefined policies.
    - Add user to group: Add the user to a group with predefined policies.
    - Copy permissions from existing user: Copy permissions from another user.
    - Attach custom policies: Attach custom policies created for specific needs.

- Review and Create:
    - Review the user details and click "Create user".
    - Download or copy the user credentials (Access Key ID and Secret Access Key) if programmatic access was selected.

2. Create an IAM Group

- Open the IAM Dashboard:
    - Go to the AWS Management Console.
    - Select "IAM" from the services menu.

- Create a Group:
    - Click on "User groups" in the left-hand menu and then click "Create group".
    - Enter a group name.
    - Attach policies to the group (e.g., AdministratorAccess, ReadOnlyAccess).

- Add Users to the Group:
    - Select users to add to the group.
    - Review and create the group.

3. Create an IAM Role

- Open the IAM Dashboard:
    - Go to the AWS Management Console.
    - Select "IAM" from the services menu.

- Create a Role:
    - Click on "Roles" in the left-hand menu and then click "Create role".
    - Select the type of trusted entity:
        - AWS service: Select a service that will assume the role (e.g., EC2).
        - Another AWS account: Allow cross-account access.
        - Web identity: Allow external web identities (e.g., Facebook, Google).
        - SAML 2.0 federation: Allow SAML 2.0-based federation.

- Attach Policies:
    - Attach policies that define the permissions for the role (e.g., AmazonS3FullAccess).

- Define Role Name:
    - Enter a name for the role and click "Create role".

4. Attach Policies to Users, Groups, or Roles

- Open the IAM Dashboard:
    - Go to the AWS Management Console.
    - Select "IAM" from the services menu.

- Navigate to the Entity:
    - Go to "Users", "User groups", or "Roles" based on where you want to attach the policy.

- Attach Policy:
    - Select the user, group, or role.
    - Click on the "Permissions" tab and then click "Add permissions".
    - Attach existing policies or create a custom policy.

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
