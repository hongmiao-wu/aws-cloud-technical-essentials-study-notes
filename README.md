- [Module 1: AWS Overview and Security](#module-1-aws-overview-and-security)
  - [1. What is the cloud?](#1-what-is-the-cloud)
  - [2. What is cloud computing?](#2-what-is-cloud-computing)
  - [3. What are the benefits of cloud computing?](#3-what-are-the-benefits-of-cloud-computing)
  - [4. What are AWS Regions?](#4-what-are-aws-regions)
  - [5. What are Availablity Zones?](#5-what-are-availablity-zones)
  - [6. Security OF the cloud vs. security IN the cloud](#6-security-of-the-cloud-vs-security-in-the-cloud)
  - [7. AWS root user credentials](#7-aws-root-user-credentials)
  - [8. What is IAM?](#8-what-is-iam)
  - [9. What is the principle of the least privilege?](#9-what-is-the-principle-of-the-least-privilege)
  - [10. What is IdP?](#10-what-is-idp)
  - [Lab 1: Introduction to IAM](#lab-1-introduction-to-iam)
  - [11. What is an IAM role?](#11-what-is-an-iam-role)
  - [12. IAM role vs. IAM user](#12-iam-role-vs-iam-user)
  - [13. What is Amazon S3?](#13-what-is-amazon-s3)
  - [14. What is Amazon EC2?](#14-what-is-amazon-ec2)
  - [15. What is EC2 instance?](#15-what-is-ec2-instance)
  - [16. What is AMI?](#16-what-is-ami)
  - [17. What is VPC?](#17-what-is-vpc)
- [Module 2: Compute and Networking](#module-2-compute-and-networking)
  - [18. Servers and clients](#18-servers-and-clients)
  - [19. Virtual machines in AWS](#19-virtual-machines-in-aws)
  - [20. What is the relationship between AMIs and EC2 Instances?](#20-what-is-the-relationship-between-amis-and-ec2-instances)
  - [21. What makes up an EC2 instance?](#21-what-makes-up-an-ec2-instance)
  - [22. EC2 instance lifecycle/actions (TODO: needs more clarification)](#22-ec2-instance-lifecycleactions-todo-needs-more-clarification)
  - [23. What is a container?](#23-what-is-a-container)
  - [24. What is Docker?](#24-what-is-docker)
  - [25. Container vs. Virutal Machine](#25-container-vs-virutal-machine)
  - [26. Amazon container orchestration services ECS \& EKS (TODO)](#26-amazon-container-orchestration-services-ecs--eks-todo)
  - [27. What is Kubernetes？](#27-what-is-kubernetes)
  - [28. What is serverless?](#28-what-is-serverless)
  - [29. AWS Fargate and AWS Lambda](#29-aws-fargate-and-aws-lambda)
  - [30. HOW Lambda works?](#30-how-lambda-works)
  - [31. What is networking?](#31-what-is-networking)

## Module 1: AWS Overview and Security

### 1. What is the cloud?
The cloud is a global network of remote servers designed to store and process data for other devices and computers. This architecture allows people to save their files and applications in the cloud. They can access them online, rather than relying on local storage.

More at [What is the Cloud?](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-the-cloud#:~:text=In%20technology%2C%20the%20cloud%20is,and%20applications%20in%20the%20cloud).

### 2. What is cloud computing?

Cloud computing isn’t a product—it’s a way of doing things. It’s a conceptual shift in how computing resources are delivered.

The ISO standard defines cloud computing as follows (ISO/IEC 22123-1 section 3.1.1): 

*cloud computing: paradigm for enabling network access to a scalable and elastic pool of shareable physical or virtual resources with self-service provisioning and administration on-demand*

More at [Cloud Computing Basics](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Empfehlungen-nach-Angriffszielen/Cloud-Computing/Grundlagen/grundlagen_node.html)

### 3. What are the benefits of cloud computing?

- Cost efficiency: Pay only for what you use.
- Economies of scale: Leverage large-scale infrastructure.
- Scalability: Adjust capacity as needed.
- Agility: Enhance speed and flexibility.
- Cost savings: Eliminate data center maintenance expenses.
- Global reach: Deploy services worldwide quickly.

More at [What is cloud computing?](https://aws.amazon.com/what-is-cloud-computing/)

### 4. What are AWS Regions?

Regions are geographic locations worldwide where AWS hosts its data centers. AWS Regions are named after the location where they reside. 

AWS Regions are independent from one another. This means that your data is not replicated from one Region to another, without your explicit consent and authorization.

A few examples of Region codes:

- us-east-1: the first Region created in the east of the US.
- ap-northeast-1: the first Region created in the northeast of Asia Pacific.

Consider four main aspects when deciding which AWS Region:
- Latency: if your application is sensitive to latency, choose a Region that is close to your user base. 
- Price: prices may vary from one Region to another. 
- Service availability: Some services may not be available in some Regions. 
- Data compliance: enterprise companies often need to comply with regulations that require customer data to be stored in a specific geographic territory. 


More at [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)

### 5. What are Availablity Zones?

Inside every Region is a cluster of Availability Zones (AZ). An AZ consists of one or more data centers with redundant power, networking, and connectivity. 

![Availability Zones](/resources/az.png)

AZs also have a code name. For example:

- us-east-1a: an AZ in us-east-1 (Northern Virginia Region)

- sa-east-1b: an AZ in sa-east-1 (São Paulo Region in South America)

Note:
- To keep your application available, maintain high availability and resiliency.
- Use Region-scoped, managed services when possible.
- If not, replicate workloads across multiple AZs to avoid failure from a single AZ.

### 6. Security OF the cloud vs. security IN the cloud

AWS is responsible for security **OF** the cloud. This means AWS is required to protect and secure the infrastructure that runs all the services offered in the AWS Cloud. *Note: The level of responsibility AWS has depends on the service.*

You’re responsible for security **IN** the cloud. When using any AWS service, you’re responsible for properly configuring the service and your applications, as well as ensuring your data is secure. *Note: The level of responsibility you have depends on the AWS service.*

![security_OF_IN_the_cloud](/resources/security_OF_IN_the_cloud.png)

More at [AWS Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)

### 7. AWS root user credentials

When you create an AWS account, you get a root user with full access to all services and resources. You sign in using the email and password you used to set up the account.

AWS also provides access keys for programmatic access using the AWS CLI or API. These keys include an access key ID and a secret access key, like a username and password. 

To ensure the safety of the root user:

- Choose a strong password for the root user.

- Never share your root user password or access keys with anyone.

- Disable or delete the access keys associated with the root user.

- Do not use the root user for administrative tasks or everyday tasks.

- Enable MFA on your AWS root user. 

### 8. What is IAM?

Amazon Identity and Access Management (IAM) is a web service that helps you securely control access to Amazon resources.

Use IAM to set up other identities in addition to your root user, such as administrators, analysts, and developers, and grant them access to the resources they need to succeed in their tasks.

More at [What is IAM?](https://docs.amazonaws.cn/en_us/IAM/latest/UserGuide/introduction.html)

### 9. What is the principle of the least privilege?
    
Least privilege is a standard security principle that advises you to grant only the necessary permissions to do a particular job and nothing more. 

### 10. What is IdP?

An Identity Provider (IdP) is a centralized system that manages user identities and controls access to multiple services. It allows employees to use a single set of credentials to log in to different systems, like AWS, Google Workspace, or other platforms. With an IdP, you can easily manage permissions, simplify user updates, and improve security by having one source of truth for all identities in your organization.

### Lab 1: Introduction to IAM

This lab guides you step by step through the Amazon IAM console to:

- Explore IAM Users and Groups
- Inspect IAM policies applied to groups
- Add users to groups and explore group permissions
- Locate and use the IAM sign-in URL
- Experiment with policies and service access

### 11. What is an IAM role?

An IAM role is an IAM identity that you can create in your account that has specific permissions. 

More at [IAM roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)

### 12. IAM role vs. IAM user

An IAM role is similar to an IAM user, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it. Also, a role does not have standard long-term credentials such as a password or access keys associated with it.

### 13. What is Amazon S3?

Amazon Simple Storage Service (Amazon S3) is an **object storage service** that stores data as objects within buckets. 

### 14. What is Amazon EC2?

Amazon Elastic Compute Cloud (Amazon EC2) provides on-demand, scalable **computing capacity** in the Amazon Web Services (AWS) Cloud.

### 15. What is EC2 instance?

An EC2 instance is a virtual server in the AWS Cloud. 

![ec2-instance](/resources/instance-types.png)

### 16. What is AMI?

Amazon Machine Images (AMIs): Preconfigured templates for your instances that package the components you need for your server (including the operating system and additional software).

### 17. What is VPC?

A Virtual Private Cloud (VPC) is a virtual network that closely resembles a traditional network that you'd operate in your own data center. 

![vpc](/resources/VPC.png)

## Module 2: Compute and Networking

### 18. Servers and clients

A client being a person or computer that sends a request, and a server handling the requests is a computer, or collection of computers, connected to the internet serving websites to internet users. 

These servers power your application by providing CPU, memory, and networking capacity to process users’ requests and transform them into responses.

### 19. Virtual machines in AWS

At a fundamental level, there are three types of compute options: virtual machines, container services, and serverless.

A virtual machine can often be the easiest compute option in AWS to understand. This is because a virtual machine emulates a physical server and allows you to install an HTTP server to run your applications.

In AWS, these virtual machines are called Amazon Elastic Compute Cloud or **Amazon EC2**. 

More at [AWS: compute services whitepaper](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/compute-services.html)

### 20. What is the relationship between AMIs and EC2 Instances?
EC2 instances are live instantiations of what is defined in an AMI, much like a class and an Object.

### 21. What makes up an EC2 instance?
EC2 instances are a combination of virtual processors (vCPUs), memory, network, and in some cases, instance storage and graphics processing units (GPUs). 

*Note: While EC2 instances are typically reliable, two is better than one, and three is better than two.* 

### 22. EC2 instance lifecycle/actions (TODO: needs more clarification)
- pending: when you launch an instance, it enters the pending state, the billing has not started.  
- running: it's ready to use. This is also the stage where billing begins. 
- reboot: the instance remains on the same host computer and maintains its public and private IP address, and any data on its instance store. *It’s different than performing a stop action and then a start action*
- stop:
- start:
- terminate: when you terminate an instance, the instance store are erased, and you lose both the public IP address and private IP address of the machine. 
- stop-hibernate:
![instance-lifecycle](/resources/instance_lifecycle.png)

More at: [Amazon EC2 instance state changes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html)

### 23. What is a container?
A container is a standardized unit that packages up your code and all of its dependencies. This package is designed to run reliably on any platform, because the container creates its own independent environment. 

### 24. What is Docker?
Docker is a popular tool that simplifies the management of the entire operating system stack needed for container isolation, including networking and storage.

### 25. Container vs. Virutal Machine
Containers are an abstraction at the app layer that packages code and dependencies together. 
Multiple containers can run on the same machine and share the OS kernel with other containers, each running as isolated processes in user space. 

Virtual machines (VMs) are an abstraction of physical hardware turning one server into many servers. 
The hypervisor allows multiple VMs to run on a single machine. 

Containers take up less space than VMs (typically tens of MBs vs. tens of GBs) and fast to boot.

More at: [Docker: what is a container?](https://www.docker.com/resources/what-container/)

### 26. Amazon container orchestration services ECS & EKS (TODO)
In AWS, containers run on EC2 instances. Most companies and organizations run many containers on many EC2 instances across several Availability Zones. 

If you’re trying to manage your compute at a large scale, you need to know:

- How to place your containers on your instances.

- What happens if your container fails.

- What happens if your instance fails.

- How to monitor deployments of your containers.

AWS offers two container orchestration services: Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS)

### 27. What is Kubernetes？
Kubernetes is a portable, extensible, open source platform for managing containerized workloads and services. 

### 28. What is serverless?
Serverless is a cloud-native development model that allows developers to build and run applications without having to manage servers.

There are still servers in serverless, but they are abstracted away from app development. A cloud provider handles the routine work of provisioning, maintaining, and scaling the server infrastructure. Developers can simply package their code in containers for deployment.

More at: [Red Hat: What is serverless?](https://www.redhat.com/en/topics/cloud-native-apps/what-is-serverless)

### 29. AWS Fargate and AWS Lambda
AWS Fargate abstracts the EC2 instance so you’re not required to manage it. However, with AWS Fargate, you can use all the same ECS primitives, APIs, and AWS integrations.

AWS Lambda lets you run code without provisioning or managing servers or containers. 

### 30. HOW Lambda works?
There are three primary components of a Lambda function: the trigger, code, and configuration.

The code is source code, that describes what the Lambda function should run. 

The configuration of a Lambda function consists of information that describes how the function should run. In the configuration, you specify network placement, environment variables, memory, invocation type, permission sets, and other configurations. 

Triggers describe when the Lambda function should run. 

More at: [Configuring AWS Lambda functions](https://docs.aws.amazon.com/lambda/latest/dg/lambda-functions.html)
![AWS-lambda](/resources/aws-lambda.png)

### 31. What is networking?
