# ansible-blue-green

### Instructions

After cloning the repository and installing ansible on your machine you should make inventory file with group [apps] which are the machines that we want to deploy app on them. Then you should run ansible playbook todo2/image.yaml which build and push images to dockerhub. This playbook run on your localhost so after that you have the images locally and remotelly on dockerhub. Then you should run playbook todo1/setup.yaml which includes installing and configuring nginx,docker and firewall. It also deploy the first application that it's parameters are defined in todo1/vars/first-var.yaml. After that you can deploy new applications with todo3/deploy.yaml which use blue/green technique. The parameters are defined in  todo3/vars/deploy-var.yaml. You can also rollback to the previous versions with todo3/rollback.yaml.

### Vars files

#### todo1/vars/first-var.yaml:
version -> choose the app version that you want deploy first. It's default is v1.0.0.  
port -> choose the port that publish for access. Nginx reverse proxy to this port.  

#### todo3/vars/deploy-var.yaml:
version -> verion that you want to deploy.  
port -> port that publish for access.  
pre_version -> version that you want to rollback to.  
pre_port -> port that nginx should reverse proxy to.  
email_host -> smtp server for sending state of the deployment like smtp.gmail.com.  
email_port -> smtp server port.  
email_username -> email address to use for sending.  
email_password -> password of the email.  
email_receiver -> email address of the person that receive the alert.  
email_enabled -> set this true/false for enable/disable the email feature. If you set it true you should define the email vars above.    
