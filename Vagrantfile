# -*- mode: ruby -*-
 # vi: set ft=ruby :

#require "vagrant-aws ?"
require_relative 'config.rb'
include MachineVariables
 
 
Vagrant.configure("2") do |config|
config.vm.box = "ubuntu/xenial64"

	config.vm.provider :aws do |aws, override|
		override.vm.box = "dummy"
		override.vm.synced_folder ".", "/vagrant", disabled: false, type: 'rsync', SharedFoldersEnableSymlinksCreate: false
		override.ssh.username = "ubuntu"
		override.ssh.private_key_path = SSH_PRIVATE_KEY
		aws.access_key_id = AWS_ACCESS_KEY_ID
		aws.secret_access_key = AWS_SECRET_ACCESS_KEY
		aws.keypair_name = AWS_KEYPAIR_NAME
		aws.region = AWS_REGION
		aws.ami = "ami-51537029"
		aws.instance_type = "t2.micro"
		aws.security_groups = ["default"] 
		aws.elastic_ip = AWS_ELASTIC_IP
	end
	

	config.vm.define "letsencrypt" do |letsencrypt|
		config.vm.provision "ansible" do |ansible|
			ansible.compatibility_mode = "2.0"
			ansible.playbook = "letsencrypt.yml"
			ansible.verbose = "v"
		end
	end

end