---

# CloudFormation Templates for ALB and EC2 Instances

This folder contains two CloudFormation templates:

1. **alb-ec2.yaml**: Creates an Application Load Balancer and two EC2 instances, adding the instances to the ALB's target group.
2. **ec2-reference.yaml**: A reference template for creating an EC2 instance.

## Templates Overview

### alb-ec2.yaml

This template provisions:
- An Application Load Balancer (ALB).
- Two EC2 instances.
- Associates the EC2 instances with the ALB's target group.

#### Parameters

- **AcmCertificate**: ARN of the ACM Certificate.
- **ExportVpcStackName**: Name of the VPC stack exporting the values.

### ec2-reference.yaml

This template serves as a reference for creating an EC2 instance. It can be used independently or as a modular component in other CloudFormation stacks.

## Usage

1. **Update the parameter values** as needed in both templates.
2. **Deploy the templates** using the AWS Management Console, AWS CLI, or SDK.

### AWS CLI Example for alb-ec2.yaml

```sh
aws cloudformation create-stack --stack-name MyALBEC2Stack --template-body file://alb-ec2.yaml --parameters \
ParameterKey=AcmCertificate,ParameterValue=your_certificate_arn \
ParameterKey=ExportVpcStackName,ParameterValue=your_vpc_stack_name
```

### AWS CLI Example for ec2-reference.yaml

```sh
aws cloudformation create-stack --stack-name MyEC2ReferenceStack --template-body file://ec2-reference.yaml
```
