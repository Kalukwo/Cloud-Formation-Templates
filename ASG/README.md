# Auto Scaling Group CloudFormation Template

This CloudFormation template creates an Auto Scaling Group along with necessary resources such as an EC2 Launch Template, SNS Topic for notifications, and CloudWatch Alarms for scaling policies.

## Template Details

### Parameters

- **ExportVpcStackName**: The name of the VPC stack that exports values.
- **ExportAlbStackName**: The name of the ALB stack that exports values.
- **OperatorEMail**: A valid email address to notify if there are any scaling operations.
- **EC2KeyName**: Name of an EC2 KeyPair to enable SSH access to the instance. Must be the name of an existing EC2 KeyPair.
- **EC2ImageID**: The ID of the custom AMI.
- **WebServerLaunchTemplateName**: Name of the launch template. Must be unique to this account. Max 128 chars. No spaces or special characters like '&', '*', '@'.
- **InstanceType**: EC2 instance type for the web servers. Allowed values are `t2.nano`, `t2.micro`, `t2.small`, `t2.medium`. Default is `t2.micro`.

### Resources

1. **WebServerLaunchTemplate**: Creates an EC2 Launch Template using the specified AMI, instance type, and key pair.
2. **NotificationTopic**: Creates an SNS Topic for sending notifications to the provided email address.
3. **WebServerAutoScalingGroup**: Creates an Auto Scaling Group with the specified configurations including VPC subnets, health check type, launch template, scaling policies, and target group.
4. **WebServerScaleUpPolicy**: Creates a scaling policy to scale up the instances when certain conditions are met.
5. **WebServerScaleDownPolicy**: Creates a scaling policy to scale down the instances when certain conditions are met.
6. **CPUAlarmHigh**: Creates a CloudWatch Alarm to trigger the scale-up policy when the CPU utilization is greater than 70% for 10 minutes.
7. **CPUAlarmLow**: Creates a CloudWatch Alarm to trigger the scale-down policy when the CPU utilization is less than 70% for 10 minutes.

## Usage

### Prerequisites

- Ensure that the VPC and ALB stacks are created and have the necessary exports.
- Ensure that you have a valid EC2 KeyPair for SSH access to the instances.
- Ensure that you have a valid AMI ID for the instances.

### Deployment

1. Navigate to the CloudFormation console.
2. Create a new stack using this template.
3. Provide the required parameters:
   - `ExportVpcStackName`
   - `ExportAlbStackName`
   - `OperatorEMail`
   - `EC2KeyName`
   - `EC2ImageID`
   - `WebServerLaunchTemplateName`
   - `InstanceType`

4. Deploy the stack.

### Outputs

- **WebServerLaunchTemplate**: The EC2 Launch Template used by the Auto Scaling Group.
- **NotificationTopic**: The SNS Topic used for scaling notifications.
- **WebServerAutoScalingGroup**: The Auto Scaling Group managing the web server instances.
- **WebServerScaleUpPolicy**: The scaling policy for scaling up instances.
- **WebServerScaleDownPolicy**: The scaling policy for scaling down instances.
- **CPUAlarmHigh**: The CloudWatch Alarm for high CPU utilization.
- **CPUAlarmLow**: The CloudWatch Alarm for low CPU utilization.

## Notes

- Ensure that the VPC and ALB stacks are correctly configured to export the necessary values used in this template.
- Modify the template parameters and resource properties as needed to fit your specific requirements.