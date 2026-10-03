# AWS IAM – User Access Management and EC2 Permission Control

## 📌 Overview

This project demonstrates the implementation of AWS Identity and Access Management (IAM) for controlling user access to Amazon EC2 resources using custom IAM policies and groups.

The implementation follows the principle of **least privilege**, where different users receive only the permissions required for their roles.

## 🎯 Objectives

- Create custom IAM policies for EC2 access.
- Create IAM groups for different access levels.
- Create IAM users and assign them to appropriate groups.
- Control EC2 permissions using resource-level access.
- Test and verify permissions using the IAM Policy Simulator.

## 🛠️ AWS Services Used

- AWS IAM
- Amazon EC2
- IAM Policy Simulator

## 👥 IAM Access Structure

### Read-Only User

The read-only user can:

- View EC2 instances.
- View EC2 instance status.
- View EC2 tags.

The user **cannot**:

- Start EC2 instances.
- Stop EC2 instances.
- Terminate EC2 instances.

### Operator User

The operator user can:

- View EC2 instances.
- View EC2 instance status.
- View EC2 tags.
- Start the designated EC2 instance.
- Stop the designated EC2 instance.

The operator user **cannot** terminate the EC2 instance.

## 🔐 Custom IAM Policies

Two customer-managed policies were created:

1. `veda-ec2-readonly-policy`
2. `veda-ec2-operator-policy`

The operator policy uses a specific EC2 instance ARN for StartInstances and StopInstances permissions, demonstrating resource-level access control.

## 🧪 Permission Testing

AWS IAM Policy Simulator was used to verify the permissions of both users.

The tests confirmed:

| Permission | Read-Only User | Operator User |
|---|---|---|
| DescribeInstances | Allowed | Allowed |
| StartInstances | Denied | Allowed |
| StopInstances | Denied | Allowed |
| TerminateInstances | Denied | Denied |

## 📂 Project Structure

```text
veda-task3-aws-iam/
│
├── README.md
│
├── policies/
│   ├── veda-ec2-readonly-policy.json
│   └── veda-ec2-operator-policy.json
│
└── screenshots/
    └── AWS IAM implementation screenshots

```
## 📸 Implementation Evidence

Screenshots included in this repository document:

- EC2 test instance
- Custom IAM policies
- IAM groups
- IAM user assignments
- IAM policy permissions
- Policy Simulator results
- EC2 permission restrictions

## ✅ Conclusion

This task demonstrates how AWS IAM can be used to implement role-based access control for EC2 resources. Custom policies, groups, and users were configured and their permissions were verified using the IAM Policy Simulator.
