---

# CloudFormation Template for NAT Gateways and Elastic IPs

This CloudFormation template creates two NAT Gateways placed in public subnet 1 and 2, with specific routing configurations to direct internet traffic to and from private subnets 1, 2, 3, and 4. It also creates Elastic IPs and public route tables to facilitate this routing.

## Template Overview

### Resources Created

1. **Public Subnets**:
   - Subnet 1 (for NAT Gateway 1)
   - Subnet 2 (for NAT Gateway 2)

2. **Private Subnets**:
   - Subnet 3 (for private traffic routed through NAT Gateway 1)
   - Subnet 4 (for private traffic routed through NAT Gateway 2)

3. **NAT Gateways**:
   - NAT Gateway 1 (in Public Subnet 1)
   - NAT Gateway 2 (in Public Subnet 2)

4. **Elastic IPs**:
   - Elastic IP 1 (attached to NAT Gateway 1)
   - Elastic IP 2 (attached to NAT Gateway 2)

5. **Public Route Tables**:
   - Route Table 1 (for Public Subnet 1)
   - Route Table 2 (for Public Subnet 2)

### Routing Configuration

- **Public Route Table 1**:
  - Routes traffic from Private Subnet 1 and Private Subnet 3 to NAT Gateway 1.

- **Public Route Table 2**:
  - Routes traffic from Private Subnet 2 and Private Subnet 4 to NAT Gateway 2.

## Usage

1. **Deploy the Template**:
   - Use AWS CloudFormation to deploy this template in your AWS account.

2. **Parameters**:
   - The template may require parameters such as VPC ID, Subnet IDs, etc., depending on your AWS environment.

3. **Configuration**:
   - Customize the template as per your specific network architecture and requirements.

## Important Notes

- Ensure that your AWS account has the necessary permissions to create and manage these resources.
- Review and modify the template's parameters and configurations as needed for your environment.

---

