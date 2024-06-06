Certainly! Here's an updated version of the README with additional information about the CloudFormation template:

---

# CloudFormation Template: VPC with Public and Private Subnets

This CloudFormation template automates the creation of a Virtual Private Cloud (VPC) in AWS with two public subnets and four private subnets. The subnets are distributed across two availability zones for high availability and fault tolerance.

## Features

- **VPC Configuration**: Creates a VPC with specified CIDR block and enables DNS support and DNS hostnames.
- **Public Subnets**: Sets up two public subnets in one availability zone and another public subnet in a different availability zone. Each public subnet has an associated Internet Gateway for internet access.
- **Private Subnets**: Creates four private subnets, with two in each availability zone. The private subnets do not have direct internet access and route traffic through a NAT Gateway for outbound connectivity.
- **Route Tables**: Creates route tables for the public subnets and associates them with the Internet Gateway for internet access.
- **Application Load Balancer**: Configures an Application Load Balancer (ALB) to distribute incoming traffic across EC2 instances in the public subnets.
- **Security Groups**:
  - Webserver Security Group: Controls inbound and outbound traffic for the instance acting as the web server.
  - Bastion Host Security Group: Allows SSH access to the instance acting as the bastion host from specific IP addresses.
  - Database Security Group: Manages inbound and outbound traffic for the instance acting as the database server.
  - Load Balancer Security Group: Defines rules for the Application Load Balancer to manage traffic.

## Usage

1. **Deploying the Template**:
   - Go to the AWS CloudFormation console.
   - Click on "Create stack" and choose "With new resources (standard)".
   - Upload or paste the contents of this CloudFormation template.
   - Configure parameters as required (e.g., VPC CIDR block, subnet CIDR blocks, etc.).
   - Review and create the stack.

2. **Accessing Resources**:
   - After the stack creation is complete, access the Application Load Balancer's DNS name to access your application.
   - Use the bastion host for SSH access to instances in private subnets.
   - Update Security Groups and Network ACLs as needed to allow or restrict traffic.

3. **Cleaning Up**:
   - To avoid incurring charges, delete the CloudFormation stack when the resources are no longer needed.
   - Go to the AWS CloudFormation console, select the stack, and choose "Delete stack."

## Requirements

- AWS account with the necessary permissions to create VPCs, subnets, Internet Gateways, NAT Gateways, Security Groups, Load Balancers, and EC2 instances.
- Basic understanding of AWS networking concepts such as VPC, subnets, routing, security groups, and load balancers.

## Additional Notes

- This template is designed for demonstration and educational purposes. Modify the template and resource configurations as per your specific requirements and security best practices.
- Always review and test CloudFormation templates in a non-production environment before deploying them in production.

For detailed information about the resources created by this template and their configurations, refer to the CloudFormation template file and AWS documentation.

---

This README now includes information about the Application Load Balancer and the additional security groups for the various EC2 instances in your architecture.