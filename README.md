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

> - Create an EC2 instance in your AWS account using the Ubuntu AMI and micro/free tier VM type. Add a memorable tag like Project:udacity to the instance. Please remember the tag name you're adding. Please note that the EC2 instance was provision using CloudFormation.

> infrafile.yml

```
AWSTemplateFormatVersion: 2010-09-09

Description: Creating an EC2 instance with hard coded values 

Resources:
  MyEC2:
    Type: AWS::EC2::Instance
    Properties: 
      InstanceType: "t2.micro"
      ImageId: "ami-052efd3df9dad4825"
      SecurityGroupIds: 
        - "sg-0cdd84a41d6e5a53e"
      SubnetId: "subnet-037fe5f8e2d468b9b"
      KeyName: "prom"
      Tags: 
        - Key: "Project"
          Value: "udacity"
```          

> - Create an inventory file called inventory (or inventory.txt) with and add [all] at the beginning, using these commands:

```
# Run this in your exercise directory
touch inventory
echo [all] > inventory
```

> - Run the following CLI command to list the EC2 instance and save the IP address to the inventory file:

```
aws ec2 describe-instances \
\
        --query 'Reservations[*].Instances[*].PublicIpAddress' \
      --filters "Name=tag:Project,Values=udacity" \
      --output text >> inventory
```      
> - This will append the udacity-tagged instance public IP addresses to our inventory file and should look something like this:

```
[all]
169.254.123.12  # The public IP will be different in your case
```
### Please terminate the EC2 instance created for this exercise to clean up.

### END
