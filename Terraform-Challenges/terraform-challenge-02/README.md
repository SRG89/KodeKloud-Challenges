# Challenge-02:
In this challenge we will implement a simple LAMP stack using terraform and docker.
We will utilize /root/code/terraform-challenges/challenge2 directory to store our Terraform configuration files.

Inspect the requirements in detail by clicking on the icons of the interactive architecture diagram on the right and complete the tasks. 
Once done click on the Check button to validate your work.
<img src="./challenge-02.png" alt="">

# 1. Terraform Inatallation 
- Install terraform binary version=1.1.5 on iac-server

# 2. Docker provider has already been configured using kreuzwerker/docker provider.
- Check out the provider.tf given at /root/code/terraform-challenges/challenge2

# 3. Create a terraform resource named php-httpd-image for building docker image with following specifications:
- Image name: php-httpd:challenge
- Build context: lamp_stack/php_httpd
- Labels: challenge: second

# 4. Create a terraform resource named mariadb-image for building docker image with following specifications:
- Image name: mariadb:challenge
- Build context: lamp_stack/custom_db
- Labels: challenge: second

# 5. Define a terraform resource phpmyadmin for docker container with following configurations:
- Container Name: db_dashboard
- Image Used: phpmyadmin/phpmyadmin
- Hostname: phpmyadmin
- Attach the container to network my_network
- Publish a container's port(s) to the host:
- Hostport: 0.0.0.0:8081
- containerPort: 80
- Labels: challenge: second
- Establish link based connectivity between db and db_dashboard containers (Deprecated)
- Explicitly specify a dependency on mariadb terraform resource

# 6. Create a terraform resource named mariadb_volume creating a docker volume with 
- name=mariadb-volume