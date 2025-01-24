
1. [What is the cloud?](#what-is-the-cloud)  
2. [What is cloud computing?](#what-is-cloud-computing)  
3. [What are the benefits of cloud computing?](#what-are-the-benefits-of-cloud-computing)  
4. [What are AWS Regions?](#what-are-aws-regions)  
5. [What are Availability Zones?](#what-are-availability-zones)  
6. [Security OF the cloud vs. security IN the cloud](#security-of-the-cloud-vs-security-in-the-cloud)  
7. [AWS root user credentials](#aws-root-user-credentials)  
8. [What is IAM?](#what-is-iam)  
9. [What is the principle of the least privilege?](#what-is-the-principle-of-the-least-privilege)  
10. [What is IdP?](#what-is-idp)


1) **What is the cloud?** 
    The cloud is a global network of remote servers designed to store and process data for other devices and computers. This architecture allows people to save their files and applications in the cloud. They can access them online, rather than relying on local storage.

    More at [What is the Cloud?](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-the-cloud#:~:text=In%20technology%2C%20the%20cloud%20is,and%20applications%20in%20the%20cloud).

2) **What is cloud computing?**

    Cloud computing isn’t a product—it’s a way of doing things. It’s a conceptual shift in how computing resources are delivered.

    The ISO standard defines cloud computing as follows (ISO/IEC 22123-1 section 3.1.1): 

    *cloud computing: paradigm for enabling network access to a scalable and elastic pool of shareable physical or virtual resources with self-service provisioning and administration on-demand*

    More at [Cloud Computing Basics](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Empfehlungen-nach-Angriffszielen/Cloud-Computing/Grundlagen/grundlagen_node.html)

3) **What are the benefits of cloud computing?**

- Cost efficiency: Pay only for what you use.
- Economies of scale: Leverage large-scale infrastructure.
- Scalability: Adjust capacity as needed.
- Agility: Enhance speed and flexibility.
- Cost savings: Eliminate data center maintenance expenses.
- Global reach: Deploy services worldwide quickly.

    More at [What is cloud computing?](https://aws.amazon.com/what-is-cloud-computing/)

4) **What are AWS Regions?**

    Regions are geographic locations worldwide where AWS hosts its data centers. AWS Regions are named after the location where they reside. 

    AWS Regions are independent from one another. This means that your data is not replicated from one Region to another, without your explicit consent and authorization.

    A few examples of Region codes:

    - us-east-1: the first Region created in the east of the US.
    - ap-northeast-1: the first Region created in the northeast of Asia Pacific.

    More at [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)

5) **What are Availablity Zones?**

    Inside every Region is a cluster of Availability Zones (AZ). An AZ consists of one or more data centers with redundant power, networking, and connectivity. 

    ![Availability Zones](/resources/az.png)

    AZs also have a code name. For example:

    - us-east-1a: an AZ in us-east-1 (Northern Virginia Region)

    - sa-east-1b: an AZ in sa-east-1 (São Paulo Region in South America)

    Note:
    - To keep your application available, maintain high availability and resiliency.
    - Use Region-scoped, managed services when possible.
    - If not, replicate workloads across multiple AZs to avoid failure from a single AZ.

6) **Security OF the cloud vs. security IN the cloud**

    AWS is responsible for security **OF** the cloud. This means AWS is required to protect and secure the infrastructure that runs all the services offered in the AWS Cloud. *Note: The level of responsibility AWS has depends on the service.*

    You’re responsible for security **IN** the cloud. When using any AWS service, you’re responsible for properly configuring the service and your applications, as well as ensuring your data is secure. *Note: The level of responsibility you have depends on the AWS service.*

    ![security_OF_IN_the_cloud](/resources/security_OF_IN_the_cloud.png)

    More at [AWS Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)

7) **AWS root user credentials**

    When you create an AWS account, you get a root user with full access to all services and resources. You sign in using the email and password you used to set up the account.

    AWS also provides access keys for programmatic access using the AWS CLI or API. These keys include an access key ID and a secret access key, like a username and password. 

    To ensure the safety of the root user:

    - Choose a strong password for the root user.

    - Never share your root user password or access keys with anyone.

    - Disable or delete the access keys associated with the root user.

    - Do not use the root user for administrative tasks or everyday tasks.

    - Enable MFA on your AWS root user. 

8) **What is IAM?**

    Amazon Identity and Access Management (IAM) is a web service that helps you securely control access to Amazon resources.

    Use IAM to set up other identities in addition to your root user, such as administrators, analysts, and developers, and grant them access to the resources they need to succeed in their tasks.

    More at [What is IAM?](https://docs.amazonaws.cn/en_us/IAM/latest/UserGuide/introduction.html)

9) **What is the principle of the least privilege?**
    
    Least privilege is a standard security principle that advises you to grant only the necessary permissions to do a particular job and nothing more. 

10) **What is IdP?**

    An Identity Provider (IdP) is a centralized system that manages user identities and controls access to multiple services. It allows employees to use a single set of credentials to log in to different systems, like AWS, Google Workspace, or other platforms. With an IdP, you can easily manage permissions, simplify user updates, and improve security by having one source of truth for all identities in your organization.