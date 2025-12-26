# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "aws-dummy"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = "test"
    aws.secret_access_key = "test"
    aws.region = "us-east-1"
    # aws.endpoint = "https://ec2.us-east-1.amazonaws.com"

    aws.ami = "ami-0b6c6ebed2801a5cb" # Ubuntu Server 24.04 LTS (HVM), SSD Volume Type
    aws.instance_type = "t2.nano"
    aws.keypair_name = "deployer-key"
    # aws.security_groups = ["SECURITY_GROUP_ID"]
    aws.user_data = File.read("user-script.sh")

    override.ssh.username = "ubuntu"
    override.ssh.private_key_path = "keys/id_rsa.pem"
  end
end
