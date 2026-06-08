Security Decisions

Purpose

This document records the key security decisions made during the deployment of the MedSecure Health AWS Foundation environment.

The objective is to provide justification for security controls and demonstrate security-focused decision making throughout the project.

⸻

Root Account Protection

Decision

The AWS root account was secured using Multi-Factor Authentication (MFA) and is reserved for emergency administrative tasks only.

Justification

The root account has unrestricted access to all AWS resources. Restricting its use reduces the risk of accidental or unauthorized changes.

Security Benefit

Reduces attack surface
Supports AWS security best practices
Limits privileged account exposure

⸻

IAM Administrative User

Decision

A dedicated IAM administrative user was created for daily administration tasks.

Justification

Routine administration should not be performed using the root account.

Security Benefit

Improved accountability
Supports audit logging
Reduces reliance on root credentials

⸻

Multi-Factor Authentication (MFA)

Decision

MFA was enabled for the IAM administrative user.

Justification

Passwords alone may be compromised through phishing, credential reuse, or brute-force attacks.

Security Benefit

Provides an additional authentication factor
Reduces risk of unauthorized account access

⸻

VPC Network Isolation

Decision

Resources were deployed inside a dedicated Amazon VPC.

Justification

A custom VPC provides greater control over networking, routing, and security boundaries.

Security Benefit

Logical network separation
Improved traffic control
Foundation for future segmentation

⸻

Security Group Access Controls

Decision

Security Groups were configured to allow:

HTTP (Port 80)
SSH (Port 22) from My IP

Justification

Administrative access should be restricted to authorized users whenever possible.

Security Benefit

Supports least-privilege access
Reduces unauthorized network access

⸻

CloudTrail Logging

Decision

AWS CloudTrail was enabled for account activity monitoring.

Justification

CloudTrail provides visibility into administrative actions and resource changes.

Security Benefit

Improved auditing
Security event investigation capability
Compliance support

⸻

S3 Versioning

Decision

Versioning was enabled on the S3 bucket used for project storage.

Justification

Versioning protects against accidental deletion or modification of stored objects.

Security Benefit

Data recovery capability
Protection against accidental changes

⸻

Security Philosophy

The MedSecure Health environment follows the following security principles:

Least Privilege
MFA Everywhere
Secure by Default
Logging and Auditing
Defense in Depth
Documentation First