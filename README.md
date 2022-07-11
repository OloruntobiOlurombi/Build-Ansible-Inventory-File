# Topic: Build Ansible Inventory File

## Overview
> We are going to generate an Ansible inventory file using the AWS CLI. So that we can easily reference devices and machines from our Ansible Playbook, we need to list those devices in an inventory file. Instead of creating it manually, we're going to use AWS to list the EC2 instance hostnames and then we will pipe that to an inventory file automatically. Please note that the EC2 instance was provision using CloudFormation.

### Prerequisites:

> AWS Account

> AWS CLI should be installed and configured. Verify it using

```
aws --version
# Run any test command
aws iam list-users
```

### File Structure

![image](https://user-images.githubusercontent.com/40290711/178330958-11113075-99ef-4174-8b34-9f9331111c7a.png)

### Steps

> - Create an EC2 instance in your AWS account using the Ubuntu AMI and micro/free tier VM type. Add a memorable tag like Project:udacity to the instance. Please remember the tag name you're adding.
