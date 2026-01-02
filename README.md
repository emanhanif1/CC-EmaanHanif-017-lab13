# Lab 13 – Terraform IAM Management with AWS

## 📌 Overview

This lab focuses on managing AWS IAM resources using Terraform inside a GitHub Codespace environment. The lab covers IAM groups, users, policies, login profiles, access keys, Terraform remote state using S3, and dynamic user creation from CSV files.

All tasks were completed using **Terraform**, **AWS CLI**, and **GitHub CLI (GH CLI)** inside a **Linux-based GitHub Codespace**.



---

## 🧰 Tools & Technologies

* Terraform
* AWS CLI
* GitHub CLI (GH CLI)
* GitHub Codespaces (Linux)
* AWS IAM & S3

---

##  Repository Structure

```
Lab13/
├── main.tf
├── variables.tf
├── locals.tf
├── users.csv
├── create-login-profile.sh
└── terraform.tfstate (remote – S3)
```

---

## 📝 Tasks Summary

### Task 0 – Lab Setup (Codespace & GH CLI)

* Created a GitHub repository and Codespace using GH CLI
* Connected to the Codespace via SSH
* All commands were executed inside the Codespace environment

---

### Task 1 – Create IAM Group and Output Details

* Created an IAM group named `developers`
* Output group name, ARN, and unique ID using Terraform outputs
* Verified the group in AWS Console

---

### Task 2 – Create IAM User with Group Membership

* Created an IAM user named `loadbalancer`
* Added the user to the `developers` group
* Output user details using Terraform
* Verified user and group membership in AWS Console

---

### Task 3 – Attach Policies to IAM Group

* Attached AWS managed policies to the `developers` group:

  * AmazonEC2FullAccess
  * IAMUserChangePassword
* Verified attached policies in AWS Console

---

### Task 4 – Create Login Profile for IAM User

* Created a Bash script to create IAM login profiles
* Used `null_resource` with `local-exec` provisioner
* Generated a login profile for the `loadbalancer` user
* Verified login via AWS CLI and AWS Console

---

### Task 5 – Generate Access Keys for IAM User

* Generated IAM access keys for the `loadbalancer` user
* Output access key ID and secret (marked as sensitive)
* Verified access keys in Terraform state and AWS Console

---

### Task 6 – Implement Terraform Remote State with S3

* Created an S3 bucket with versioning enabled
* Configured Terraform S3 backend for remote state storage
* Migrated local state to S3 using `terraform init -migrate-state`
* Verified state file in S3
* Destroyed resources and confirmed state updates in S3

---

### Task 7 – Create Multiple Users from CSV File

* Created `users.csv` containing multiple user names
* Used `csvdecode()` and `for_each` to dynamically create users
* Added all users to the `developers` group
* Generated login profiles and access keys for each user
* Verified users, group membership, and access keys in AWS Console

---

##  Cleanup

* Destroyed all Terraform-managed resources
* Verified deletion of users and groups in AWS Console
* Confirmed empty/updated Terraform state in S3
* (Optional) Deleted S3 bucket after cleanup

---

✅ Conclusion

This lab demonstrated end-to-end IAM management using Terraform, including advanced concepts such as remote state management, dynamic resource creation, and automation using provisioners. All tasks were successfully completed and verified through Terraform outputs, AWS CLI, and AWS Console.

---


