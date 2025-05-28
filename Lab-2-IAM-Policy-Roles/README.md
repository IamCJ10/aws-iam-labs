# Lab 02 – Custom IAM Policies

## Objective
Create and attach a custom IAM policy to enforce fine-grained permissions, and test those permissions through allowed and denied actions.

---

## Tools Used
- AWS Console
- IAM
- Amazon S3
- EC2 Instance (for testing via AWS CLI)

---

## Key Tasks Completed

### 1. Created a Custom IAM Policy
- Used the JSON editor to define specific actions (e.g., `s3:ListBucket`)
- Restricted access to a specific bucket: `arn:aws:s3:::iam-lab-test-bucket-cj2025`

### 2. Attached Policy to IAM User
- Attached the custom policy to IAM user `john.doe`
- Removed any broader permissions for clean testing

### 3. Verified Permissions (Access Denied)
- Ran `aws s3 cp` to upload a file
- Received `AccessDenied` (as expected) due to missing `s3:PutObject`

### 4. Updated Policy with Additional Actions
- Added `s3:PutObject` for `arn:aws:s3:::iam-lab-test-bucket-cj2025/*`
- Re-tested and successfully uploaded file via CLI

---

## What I Learned

- How to write custom IAM policies in JSON format
- Importance of specifying both **bucket-level** and **object-level** permissions in S3
- How AWS uses **policy evaluation logic** (explicit deny > allow)
- Testing policies through real CLI actions helps validate security boundaries
- How IAM supports **least privilege** and secure access by design

---

## Screenshots
- `custom-policy-json.png` – Custom policy created in JSON editor
- `policy-attached-to-user.png` – IAM user with custom policy attached
- `denied-access-test.png` – Proof of denied access before permission update
- `allowed-access-test.png` – Successful test after updating policy

---

## Next Lab
[Lab 03 – MFA and Password Policies](../lab-03-mfa-password-policy/README.md)

