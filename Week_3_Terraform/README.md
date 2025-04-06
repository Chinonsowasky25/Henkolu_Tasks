## Steps Overview
Create a VPC
Create a Public & Private Subnet
Create an Internet Gateway and Route Table for the Public Subnet
Create a Security Group to Allow SSH (for the Public Instance)
Generate an SSH Key Pair and Attach it to the Public EC2 Instance
Deploy Two EC2 Instances (One in Each Subnet)

#  Terraform AWS EC2 Deployment

This project uses **Terraform** to provision AWS infrastructure, including:
- A custom **VPC**
- A **public subnet** and a **private subnet**
- Two `t2.micro` **EC2 instances**:
  - One in the public subnet (with SSH access)
  - One in the private subnet
- A generated **SSH key pair** for secure access to the public instance


##  Prerequisites

Before getting started, ensure you have:

- **Terraform** installed locally — [Install Terraform](https://developer.hashicorp.com/terraform/downloads)
- An **AWS account**
- **AWS CLI** configured on your system using:

On the terminal:
aws configure

.
├── InstD.tf           # Instance data for the main entry point or an additional configuration
├── variables.tf      # Input variables
├── outputs.tf        # Output values (e.g., IP addresses)
├── keypair.tf     # Generates an SSH key pair and saves the private key locally.
├── SecGrp.tf     # Creates security groups (firewall rules)
├── providers.tf  # Sets up the AWS provider – tells Terraform which cloud and region to use.
├── Instance.tf  #Launches two EC2 instances: one in the public subnet, one in the private subnet.
├── vpc.tf      # Creates the VPC, public & private subnets, internet gateway, and route tables.
├── .gitignore  # 	Ignores sensitive or temporary files like the private key.
└── README.md         # Project documentation

After writing the scripts for the deployment

## Deploy Commands
terraform init
terraform fmt
terraform validate
terraform plan
terraform apply




