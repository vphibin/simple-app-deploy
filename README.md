## Deployment of a Simple Sinatra application to a web server

This repo contains an Ansible playbook to deploy a simple Sinatra application to a web server.

A Vanilla OS image (Ubuntu) is used. The playbook will perform the following on top of the basic OS instance.

- Install basic/required packages like Make, Ruby
- Installs Apache
- Installs and configures Phusion Passenger, Sinatra
- Deploys the web application

### Instructions
The playbook can be executed by using the following instructions:  
*Note: This has been tested in a Ubuntu 14.04 remote instance in an EC2 environment*  
1. Download and install Ansible if not already installed  
[Install Ansible](http://docs.ansible.com/intro_installation.html#installation)  
2. Download the repository using the following  
```git clone https://github.com/vphibin/simple-app-deploy.git```  
3. Uncomment the line corresponding to the appropriate Ubuntu/Debian version (remote server instance) in the file roles/sinatra-passenger/files/passenger.list (right now ubuntu 14.04 is  selected). Comment out all other lines.  
4. Update the hostname/DNS of your remote instance in the "web-servers" section of the hosts file (in the main directory)  
5. Change the remote_username in the file group_vars/web-servers, if using a different user name for remote ssh  
6. Execute the playbook using the following:  
```$ ansible-playbook -i hosts site.yml```  
If you are using a private key file to connect to remote host, execute as below  
```$ ansible-playbook -i hosts --private-key=/path/to/private/key/file site.yml```  

Below is an example url where the application has been successfully deployed by using this playbook:
[ec2-52-10-210-106.us-west-2.compute.amazonaws.com](ec2-52-10-210-106.us-west-2.compute.amazonaws.com)

### Credits

The simple Sinatra application code is based on others we have encountered in the public domain, in particular:

[https://github.com/tnh/simple-sinatra-app](https://github.com/tnh/simple-sinatra-app)

Thanks to the authors for making their contributions publicly available.

