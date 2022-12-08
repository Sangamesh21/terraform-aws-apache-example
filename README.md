Terraform Module to provision an EC2 Instance that is running Apache.

Not intended for production use. Just showcasing how to create a public module on Terraform Registry

```hcl
terraform {

}

provider "aws" {
  region = "eu-central-1"
}

module "apache" {
  source = "./terraform-aws-apache-example"
  vpc_id = "vpc-0000000"
  my_ip_with_cidr = "MY_IP_ADDRESS/32"
  public_key = "ssh-rsa AAAAB...."
  instance_type = "t2.micro"
  server_name = "Apache Example Server"
}

output "public_ip" {
  value = module.apache.public_ip
}
```