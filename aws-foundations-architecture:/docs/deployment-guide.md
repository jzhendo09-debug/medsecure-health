Deployment Guide

Purpose

This guide documents the deployment process used to build the MedSecure Health AWS Foundation environment.

⸻

Prerequisites

AWS Account
MFA-enabled root account
IAM administrative user
AWS Management Console access

⸻

Step 1 – Secure AWS Account

Actions performed:

Enabled MFA on the AWS root account
Created a dedicated IAM administrative user
Enabled MFA on the IAM administrative user
Reserved the root account for emergency use only

⸻

Step 2 – Create VPC

Resource:

VPC Name: medsecure-vpc
CIDR Block: 10.0.0.0/16

Purpose:

Provides a dedicated network environment for MedSecure Health resources.

⸻

Step 3 – Create Public Subnet

Resource:

Subnet Name: public-subnet-1
CIDR Block: 10.0.1.0/24

Purpose:

Hosts publicly accessible resources such as web servers.

⸻

Step 4 – Create Internet Gateway

Resource:

Internet Gateway Name: medsecure-igw

Actions:

Created Internet Gateway
Attached Internet Gateway to medsecure-vpc

Purpose:

Provides internet connectivity to resources within the VPC.

⸻

Step 5 – Configure Route Table

Resource:

Route Table Name: public-route-table

Actions:

Created route table
Added route:
Destination: 0.0.0.0/0
Target: Internet Gateway
Associated route table with public-subnet-1

Purpose:

Enables outbound internet access.

⸻

Step 6 – Configure Security Group

Resource:

Security Group Name: medsecure-web-sg

Inbound Rules:

HTTP (80) from 0.0.0.0/0
SSH (22) from My IP

Purpose:

Controls access to EC2 resources.

⸻

Step 7 – Deploy EC2 Instance

Resource:

Instance Name: medsecure-web-01
Operating System: Amazon Linux 2023
Instance Type: t3.micro

Actions:

Launched EC2 instance
Assigned Security Group
Verified successful deployment

Purpose:

Provides a web server platform for future application hosting.

⸻

Step 8 – Create S3 Bucket

Purpose:

Provides object storage for project resources and CloudTrail logs.

Actions:

Created S3 bucket
Enabled versioning

⸻

Step 9 – Enable CloudTrail

Resource:

Trail Name: medsecure-cloudtrail

Actions:

Enabled CloudTrail
Configured log delivery to Amazon S3
Verified event logging

Purpose:

Provides audit logging and activity monitoring.

⸻

Deployment Validation

The following validation steps were performed:

Verified IAM MFA configuration
Verified VPC deployment
Verified subnet deployment
Verified Internet Gateway attachment
Verified route table configuration
Verified Security Group rules
Verified EC2 instance status
Verified S3 bucket creation
Verified CloudTrail event logging

⸻

Deployment Outcome

A secure AWS foundation environment was successfully deployed to support future MedSecure Health cloud security projects.git