  
# Amazon EC2 Instance Storage `ris:Database2`

Amazon EC2 Instance Storage, also known as ephemeral storage, ==is directly attached to the EC2 instance==. It is ideal for temporary data storage, such as buffers, caches, and scratch data that can be recreated if lost. This storage is physically attached to the host machine running the EC2 instance. The data on instance storage is volatile and is lost if the instance is stopped or terminated. Performance is often better than Amazon EBS, as it is directly connected to the instance and not over the network. However, it is specific to the instance type and cannot be resized or attached to another instance.

# Amazon Elastic Block Store (EBS) `ris:Database2`

Amazon Elastic Block Store (EBS) provides persistent ==block-level storage volumes that can be attached to EC2 instances==. It is suitable for data that requires long-term persistence, such as databases and file systems. ==EBS volumes are network-attached storage and can be detached from one instance and attached to another==, providing more flexibility. Unlike instance storage, EBS volumes persist independently of the life of an EC2 instance. Data is not lost when an instance is stopped or terminated. EBS volumes can be resized, and additional volumes can be attached to an instance. Different types of EBS volumes are available, each with its own performance characteristics, ==such as General Purpose (SSD), Provisioned IOPS (SSD), Cold HDD, and Throughput Optimized HDD.==

# Use Cases

==Consider using EC2 instance storage when you need high-performance==, temporary storage and can afford to lose the data in case of instance termination. ==On the other hand, opt for Amazon EBS when you need persistent and reliable storage that can be detached from one instance and attached to another, and when data durability is critical==.

In summary, the choice between EC2 Instance Storage and Amazon EBS depends on the specific requirements of your application, such as performance needs, data persistence, and the ability to detach and move storage between instances.



More info  `ris:ArrowDown`

# Reading 3.2: Amazon EC2 Instance Storage and Amazon Elastic Block Store

**Amazon EC2 Instance Store**

Amazon EC2 Instance Store provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer. This ties the lifecycle of your data to the lifecycle of your EC2 instance. If you delete your instance, the instance store is deleted as well. Due to this, instance store is considered ephemeral storage. Read more about it in the [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) .

Instance store is ideal if you are hosting applications that replicate data to other EC2 instances, such as Hadoop clusters. For these cluster-based workloads, having the speed of locally attached volumes and the resiliency of replicated data helps you achieve data distribution at high performance. It’s also ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content.

**Amazon Elastic Block Storage (Amazon EBS)** As the name implies, Amazon EBS is a block-level storage device that you can attach to an Amazon EC2 instance. These storage devices are called Amazon EBS volumes. EBS volumes are essentially drives of a user-configured size attached to an EC2 instance, similar to how you might attach an external drive to your laptop.

EBS volumes act similarly to external drives in more than one way.

- Most Amazon EBS volumes can only be connected with one computer at a time. Most EBS volumes have a one-to-one relationship with EC2 instances, so they cannot be shared by or attached to multiple instances at one time. _Note: Recently, AWS announced the Amazon EBS multi-attach feature that enables volumes to be attached to multiple EC2 instances at one time. This feature is not available for all instance types and all instances must be in the same Availability Zone. Read more about this scenario in the_ [_EBS documentation_](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes-multi.html) _._
    
- You can detach an EBS volume from one EC2 instance and attach it to another EC2 instance in the same Availability Zone, to access the data on it.
    
- The external drive is separate from the computer. That means, if an accident happens and the computer goes down, you still have your data on your external drive. The same is true for EBS volumes.
    
- You’re limited to the size of the external drive, since it has a fixed limit to how scalable it can be. For example, you may have a 2 TB external drive and that means you can only have 2 TB of content on there. This relates to EBS as well, since volumes also have a max limitation of how much content you can store on the volume.
    

### Scale Amazon EBS Volumes

You can scale Amazon EBS volumes in two ways.

1. Increase the volume size, as long as it doesn’t increase above the maximum size limit. For EBS volumes, the maximum amount of storage you can have is 16 TB. That means if you provision a 5 TB EBS volume, you can choose to increase the size of your volume until you get to 16 TB.
    
