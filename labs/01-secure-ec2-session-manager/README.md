# Secure EC2 Administration with IAM and Session Manager

## Objective

Securely administer an Amazon EC2 instance without permanent access keys, SSH keys, or publicly exposed management ports.

## Environment

- Amazon EC2
- Amazon Linux 2023
- AWS Identity and Access Management
- AWS Systems Manager Session Manager
- AWS Security Token Service
- EC2 security groups

## Implementation

1. Deployed an Amazon Linux EC2 instance named `AWS-CYBERLAB-SERVER01`.
2. Created the IAM role `EC2-CyberLab-SSM-Role`.
3. Configured EC2 as the role’s trusted AWS service.
4. Attached the `AmazonSSMManagedInstanceCore` policy.
5. Attached the role to the running EC2 instance.
6. Verified that the SSM agent registered and became available.
7. Connected through Systems Manager Session Manager.
8. Used `aws sts get-caller-identity` to verify temporary assumed-role credentials.
9. Removed the security-group rule exposing SSH port 22 to `0.0.0.0/0`.
10. Confirmed that Session Manager access continued with zero inbound rules.

## Validation

The EC2 instance successfully assumed `EC2-CyberLab-SSM-Role` and remained manageable through Session Manager after all inbound security-group rules were removed.

## Security Outcomes

- Applied least-privilege access
- Eliminated permanent credentials from the EC2 instance
- Removed public SSH exposure
- Reduced the external attack surface
- Implemented IAM-based, auditable administrative access

## Résumé Bullet

- Secured an Amazon EC2 instance by implementing a least-privilege IAM role with AWS Systems Manager Session Manager, validating temporary STS credentials, and eliminating public SSH exposure by removing the port 22 inbound rule.
