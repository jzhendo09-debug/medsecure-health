# Security Findings Analysis

## Finding 1

### Description

**VPC default security groups should not allow inbound or outbound traffic**

Security Hub detected that the default security group in the VPC allows network traffic. Default security groups are automatically created with every VPC and often allow communication between resources assigned to the same security group.

### Risk

Default security groups are commonly overlooked and can unintentionally permit communication between resources. Attackers who gain access to one resource may be able to move laterally to other systems within the VPC.

### Investigation

The default security group associated with the MedSecure Health VPC was reviewed to identify any unnecessary inbound and outbound rules. Security Hub flagged the configuration because it did not align with AWS security best practices.

### Remediation

Reviewed the default security group configuration and removed unnecessary rules. Future EC2 instances will use dedicated security groups based on least-privilege principles rather than the default security group.

---

## Finding 2

### Description

**EC2 subnets should not automatically assign public IP addresses**

Security Hub detected that one or more subnets are configured to automatically assign public IP addresses to newly launched EC2 instances.

### Risk

Automatically assigning public IP addresses increases the attack surface by exposing instances directly to the internet. Publicly accessible systems are more susceptible to scanning, exploitation attempts, and unauthorized access.

### Investigation

Subnet configurations were reviewed to determine whether public IP assignment was enabled by default. The finding indicated that newly launched EC2 instances could receive public IP addresses without requiring manual configuration.

### Remediation

Reviewed subnet settings and documented the recommendation to disable automatic public IP assignment for production workloads. Future infrastructure deployments will use private networking wherever possible.

---

## Finding 3

### Description

**S3 general purpose buckets should require requests to use SSL**

Security Hub detected that S3 buckets do not enforce encrypted connections using SSL/TLS.

### Risk

Without SSL enforcement, data could potentially be transmitted over unencrypted connections, increasing the risk of interception or unauthorized disclosure of sensitive healthcare-related information.

### Investigation

S3 bucket configurations were reviewed to determine whether bucket policies enforced HTTPS-only access. Security Hub identified that SSL enforcement controls were not configured.

### Remediation

Reviewed S3 bucket configurations and implemented plans to enforce HTTPS-only access through bucket policies. Encryption in transit was identified as a required security control for all future S3 resources.