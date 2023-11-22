Security is a top priority for Amazon Web Services (AWS), and they implement a shared responsibility model to clarify the division of security responsibilities between AWS and its customers. The AWS Shared Responsibility Model defines which security measures are the responsibility of AWS and which are the responsibility of the customer. This model is crucial for ensuring a secure cloud computing environment.

![[Pasted image 20231121051333.png]]


## 1. AWS Responsibility

| **Category** | **Examples of AWS Services in the Category** | **AWS Responsability** |
|----------|-----------------------------------------------|-----------------------|
|infrastructure services| Compute services, such as Amazon Elastic Compute Cloud **(Amazon EC2)**|AWS manages the underlying infrastructure and foundation services.|
|container services | Services that require less management from the customer, such as Amazon Relational Database Service (Amazon RDS) |AWS manages the underlying infrastructure and foundation services, operating system, and application platform.
|Abstracted services | Services that require very little management from the customer, such as Amazon Simple Storage Service (Amazon S3) | AWS operates the infrastructure layer, operating system, and platforms, as well as server-side encryption and data protection.

### a. Global Infrastructure **Security**
   - AWS is responsible for the security of the infrastructure that includes data centers, networking, and hardware.

### b. Physical Security
   - AWS ensures the physical security of the data centers, including access control, surveillance, and environmental controls.

### c. Hypervisor Security
   - AWS manages the security of the virtualization layer (hypervisor) that separates and secures customer resources.

### d. Managed Services Security
   - Security of AWS-managed services (e.g., Amazon RDS, Amazon S3) is the responsibility of AWS. Customers leverage these services without having to manage the underlying infrastructure.

### e. Compliance and Certifications
   - AWS maintains a wide range of compliance certifications and provides a secure foundation for customers to build upon.

## 2. Customer Responsibility

| **Category**               | **AWS Responsibility**                                            | **Customer Responsibility**                                                 |
|------------------------|--------------------------------------------------------------|-------------------------------------------------------------------------|
| Infrastructure services| AWS manages the infrastructure and foundation services.       | You control the operating system and application platform, as well as encrypting, protecting, and managing customer data.                 |
| Container services      | AWS manages the infrastructure and foundation services, operating system, and application platform. | You are responsible for customer data, encrypting that data, and protecting it through network firewalls and backups.                      |
| Abstracted services     | AWS operates the infrastructure layer, operating system, and platforms, as well as server-side encryption and data protection. | You are responsible for managing customer data and protecting it through client-side encryption.                                         |
****

### a. Data Security
   - Customers are responsible for the security of their own data, including encryption in transit and at rest.

### b. Identity and Access Management (IAM)
   - Customers manage user access to AWS resources, defining and enforcing policies using AWS IAM.

### c. Platform and Applications
   - Security configurations and updates for operating systems, applications, and databases running on AWS are the responsibility of the customer.

### d. Network Security
   - Customers are responsible for configuring network security, including firewalls, security groups, and network access control lists (ACLs).

### e. Data Encryption
   - While AWS provides encryption tools, customers are responsible for implementing encryption for their data, both in transit and at rest.

### f. Identity and Access Management (IAM)
   - Customers are responsible for managing user identities, roles, and permissions within AWS.

### g. Application Security
   - The security of applications developed and deployed on AWS is the responsibility of the customer.

## 3. Shared Responsibility in Action

### a. Example 1 - Amazon S3
   - AWS is responsible for securing the infrastructure and managing the security of the S3 service. Customers are responsible for configuring access controls (e.g., bucket policies, access control lists) and encrypting their data stored in S3.

### b. Example 2 - Amazon EC2
   - AWS is responsible for the security of the underlying infrastructure, while customers are responsible for securing their EC2 instances, including patch management, firewall configuration, and application security.

## 4. Continuous Monitoring and Improvement

- Both AWS and customers share the responsibility for continuously monitoring and improving security. AWS provides tools and services to assist customers in monitoring their environment, but customers must actively use these tools and respond to security events.

By clearly defining the shared responsibility model, AWS aims to ensure a secure cloud environment while empowering customers with the flexibility and control they need to implement security measures for their specific applications and data. It's essential for AWS customers to understand and fulfill their role in this shared responsibility to create a secure and compliant cloud environment.
