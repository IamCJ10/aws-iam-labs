# Lab 01 – IAM Users, Groups, and Roles with EC2 Role Access

## Description
This lab demonstrates identity management in AWS using the IAM console and EC2. It simulates real-world user provisioning and role-based access control, following best practices for cloud security.

## Objective
Build foundational IAM skills by creating a secure access structure using IAM users, groups, policies, and roles. Then validate role-based access by launching an EC2 instance with read-only access to Amazon S3.

---

## Tools Used
- AWS Console
- EC2 Instance Connect
- AWS IAM
- Amazon S3
- AWS CLI

---

## Key Tasks Completed

### 1. IAM User Creation
- Created a new IAM user: `john.doe`
- Granted programmatic and console access
- Assigned user to a new IAM group: `Developers`

### 2. IAM Group & Policy
- Created an IAM group: `Developers`
- Attached **AmazonS3ReadOnlyAccess** policy
- This ensures the user inherits read-only access to S3 through the group

### 3. IAM Role for EC2
- Created a role named `EC2_S3_ReadOnlyRole`
- Selected **EC2** as the trusted service
- Attached **AmazonS3ReadOnlyAccess** to the role
- Purpose: Allow EC2 instances to access S3 securely without long-term credentials

### 4. EC2 Launch and Role Assignment
- Launched an Amazon Linux 2 EC2 instance (`t2.micro`)
- Attached the `EC2_S3_ReadOnlyRole` IAM role at launch
- Connected to the instance via **EC2 Instance Connect**

### 5. Test IAM Role via CLI
- Ran: `aws s3 ls`
- Successfully listed accessible S3 buckets
- Confirmed IAM role permissions were applied correctly to the EC2 instance

### 6. S3 Bucket Creation
- Created test bucket: `iam-lab-test-bucket-cj2025`
- Verified its visibility from EC2 instance using AWS CLI

---

## What I Learned

- How to securely manage users and groups using IAM
- The difference between **user-based** and **role-based** access
- How to create and attach **managed policies**
- How to assign **IAM roles to EC2 instances**
- How to test access securely using **AWS CLI**
- Importance of **least privilege** and separation of duties in IAM
- Basic use of **EC2 Instance Connect** for testing cloud services
- Confirmed how role-based credentials work without needing access keys

---

## Screenshots
Include screenshots of:
- IAM user and group setup
- IAM role summary page
- EC2 instance with role attached
- EC2 terminal showing successful `aws s3 ls` output

---

## Next Lab
[Lab 02 – Custom IAM Policies](../lab-02-custom-iam-policies/README.md)
