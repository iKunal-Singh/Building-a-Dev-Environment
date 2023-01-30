# Building a Dev Environment with Terraform and AWS
This repository contains Terraform code to deploy a development environment on AWS. The environment includes the deployment of various AWS resources and an EC2 instance that you can SSH into to have your own redeployable development environment.
## Requirements
* [**Terraform**](https://developer.hashicorp.com/terraform/downloads)
* An **AWS account**
## How to use this Repository
### 1. Clone this repository:
```shell
$ git clone https://github.com/iKunal-Singh/building-a-dev-environment.git
```
### 2. Change into the repository directory:
```shell
$ cd building-a-dev-environment
```
### 3. Initialize Terraform:
```
$ terraform init
```
### 4. Configure the AWS credentials by editing the provider.tf file:
```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.0"
    }
  }
}

provider "aws" {
  region = "us-east-1"
  shared_config_files      = ["~/kunal/.aws/config"]   
  shared_credentials_files = ["~/kunal/.aws/credentials"]
  profile = "vscode"
}
```
Replace ACCESS_KEY, SECRET_KEY, and REGION with your AWS access key, secret key, and the region you want to deploy to. 

### 5. Create the Terraform plan:
```
$ terraform plan
```
### 6. Deploy the environment:
```
$ terraform apply
```
### 7. After the Terraform apply command finishes, you can log into the EC2 instance by typing ssh in command palette and choosing IP.
### 8. When you're finished with the environment, you can destroy it by running the following command:
```
$ terraform destroy
```

