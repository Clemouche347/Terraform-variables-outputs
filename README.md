# Terraform Variables & Outputs Project

[![Terraform](https://img.shields.io/badge/Terraform-1.5-blue?logo=terraform)](https://www.terraform.io/)
[![AWS](https://img.shields.io/badge/AWS-Cloud-orange?logo=amazon-aws)](https://aws.amazon.com/)

## Overview
This project demonstrates how to use **Variables** and **Outputs** in Terraform by creating a **VPC** and **public subnets** on AWS. It covers defining variables of different types, using `.tfvars` files, and exposing resource information through outputs.

---

## Architecture
This project creates:

- **1 VPC** with a CIDR block defined via variable
- **2 public subnets** from a list of CIDRs

### Diagram (ASCII)
```
         +----------------------+
         |      VPC (10.0.0.0/16)|
         |      ID: vpc-xxxxxxx |
         +----------+-----------+
                    |
         -------------------------
         |                       |
 +----------------+       +----------------+
 | Public Subnet 1 |       | Public Subnet 2 |
 | CIDR: 10.0.1.0/24|      | CIDR: 10.0.2.0/24|
 | ID: subnet-xxx  |      | ID: subnet-xxx  |
 +----------------+       +----------------+
```

### Variables
| Name | Type | Description | Default |
|------|------|-------------|---------|
| `aws_region` | string | AWS region | `"eu-west-1"` |
| `project_name` | string | Name of the project | - |
| `vpc_cidr` | string | CIDR block for the VPC | - |
| `public_subnets_cidr` | list(string) | List of public subnet CIDRs | - |
| `tags` | map(string) | Common tags for resources | - |

### Outputs
| Name | Description |
|------|-------------|
| `vpc_id` | ID of the created VPC |
| `public_subnet_ids` | List of IDs of the public subnets |
| `vpc_cidr` | CIDR block of the VPC |

---

## Prerequisites
- AWS Account
- AWS CLI configured with credentials
- Terraform version >= 1.5

---

## Usage
```bash
terraform init
terraform plan
terraform apply
```

To see outputs:
```bash
terraform output
```

---

## Cleanup
```bash
terraform destroy
```

---

## Security Notes
- Never commit AWS credentials to GitHub
- Apply **least privilege** principle for IAM roles
- Do not hardcode sensitive values in Terraform files; use variables or secrets management

---

## Notes for Portfolio
- Practiced defining variables of different types: `string`, `number`, `bool`, `list`, `map`
- Created a VPC and public subnets on AWS using Terraform
- Learned to expose resource information via outputs
- Applied best practices: separating variables, using `.tfvars`, clear documentation, reusable outputs
