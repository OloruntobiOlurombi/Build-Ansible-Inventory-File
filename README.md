# Topic: Build Ansible Inventory File

## Overview
> We are going to generate an Ansible inventory file using the AWS CLI. So that we can easily reference devices and machines from our Ansible Playbook, we need to list those devices in an inventory file. Instead of creating it manually, we're going to use AWS to list the EC2 instance hostnames and then we will pipe that to an inventory file automatically. Please note that the EC2 instance was provision using CloudFormation.


