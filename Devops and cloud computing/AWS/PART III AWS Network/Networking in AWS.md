
Networking in AWS refers to the ==infrastructure and services that enable communication between different components of your applications==, data centers, and AWS services. AWS provides a comprehensive set of networking services that allow you to build, configure, and manage your network infrastructure in the cloud. Here are some key aspects of networking in AWS:

### [[Amazon Virtual Private Cloud (VPC)|Virtual Private Cloud (VPC)]]

A VPC is a logically isolated section of the AWS Cloud where you can launch AWS resources. It is customizable, allowing control over IP address ranges, subnets, route tables, and network gateways. VPCs provide network isolation, enabling the creation of multiple VPCs for different applications or environments.

### Subnets

==Subnets are segments of a VPC's IP address range where you can place groups of resources==. They are used to organize and ==isolate resources==, and they can be public or private. Public subnets are associated with a route to the internet, while private subnets are not.

### Route Tables

==A route table contains a set of rules, called routes, that determine where network traffic is directed==. Route tables are associated with subnets and control traffic leaving the subnet. They are used to route traffic within the VPC and between the VPC and external networks.

### Internet Gateway (IGW)

An Internet Gateway is a horizontally scaled, redundant, and highly available VPC component that enables communication between instances in your VPC and the internet. It allows resources within your VPC to access the internet and is associated with a VPC's route table.

### Elastic Load Balancer (ELB)

ELB automatically distributes incoming application traffic across multiple targets, enhancing the availability and fault tolerance of applications. It scales resources dynamically, distributing traffic across EC2 instances in multiple Availability Zones.

### Amazon Route 53

Route 53 is a scalable and highly available Domain Name System (DNS) web service. It is used for domain registration, DNS routing, and health checking, enabling global routing of users to endpoints.

### Virtual Private Network (VPN) and Direct Connect

- **VPN:** AWS VPN allows you to connect your on-premises data centers to your VPC using encrypted tunnels over the internet.
- **Direct Connect:** This is a dedicated network connection from your on-premises data centers to AWS, providing more reliable and consistent performance compared to VPN.

### AWS Direct Connect Gateway

A globally available resource that allows you to connect multiple Virtual Private Gateways (VGWs) from different AWS Regions to your on-premises networks.

These headers provide a structured overview of key networking components in AWS. Understanding these components is essential for designing secure, scalable, and performant architectures in the AWS Cloud.