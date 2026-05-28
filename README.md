# Terraform AWS Infrastructure Deployment

This project demonstrates Infrastructure as Code (IaC) using Terraform on AWS. The infrastructure provisions a custom VPC, public and private subnets, and an Amazon S3 bucket in the `ap-south-1` region.

## Project Overview

The Terraform configuration automates the deployment of the following AWS resources:

* Custom VPC
* Public Subnet
* Private Subnet
* Amazon S3 Bucket
* AWS Provider Configuration

This project was created and deployed from an Ubuntu EC2 instance using Terraform CLI and AWS CLI.

---

# Technologies Used

* Terraform v1.15.5
* AWS CLI
* AWS EC2 Ubuntu Instance
* Amazon VPC
* Amazon S3
* Linux (Ubuntu)

---

# Architecture

## Resources Created

### VPC

* CIDR Block: `10.0.0.0/16`

### Public Subnet

* CIDR Block: `10.0.38.0/24`

### Private Subnet

* CIDR Block: `10.0.40.0/24`

### S3 Bucket

* Bucket Name: `my-tf-test-bucket-28052026`

---

# Project Structure

```bash
day1/
│
├── main.tf
├── terraform.tfstate
├── .terraform.lock.hcl
└── .terraform/
```

---

# Terraform Configuration

## Provider Configuration

```hcl
provider "aws" {
  region = "ap-south-1"
}
```

---

# Deployment Steps

## 1. Install Terraform

```bash
sudo apt update
sudo apt install terraform
```

Verify installation:

```bash
terraform --version
```

---

## 2. Install AWS CLI

```bash
sudo apt install awscli
```

Verify installation:

```bash
aws --version
```

---

## 3. Configure AWS Credentials

```bash
aws configure
```

Provide:

* AWS Access Key ID
* AWS Secret Access Key
* Region: `ap-south-1`
* Output Format: `json`

---

## 4. Initialize Terraform

```bash
terraform init
```

This downloads the required provider plugins.

---

## 5. Validate Terraform Configuration

```bash
terraform validate
```

---

## 6. Review Infrastructure Plan

```bash
terraform plan
```

This command previews the infrastructure changes before deployment.

---

## 7. Deploy Infrastructure

```bash
terraform apply
```

Type:

```bash
yes
```

to confirm deployment.

---

# Terraform State File

Terraform stores infrastructure metadata inside:

```bash
terraform.tfstate
```

This file tracks all deployed AWS resources and their current state.

---

# Challenges Faced

## S3 Bucket Name Conflict

Initially, Terraform failed to create the S3 bucket because bucket names in AWS are globally unique.

### Error

```bash
BucketAlreadyExists
```

### Resolution

The bucket name was changed to a unique value:

```hcl
bucket = "my-tf-test-bucket-28052026"
```

---

# Verification

After deployment:

```bash
aws s3 ls
```

Terraform successfully created:

* VPC
* Public Subnet
* Private Subnet
* S3 Bucket

---

# Terraform Commands Used

```bash
terraform init
terraform validate
terraform plan
terraform apply
terraform destroy
```

---

# Future Improvements

* Add Internet Gateway
* Add Route Tables
* Launch EC2 Instances
* Configure NAT Gateway
* Store Terraform state remotely using S3 backend
* Implement Terraform modules
* Add Security Groups and NACLs

---



Cloud and DevOps Enthusiast

