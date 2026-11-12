# Amazon EC2 Instance Storage `ris:Database2`

Amazon EC2 Instance Storage, also known as ephemeral storage, is directly attached to the EC2 instance. It is ideal for temporary data storage, such as buffers, caches, and scratch data that can be recreated if lost. This storage is physically attached to the host machine running the EC2 instance. The data on instance storage is volatile and is lost if the instance is stopped or terminated. Performance is often better than Amazon EBS, as it is directly connected to the instance and not over the network. However, it is specific to the instance type and cannot be resized or attached to another instance. 📉

# Amazon Elastic Block Store (EBS) `ris:Database2`

Amazon Elastic Block Store (EBS) provides persistent block-level storage volumes that can be attached to EC2 instances. It is suitable for data that requires long-term persistence, such as databases and file systems. EBS volumes are network-attached storage and can be detached from one instance and attached to another, providing more flexibility. Unlike instance storage, EBS volumes persist independently of the life of an EC2 instance. Data is not lost when an instance is stopped or terminated. EBS volumes can be resized, and additional volumes can be attached to an instance. Different types of EBS volumes are available, such as General Purpose (SSD), Provisioned IOPS (SSD), Cold HDD, and Throughput Optimized HDD. 🚀

## Use Cases

Consider using EC2 instance storage when you need high-performance, temporary storage and can afford to lose the data in case of instance termination. On the other hand, opt for Amazon EBS when you need persistent and reliable storage that can be detached from one instance and attached to another, and when data durability is critical. 👍

In summary, the choice between EC2 Instance Storage and Amazon EBS depends on the specific requirements of your application, such as performance needs, data persistence, and the ability to detach and move storage between instances.

## Reading 3.2: Amazon EC2 Instance Storage and Amazon Elastic Block Store

**Amazon EC2 Instance Store**

Amazon EC2 Instance Store provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer. This ties the lifecycle of your data to the lifecycle of your EC2 instance. If you delete your instance, the instance store is deleted as well. Due to this, instance store is considered ephemeral storage.

Instance store is ideal if you are hosting applications that replicate data to other EC2 instances, such as Hadoop clusters. For these cluster-based workloads, having the speed of locally attached volumes and the resiliency of replicated data helps you achieve data distribution at high performance. It’s also ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content. 💻

**Amazon Elastic Block Storage (Amazon EBS)** As the name implies, Amazon EBS is a block-level storage device that you can attach to an Amazon EC2 instance. These storage devices are called Amazon EBS volumes. EBS volumes are essentially drives of a user-configured size attached to an EC2 instance, similar to how you might attach an external drive to your laptop.

EBS volumes act similarly to external drives in more than one way.

- Most Amazon EBS volumes can only be connected with one computer at a time. Most EBS volumes have a one-to-one relationship with EC2 instances, so they cannot be shared by or attached to multiple instances at one time.
- You can detach an EBS volume from one EC2 instance and attach it to another EC2 instance in the same Availability Zone, to access the data on it.
- The external drive is separate from the computer. That means, if an accident happens and the computer goes down, you still have your data on your external drive. The same is true for EBS volumes.
- You’re limited to the size of the external drive, since it has a fixed limit to how scalable it can be. For example, you may have a 2 TB external drive and that means you can only have 2 TB of content on there. This relates to EBS as well, since volumes also have a max limitation of how much content you can store on the volume.

### Scale Amazon EBS Volumes

You can scale Amazon EBS volumes in two ways.

1. Increase the volume size, as long as it doesn’t increase above the maximum size limit. For EBS volumes, the maximum amount of storage you can have is 16 TB.
2. Attach multiple volumes to a single Amazon EC2 instance. EC2 has a one-to-many relationship with EBS volumes.

### Amazon EBS Use Cases

Amazon EBS is useful when you need to retrieve data quickly and have data persist long-term. Volumes are commonly used in the following scenarios.

- Operating systems: Boot/root volumes to store an operating system.
- Databases: A storage layer for databases running on Amazon EC2.
- Enterprise applications: Amazon EBS provides reliable block storage to run business-critical applications.
- Throughput-intensive applications: Applications that perform long, continuous reads and writes.

### Amazon EBS Volume Types

||EBS Provisioned IOPS SSD|EBS General Purpose SSD|Throughput Optimized HDD|Cold HDD|
|---|---|---|---|---|
|**Description**|Highest performance SSD designed for latency-sensitive transactional workloads|General purpose SSD that balances price and performance for a wide variety of transactional workloads|Low-cost HDD designed for frequently accessed, throughput intensive workloads|Lowest cost HDD designed for less frequently accessed workloads|
|**Use Cases**|I/O-intensive NoSQL and relational databases|Boot volumes, low-latency interactive apps, development, and test|Big data, data warehouses, log processing|Colder data requiring fewer scans per day|
|**Volume Size**|4 GB-16 TB|1 GB-16 TB|500 GB-16 TB|500 GB-16 TB|
|**Max IOPS/Volume**|64,000|16,000|500|250|
|**Max Throughput/Volume**|1,000 MB/s|250 MB/s|500 MB/s|250 MB/s|

## Benefits of Using Amazon EBS

Here are the following benefits of using Amazon EBS (in case you need a quick cheat sheet).

- High availability: When you create an EBS volume, it is automatically replicated within its Availability Zone to prevent data loss from single points of failure.
- Data persistence: The storage persists even when your instance doesn’t.
- Data encryption: All EBS volumes support encryption.
- Flexibility: EBS volumes support on-the-fly changes.
- Cost-effective: EBS provides flexible pricing options to match your storage needs. 👍

## Resources

- [_External Site:_ AWS: Amazon Elastic Block Store (Amazon EBS)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)
- [_External Site:_ AWS: Amazon EBS FAQs](https://aws.amazon.com/ebs/faqs/)