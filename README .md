# Multi-AZ Scalable Website Infrastructure on AWS

## Project Overview

Deployed the **Kawaii Spatial Diorama (`2171_spatial_diorama`)** website on AWS using Nginx, an Application Load Balancer, and an Auto Scaling Group. The infrastructure was configured through the AWS Management Console in the Mumbai region (`ap-south-1`).

## AWS Services Used

- Amazon VPC
- Public and private subnets
- Internet Gateway
- NAT Gateway
- Route tables
- Amazon EC2
- Amazon Machine Image (AMI)
- Launch Template
- Application Load Balancer (ALB)
- Target Group and health checks
- Auto Scaling Group
- Security Groups

## Implementation

1. Created a custom VPC named `multi-az-vpc` with CIDR `10.0.0.0/16`.
2. Created two public and two private subnets across two Availability Zones.
3. Created and attached an Internet Gateway.
4. Configured public and private route tables.
5. Created a NAT Gateway to provide outbound internet access to private instances.
6. Launched a temporary Ubuntu EC2 instance and installed Nginx.
7. Deployed the `2171_spatial_diorama` website and verified it in a browser.
8. Created an AMI named `spatial-diorama-ami` from the configured website instance.
9. Created a Launch Template using the AMI.
10. Created an Application Load Balancer and configured its target group.
11. Created an Auto Scaling Group named `multi-az-asg` across two Availability Zones.
12. Accessed the website successfully using the ALB DNS name.
13. Verified that all three registered targets were healthy.
14. Tested automatic scale-out. The Auto Scaling Group successfully increased capacity from one to two instances and then from two to three instances.

## Verification

- Website accessible through the ALB DNS name.
- Target group showed three healthy targets.
- Auto Scaling Activity History showed successful EC2 instance launches triggered by the target-tracking scaling policy.
- Auto Scaling Group reached its configured desired capacity of three instances.

## Region

`ap-south-1` — Asia Pacific (Mumbai)

## Implementation Method

AWS Management Console

## Screenshots

Project screenshots are available in the `screenshots/` directory.

- `alb-website.png`
- `vpc-resource-map.png`
- `target-group-healthy.png`
- `autoscaling-scale-out.png`
- `autoscaling-configuration.png`
