## Terraform Modules: Simplifying Infrastructure as Code

Terraform modules are a fundamental concept in Terraform, a widely-used Infrastructure as Code (IaC) tool. They play a crucial role in making infrastructure code more modular, manageable, and reusable. By encapsulating Terraform configurations, modules abstract and organize resources, making it easier to provision, manage, and scale infrastructure across various environments and projects.

## Task 1 : Creating AWS resources using terraform modules
```
cd /home/ubuntu/
```
```
sudo apt install tree -y
```
```
wget https://s3.ap-south-1.amazonaws.com/files.cloudthat.training/devops/terraform-essentials/terraform-modules.tar.gz
```
```
tar -xvf terraform-modules.tar.gz
```
```
cd terraform-modules
```
```
tree
```
```
vi main.tf
```
# Add the below code after block module "my_security_group"
```
output "secgrpid" {
  description = "Newly created sec grp"
  value       = module.my_security_group.sgid
}
```
# Create a key pair. The public key of the same will be saved into the EC2 being launched.
```
ssh-keygen -f mykey
```
```
vi variables.tf 
```
**Note:** Replace the `Region` Default `VPC ID,` `AMI Id` and `Subnet ID` from your Allocated region in `variable.tf` file.
* `Change vpc_id` to default VPC in your region (**Ex:** vpc-0e608033e14b01c3c)
* `Change subnet id` Use any available subnets from AZ `a or b`. (**Ex:** subnet-086dd80df2e64b56b)
* `Change key_name to yourname-Lab12-keypair (ex: my-keypair)

Then, Save it
```hcl

variable "region" {
    default = "us-east-1"
} 

variable "sg_vpcid" {
    default = "vpc-0145545ee19d71389"
}

variable "from_port" {
    default = 22
}

variable "to_port" {
    default = 22
}

variable  "sg_name" {
    default = "terraform-sgp"
}

variable "ami_id" {
    default = "ami-0fc5d935ebf8bc3bc"
}

variable "ins_type" {
    default = "t2.micro"
}

variable sub_id {
    default = "subnet-0881026ede3d83d8f"
}

variable key_name {
    default = "my-key-pair"
}

variable from_port2 {
    default = 80
}

variable to_port2 {
    default = 80
}

variable public_key {
    default = "mykey.pub"
}
```
```
terraform init
```
```
terraform fmt
```
```
terraform validate
```
```
terraform plan
```
```
terraform apply -auto-approve
```
```
terraform destroy -auto-approve
```
```
cd ..
rm -rf terraform-modules
```
