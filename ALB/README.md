---

# CloudFormation Template for Application Load Balancer

This template provisions an Application Load Balancer (ALB) with listeners and a target group.

## Parameters

- **AcmCertificate**: ARN of the AWS Certification Manager's Certificate.
- **ExportVpcStackName**: Name of the VPC stack exporting values.

## Resources

- **ApplicationLoadBalancer**: ALB named `MyApplicationLoadBalancer`.
- **ALBListenerNoSslCertificate**: HTTP listener on port 80, redirects to HTTPS.
- **ALBListenerSslCertificate**: HTTPS listener on port 443 with ACM certificate.
- **ALBTargetGroup**: Target group for web servers.

## Outputs

- **ALBTargetGroup**: Exported as `ALBTargetGroup`.
- **ApplicationLoadBalancerDnsName**: Exported as `ApplicationLoadBalancerDnsName`.
- **ApplicationLoadBalancerZoneID**: Exported as `ApplicationLoadBalancerZoneID`.

## Usage

1. Update parameter values in the template or during stack creation.
2. Deploy the template via AWS Management Console, AWS CLI, or SDK.

### AWS CLI Example

```sh
aws cloudformation create-stack --stack-name MyALBStack --template-body file://alb.yaml --parameters \
ParameterKey=AcmCertificate,ParameterValue=your_certificate_arn \
ParameterKey=ExportVpc