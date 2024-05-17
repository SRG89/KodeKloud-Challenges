# Terraform Challenge-03

In this challenge we will implement a simple EC2 instance with some preinstalled packages. 
We will utilize /root/terraform-challenges/project-citadel directory to store our Terraform configuration files.
Inspect the requirements in detail by clicking on the icons of the interactive architecture diagram:

<img src="./challenge-03.png" alt="">

# Initializaion of AWS Provider
<details>
<summary>AWS Provider</br>Aws provider has already been configured.Initialize aws provider for resource provision</summary>
  
```bash
    cd /root/terraform-challenges/project-citadel
    # Now initialize the aws provider.
    terraform init
```
Access the Aws provider file at [aws-provider](./provider.tf)
</details>

# Provision of AWS Resources With Terraform 
<details>
<summary>Aws Resources</br>Create the EC2 instance.</br>Create a terraform key-pair citadel-key with key_name citadel</br>Create a local-exec provisioner for the eip resource and use it to print the attribute called public_dns to a file /root/citadel_public_dns.txt on the iac-server</summary>

Access Aws resource provision file at [aws-resources](./main.tf)
</details>

# Deploy in AWS Environment
<details>
<summary>DEPLOY!</summary>
  
```bash
    terraform validate
    terraform plan
    terraform apply
```
</details>
