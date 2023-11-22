
An **IAM Role** in AWS (Identity and Access Management) is a set of permissions that define what actions are allowed or denied for entities (such as AWS users or AWS services) assuming the role. Roles are used to grant temporary access to AWS resources without the need for sharing long-term security credentials.

## Key Characteristics of IAM Roles:

- **Temporary Permissions:**
  - IAM roles provide temporary permissions that can be assumed by entities when needed. This helps in minimizing the exposure of security credentials.

- **Assume Role Action:**
  - Entities assume a role using the "AssumeRole" API action. Once assumed, the entity takes on the permissions and policies associated with the role.

- **Delegation of Permissions:**
  - Roles are often used to delegate permissions between AWS accounts, services, or within the same AWS account. This allows for a granular and secure permission structure.

- **Cross-Account Access:**
  - IAM roles enable cross-account access, allowing entities from one AWS account to assume a role in another AWS account. This is commonly used for resource sharing and collaboration.

## Creating an IAM Role:

IAM roles are created and configured in the AWS Management Console, AWS CLI, or using AWS SDKs and APIs. When creating a role, you define the trusted entities (the entities allowed to assume the role) and attach policies specifying the permissions for the role.

### Example IAM Role Creation (AWS CLI):

```sh
aws iam create-role --role-name MyRole --assume-role-policy-document file://trust
