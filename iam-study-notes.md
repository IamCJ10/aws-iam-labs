# IAM – Identity and Access Management

## What is IAM?

IAM (Identity and Access Management) is a **free AWS security service** that helps you **control who can access AWS**, what actions they can perform, and **on which resources**.

---

## Core Components

| Component | Description | Strategic Use |
|-----------|-------------|---------------|
| **IAM User** | Represents a person or app needing long-term credentials | Ideal for developers, CLI users |
| **IAM Group** | A set of users with shared permissions | Use for Role-Based Access Control (RBAC) |
| **IAM Role** | Identity assumed temporarily by services or users | For EC2, Lambda, or cross-account setups |
| **Policy** | JSON document that defines permissions | Attached to users, groups, or roles |

---

## AWS Policy Evaluation Logic

AWS evaluates permissions in this order:

1. **Explicit Deny** → Always wins. Stops evaluation immediately.
2. **Organization SCPs** → Evaluated next if using AWS Organizations.
3. **Resource-based Policies** → Checked for resource-level permissions.
4. **Identity-based Policies** → Attached to users, groups, or roles.
5. **IAM Permissions Boundaries** → Limits max permissions an identity can have.
6. **Session Policies** → Scoped down permissions for assumed roles.

### Policy Evaluation Scenarios

| Scenario | Result | Reason |
|----------|--------|--------|
| User + Group = Allow | ✅ Allowed | Permissions merge |
| One Deny anywhere | ❌ Denied | Deny > Allow |
| No matching policy | ❌ Denied | Default = deny |
| Group allows, user denies | ❌ Denied | Deny always wins |

---

## Section 3: AWS Architect Pro Tips

### Decision-Making Table

| Situation | Best Practice |
|-----------|---------------|
| EC2 needs S3 access | Attach IAM Role to EC2 |
| 5 devs need same permissions | Create Group + Policy |
| Root user login | Lock, MFA, never use |
| Temporary access to another account | Cross-account Role |
| Prevent bucket deletion | Explicit deny in policy |

---

## Hidden Traps (Exam Alert!)

- **User Data doesn't run** → Forgot `#!/bin/bash`
- **Access key leaked** → Rotate + use roles instead
- **Implicit deny ≠ Explicit deny** → Know the difference
- **IAM User + Role = different animals** — don't confuse them

---

## IAM Core Concepts (Architect View)

