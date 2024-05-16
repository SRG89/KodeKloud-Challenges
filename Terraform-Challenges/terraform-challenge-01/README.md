# Challenge-01:
In this challenge we will deploy several Kubernetes resources using terraform.
We will Utilize /root/terraform_challenge directory to store our Terraform configuration files.

Inspect the requirements in detail by clicking on the icons of the interactive architecture diagram on the right and complete the tasks.

<img src="./challenge-01.png" alt="">

# 1. Terraform Installation: 
  - Check if Terraform version: 1.1.5 is installed on controlplane node

# 2. Kubernetes provider:
Configure terraform and provider settings within provider.tf file with following specifications:
- Configure terraform to use hashicorp/kubernetes provider.
- Specify the provider's local name: kubernetes
- Provider version: 2.11.0
- Configure kubernetes provider with path to your kubeconfig file: /root/.kube/config

# 3.Create a terraform resource webapp-service for kubernetes service with following specs:
- Service name: webapp-service
- Service Type: NodePort
- Port: 8080
- NodePort: 30080

# 4.Create a terraform resource frontend for kubernetes deployment with following specs: 
- Deployment Name: frontend
- Deployment Labels = name: frontend
- Replicas: 4
- Pod Labels = name: webapp
- Image: kodekloud/webapp-color:v1
- Container name: simple-webapp
- Container port: 8080