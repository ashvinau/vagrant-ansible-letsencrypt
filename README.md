# vagrant-ansible-letsencrypt
Vagrant and ansible configuration to demonstrate control of a domain and obtain a SSL certificate from Let's Encrypt

Requires:
Vagrant 2.0
Ansible 2.6

If you have a domain name pointed to an IP and want to demonstrate control to obtain a SSL certificate for free from Let's Encrypt you can use this playbook. 

1. Fill in the variables in config.rb with your AWS credentials and preferences. 
2. Fill in the domain name and email at the top of letsencrypt.yml.
3. Vagrant up
4. Retrieve your certificates and keys from the ./certificates directory to be used in the provisioning of your web server

Your provisioning must include the addition of the cron job like on line 76 of letsencrypt.yml to renew the certificates weekly.