2. Attach multiple volumes to a single Amazon EC2 instance. EC2 has a one-to-many relationship with EBS volumes. You can add these additional volumes during or after EC2 instance creation to provide more storage capacity for your hosts.
    

### Amazon EBS Use Cases

Amazon EBS is useful when you need to retrieve data quickly and have data persist long-term. Volumes are commonly used in the following scenarios.

- **Operating systems:** Boot/root volumes to store an operating system. The root device for an instance launched from an Amazon Machine Image (AMI) is typically an Amazon EBS volume. These are commonly referred to as EBS-backed AMIs.
    
- **Databases:** A storage layer for databases running on Amazon EC2 that rely on transactional reads and writes.
    
- **Enterprise applications:** Amazon EBS provides reliable block storage to run business-critical applications.
    
- **Throughput-intensive applications:** Applications that perform long, continuous reads and writes.
    

### Amazon EBS Volume Types

||EBS Provisioned IOPS SSD|EBS General Purpose SSD|Throughput Optimized HDD|Cold HDD|
|---|---|---|---|---|
|**Description**|Highest performance SSD designed for latency-sensitive transactional workloads|General purpose SSD that balances price and performance for a wide variety of transactional workloads|Low-cost HDD designed for frequently accessed, throughput intensive workloads|Lowest cost HDD designed for less frequently accessed workloads|
|**Use Cases**|I/O-intensive NoSQL and relational databases|Boot volumes, low-latency interactive apps, development, and test|Big data, data warehouses, log processing|Colder data requiring fewer scans per day|
|**Volume Size**|4 GB-16 TB|1 GB-16 TB|500 GB-16 TB|500 GB-16 TB|
|**Max IOPS/Volume**|64,000|16,000|500|250|
|**Max Throughput/Volume**|1,000 MB/s|250 MB/s|500 MB/s|250 MB/s|

There are two main categories of Amazon EBS volumes: solid-state drives (SSDs) and hard-disk drives (HDDs). SSDs provide strong performance for random input/output (I/O), while HDDs provide strong performance for sequential I/O. AWS offers two types of each. The following chart can help you decide which EBS volume is the right option for your workload.

### Benefits of Using Amazon EBS

Here are the following benefits of using Amazon EBS (in case you need a quick cheat sheet).

- High availability: When you create an EBS volume, it is automatically replicated within its Availability Zone to prevent data loss from single points of failure.
    
- Data persistence: The storage persists even when your instance doesn’t.
    
- Data encryption: All EBS volumes support encryption.
    
- Flexibility: EBS volumes support on-the-fly changes. You can modify volume type, volume size, and input/output operations per second (IOPS) capacity without stopping your instance.
    
- Backups: Amazon EBS provides you the ability to create backups of any EBS volume.
    

### EBS Snapshots

Errors happen. One of those errors is not backing up data, and then, inevitably losing that data. To prevent this from happening to you, you should back up your data—even in AWS. Since your EBS volumes consist of the data from your Amazon EC2 instance, you’ll want to take backups of these volumes, called snapshots.

EBS snapshots are incremental backups that only save the blocks on the volume that have changed after your most recent snapshot. For example, if you have 10 GB of data on a volume, and only 2 GB of data have been modified since your last snapshot, only the 2 GB that have been changed are written to Amazon Simple Storage Service (Amazon S3).

When you take a snapshot of any of your EBS volumes, these backups are stored redundantly in multiple Availability Zones using Amazon S3. This aspect of storing the backup in Amazon S3 will be handled by AWS, so you won’t need to interact with Amazon S3 to work with your EBS snapshots. You simply manage them in the EBS console (which is part of the EC2 console).

EBS snapshots can be used to create multiple new volumes, whether they’re in the same Availability Zone or a different one. When you create a new volume from a snapshot, it’s an exact copy of the original volume at the time the snapshot was taken.

### **Resources**

- [_External Site:_ AWS: Amazon Elastic Block Store (Amazon EBS)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)
    
- [_External Site:_ AWS: Amazon EBS FAQs](https://aws.amazon.com/ebs/faqs/)