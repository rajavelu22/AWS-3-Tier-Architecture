# AWS-3-Tier-Architecture

AWS 3-Tier Application Setup
Overview :
This project involves setting up a highly scalable and secure 3-tier architecture on AWS, leveraging various cloud services to ensure high availability, fault tolerance, and security. The architecture is divided into three distinct layers:



1.Web Tier (Public Subnet):
          •	This tier consists of EC2 instances hosting the frontend of the application.
          •	It is placed in a public subnet, allowing users to access the application via the internet.
          •	An Application Load Balancer (ALB) distributes incoming requests efficiently.
          •	A Security Group (SG) is configured to allow only HTTP/HTTPS traffic from the internet.



2.Application Tier (Private Subnet):
•	This layer contains the backend application logic running on EC2 instances.
•	It resides in a private subnet, making it inaccessible from the public internet, improving security . The application code is uploaded to an S3 bucket, and EC2 instances pull the latest version from there.
•	Communication between the web and app tiers happens via the Internal Load Balancer, ensuring seamless traffic distribution, IAM roles are used to provide EC2 instances access to S3, minimizing unnecessary exposure.



3.Database Tier (Private Subnet):
•	This layer consists of an Amazon RDS instance for structured data storage.
•	It is placed in a private subnet to prevent direct access from the internet.
•	Only the Application Tier has permissions to connect to the database.
•	Due to AWS Free Tier limits, RDS is deployed in a single availability zone instead of a multi-AZ setup.
          AWS Services Used:
          •	VPC – For secure network isolation.
          •	EC2 – Hosting application servers.
          •	IAM – Managing secure access and permissions.
          •	S3 – Storing application assets and backups.
          •	RDS – Managed database service for reliable data storage.
          •	Certificate Manager – Enabling secure HTTPS communication.
          Load Balancing for High Availability:
          To enhance fault tolerance and distribute traffic efficiently, we integrate load balancers at different tiers:
          •	Internal Load Balancer: Balances traffic within the Application Tier.
          •	External Load Balancer: Ensures public accessibility and improves fault tolerance.
                ⚠ Note: Due to free-tier limitations, RDS will be deployed in a single availability zone. This structured approach ensures a cost-effective yet production-ready                                      environment, ideal for deployment and scalability.
          
          
          
Setup Components :
          1. Building Your Own Space: Virtual Private Cloud (VPC)
          o	Creation: Establish a VPC to provide an isolated network environment, serving as the foundation for all resources.
          o	Subnets: Configure public subnets for the Web Tier and private subnets for the Application and Database Tiers to enhance security and control.

          
2. Amazon S3 and IAM Configuration:
          o	S3 Bucket: Create an S3 bucket to store and manage application code, facilitating easy deployment and version control.
          o	IAM Roles and Policies: Set up IAM roles with appropriate policies to grant EC2 instances secure access to the S3 bucket, ensuring controlled permissions and adherence to the             principle of least privilege.


   
4. Setting Up Your Database: Amazon RDS
          o	Amazon RDS Instance: Launch and configure an RDS instance within the private subnet to serve as the backend database, ensuring data is securely stored and managed.
          o	Security Groups: Define security groups to allow traffic only from the Application Tier, preventing unauthorized access and enhancing data security.


   
4.Application Tier Setup:
          o	EC2 Instances: Deploy EC2 instances in the private subnet to run the application logic, ensuring they are not directly accessible from the internet.
          o	Internal Load Balancer: Configure an internal load balancer to distribute traffic evenly among application instances, promoting high availability and reliability.



5.Web Tier Setup:
          o	EC2 Instances: Provision EC2 instances in the public subnet to handle incoming user traffic and serve static content.
          o	External Load Balancer: Set up an external load balancer to manage and distribute incoming traffic from users, ensuring seamless access and improved performance.



Project Credits: This project was built with the help of https://github.com/KastroVKiran/3TierArchitectureApp this GitHub repository . I acknowledge and appreciate the original work as a reference for my implementation.
