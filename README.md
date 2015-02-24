## Deployment of a Simple Sinatra application to a web server

This repo contains an Ansible playbook to deploy a simple Sinatra application to a web server.

A Vanilla OS image (Ubuntu) is used. The playbook will perform the following on top of the basic OS instance.

- Install basic/required packages like Make, Ruby
- Installs Apache
- Installs and configures Phusion Passenger, Sinatra
- Deploys the web application

### Instructions
The playbook can be used by using the following instructions:
*Note: This has been tested in a Ubuntu 14.04 remote instance in an EC2 cluster*
1. Download and install Ansible if not already installed
[Install Ansible](http://docs.ansible.com/intro_installation.html#installation)
2. Download the repository using the following
git clone https://github.com/vphibin/simple-app-deploy.git
3. Uncomment the line corresponding to the appropriate Ubuntu/Debian version (remote server instance) in the file roles/sinatra-passenger/files/passenger.list (right now ubuntu 14.04 is  selected). Comment out all other lines.
4. Update the hostname/DNS of your remote instance in the webservers section of the hosts file
5. Change the servername in the apache_hosts variable in roles/webapp-deploy/vars/main.yml to the hostname/DNS of your instance
6. Execute the playbook using following:
```$ ansible-playbook site.yml```


### Credits

The simple Sinatra application code is based on others we have encountered in the public domain, in particular:

[https://github.com/tnh/simple-sinatra-app](https://github.com/tnh/simple-sinatra-app)

Thanks to the authors for making their contributions publicly available.

