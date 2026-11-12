# Reading 3.4: Choose the Right Storage Service

Here’s a recap of all the storage services mentioned so far. By the end of this reading, you should be able to better answer the question “Which storage service should I use?” for some of the more common scenarios.

## Amazon EC2 Instance Store

Instance store is ephemeral block storage. This is preconfigured storage that exists on the same physical server that hosts the EC2 instance and cannot be detached from Amazon EC2. You can think of it as a built-in drive for your EC2 instance. Instance store is generally well-suited for temporary storage of information that is constantly changing, such as buffers, caches, and scratch data. It is not meant for data that is persistent or long-lasting. If you need persistent long-term block storage that can be detached from Amazon EC2 and provide you more management flexibility, such as increasing volume size or creating snapshots, then you should use Amazon EBS.

## Amazon EBS

Amazon EBS is meant for data that changes frequently and needs to persist through instance stops, terminations, or hardware failures. Amazon EBS has two different types of volumes: SSD-backed volumes and HDD-backed volumes.SSD-backed volumes have the following characteristics.

- Performance depends on IOPS (input/output operations per second).
    
- Ideal for transactional workloads such as databases and boot volumes.
    

HDD-backed volumes have the following characteristics:

- Performance depends on MB/s.
    
- Ideal for throughput-intensive workloads, such as big data, data warehouses, log processing, and sequential data I/O.
    

Here are a few important features of Amazon EBS that you need to know when comparing it to other services.

- It is block storage.
    
- You pay for what you provision (you have to provision storage in advance).
    
- EBS volumes are replicated across multiple servers in a single Availability Zone.
    
- Most EBS volumes can only be attached to a single EC2 instance at a time.
    

## Amazon S3

If your data doesn’t change that often, Amazon S3 might be a more cost-effective and scalable storage solution. S3 is ideal for storing static web content and media, backups and archiving, data for analytics, and can even be used to host entire static websites with custom domain names.Here are a few important features of Amazon S3 to know about when comparing it to other services.

- It is object storage.
    
- You pay for what you use (you don’t have to provision storage in advance).
    
- Amazon S3 replicates your objects across multiple Availability Zones in a Region.
    
- Amazon S3 is not storage attached to compute.
    

## Amazon Elastic File System (Amazon EFS) and Amazon FSx

In this module, you’ve already learned about Amazon S3 and Amazon EBS. You learned that S3 uses a flat namespace and isn’t meant to serve as a standalone file system. You also learned most EBS volumes can only be attached to one EC2 instance at a time. So, if you need file storage on AWS, which service should you use?For file storage that can mount on to multiple EC2 instances, you can use Amazon Elastic File System (Amazon EFS) or Amazon FSx. Use the following table for more information about each of these services.

|   |   |   |
|---|---|---|
|Service|Characteristic|More Information|
|Amazon Elastic File System (EFS)|Fully managed NFS file system.|[EFS FAQs](https://aws.amazon.com/efs/faq/)|
|Amazon FSx for Windows File Server|Fully managed file server built on Windows Server that supports the SMB protocol.|[FSx for Windows File Server FAQs](https://aws.amazon.com/fsx/windows/faqs/?nc=sn&loc=8)|
|Amazon FSx for Lustre|Fully managed Lustre file system that integrates with S3.|[FSx for Lustre FAQs](https://aws.amazon.com/fsx/lustre/faqs/?nc=sn&loc=5)|

Here are a few important features of Amazon EFS and FSx to know about when comparing them to other services.

- It is file storage.
    
- You pay for what you use (you don’t have to provision storage in advance).
    
- Amazon EFS and Amazon FSx can be mounted onto multiple EC2 instances.
    

**Resources**:

- [_External Site:_ AWS: Storage](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Storage.html)
    
- [_External Site:_ AWS: Cloud Storage on AWS](https://aws.amazon.com/products/storage/)
    
- [_External Site:_ Amazon EFS How it works](https://docs.aws.amazon.com/efs/latest/ug/how-it-works.html)
    
- [_External Site:_ Amazon FSx for Windows File Server](https://aws.amazon.com/fsx/windows/)
    
- [_External Site:_ Amazon FSx for Lustre](https://aws.amazon.com/fsx/lustre/)