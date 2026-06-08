Threat Model
Purpose
This document identifies key assets, potential threats, and security controls implemented within the MedSecure Health AWS Foundation environment.


⸻


Environment Overview
The MedSecure Health AWS Foundation environment consists of:
AWS Account
IAM Administrative User
Amazon VPC
Public Subnet
Security Groups
Amazon EC2
Amazon S3
AWS CloudTrail


⸻


Threat Analysis
Asset
Potential Threat
Security Control
AWS Root Account
Unauthorized access
MFA enabled, emergency use only
IAM Administrative User
Credential compromise
MFA enabled
Amazon EC2 Instance
Unauthorized SSH access
Security Group restricted to My IP
Amazon EC2 Instance
Internet-based attacks
Security Group filtering
Amazon S3 Bucket
Accidental deletion or modification
Versioning enabled
CloudTrail Logs
Lack of visibility into account activity
CloudTrail enabled
VPC Resources
Unrestricted network access
Security Groups and routing controls
AWS Environment
Unauthorized configuration changes
IAM controls and CloudTrail auditing


⸻


Security Assumptions
The following assumptions apply:
MFA remains enabled on privileged accounts.
Administrative credentials are protected.
Security Groups are reviewed before production deployment.
CloudTrail remains enabled.
AWS best practices continue to be followed.


⸻


Residual Risks
The following risks remain:
Public-facing resources may be exposed to internet-based attacks.
Misconfigured Security Groups could increase exposure.
Compromised administrator credentials could impact resources.
Human error may result in configuration mistakes.


⸻


Risk Mitigation Strategy
The MedSecure Health environment reduces risk through:
Least Privilege
Multi-Factor Authentication
Logging and Auditing
Security Group Access Controls
S3 Versioning
Documentation and Change Tracking


⸻


Future Improvements
Future projects will further reduce risk through:
AWS Security Hub
Amazon GuardDuty
CloudWatch Monitoring
Infrastructure as Code (Terraform)
Automated Security Scanning
Disaster Recovery Controls
