# RDS Database Instance Creation Template

This repository contains an `rds.yaml` CloudFormation template to create an Amazon RDS instance within private subnets 3 and 4, ensuring the instance is not publicly accessible.

## Contents

- `rds.yaml`: CloudFormation template.

## Prerequisites

1. **AWS Account** with necessary permissions.
2. **VPC** with private subnets 3 and 4.
3. **IAM Role** with required permissions.

## Parameters

- **DBInstanceIdentifier**: Unique identifier for the RDS instance.
- **DBInstanceClass**: Instance type (e.g., db.t3.medium).
- **DBName**: Initial database name.
- **MasterUsername**: Master username.
- **MasterUserPassword**: Master user password.
- **VpcId**: VPC ID.
- **SubnetId1**: ID of Subnet 3.
- **SubnetId2**: ID of Subnet 4.

## Deployment

### Using AWS CLI

1. Clone the repository:
    ```bash
    git clone https://github.com/your-repo-url.git
    cd your-repo-directory
    ```

2. Deploy the stack:
    ```bash
    aws cloudformation create-stack --stack-name my-rds-stack --template-body file://rds.yaml --parameters ParameterKey=DBInstanceIdentifier,ParameterValue=mydbinstance ParameterKey=DBInstanceClass,ParameterValue=db.t3.medium ParameterKey=DBName,ParameterValue=mydatabase ParameterKey=MasterUsername,ParameterValue=admin ParameterKey=MasterUserPassword,ParameterValue=yourpassword ParameterKey=VpcId,ParameterValue=vpc-xxxxxxx ParameterKey=SubnetId1,ParameterValue=subnet-xxxxxxxx ParameterKey=SubnetId2,ParameterValue=subnet-yyyyyyyy
    ```

### Using AWS Management Console

1. Navigate to CloudFormation.
2. Create a new stack with `rds.yaml`.
3. Follow the prompts to specify details and parameter values.
4. Create the stack.

## Cleanup

To delete the resources:

### Using AWS CLI

```bash
aws cloudformation delete-stack --stack-name my-rds-stack
```

### Using AWS Management Console

1. Navigate to CloudFormation.
2. Select the stack.
3. Click "Delete".

## Support

For issues or questions, open an issue in this repository or contact [Support].

## License

This project is licensed under the MIT License. See the LICENSE file for details.