
AWS Identity and Access Management (IAM) is a service provided by Amazon Web Services (AWS) that enables users to securely control access to AWS services and resources. IAM allows you to manage users, groups, roles, and their respective permissions within your AWS environment. This service is fundamental for ensuring the security and compliance of your AWS account by enforcing the principle of least privilege.

## Key Concepts

### 1. Users
   - IAM users represent individual AWS account holders or applications that interact with AWS resources. Each user has a unique set of security credentials (username and password or access keys).

### 2. Groups
   - Groups are collections of IAM users. Instead of attaching policies directly to users, you can assign permissions to groups, making it easier to manage access for multiple users with similar roles.

### 3. Roles
   - IAM roles define a set of permissions for making AWS service requests. Unlike users or groups, roles do not have credentials associated with them. Instead, IAM users or AWS services assume a role to obtain temporary security credentials.

### 4. Policies [[Policy Definition]]
   - IAM policies are JSON documents that define permissions. Policies can be attached to users, groups, or roles, specifying what actions are allowed or denied on which resources.

### 5. Permissions
   - IAM permissions define what actions are allowed or denied. They are granted through policies and determine what users, groups, or roles can do within AWS.

### 6. Authentication and Authorization
   - IAM handles authentication (verifying the identity of users, applications, or services) and authorization (determining what actions and resources a user, group, or role is allowed to access).

## Key Features

### 1. Multi-Factor Authentication (MFA) [[Multi-Factor Authentication (MFA) Definition]]
   - IAM supports the use of Multi-Factor Authentication, providing an additional layer of security by requiring users to present two or more forms of identification.

### 2. Identity Federation
   - IAM supports identity federation, allowing users to access AWS resources using existing credentials from their corporate directory (e.g., Active Directory).

### 3. Access Key Rotation
   - IAM allows for the rotation of access keys, enhancing security by regularly changing the credentials used for programmatic access.

### 4. IAM Access Advisor
   - Access Advisor provides information about the last time an IAM user or

IAM is a key component in securing and managing access to AWS resources, and understanding its concepts and features is essential for building a secure and well-managed cloud environment.
