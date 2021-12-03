# eng99CloudAWS

- create EC2 instance - VM 
- Ubuntu 18.04LTS
- Select the size of the VM
- Create Security Group
- SSH into machine with AWS key
- check VM - with update and upgrade
- install nginx to be accessible on public IP
- enable public ip
- get app folder using secure copy 'scp'
- install dependencies


Copy files into EC2 instance:

scp -i pem_file file_to_copy user@ip:/destination

example: scp -i "~/.ssh/eng99.pem" restaurant.py ubuntu@e***.com:/home/ubuntu/new_folder/restaurant.py

Regions and Availability Zones (AZ) 

Not every AZ has every services 

Configure security group:

Go in security tab and select security group
Add new inbound rule


![image](https://user-images.githubusercontent.com/14828358/144407299-7e2b7eb4-c4fe-4744-aa2b-f1fb2c84e7d3.png)

## Steps to set up instance:

![image](https://user-images.githubusercontent.com/14828358/144407787-afcb3c44-4b77-4e00-8835-2c9755fddd0d.png)

## Step 1: Select free tier filter

![image](https://user-images.githubusercontent.com/14828358/144407926-42fd46f6-2fa6-42fe-b271-2b5b9afe0680.png)

## Step 2: Select Instance

![image](https://user-images.githubusercontent.com/14828358/144407995-6b230bb3-35be-4939-a62e-2330d44ea0c8.png)

Click Next

## Step 3: Configure Instance

![image](https://user-images.githubusercontent.com/14828358/144436911-630261ce-ed00-4a7a-8004-ce483c0bb27d.png)

## Step 4: Add Storage

Click Next

## Step 5: Add Tags

![image](https://user-images.githubusercontent.com/14828358/144409066-a9e3d1e8-41a3-4fd7-adf8-7e2f5b6b90be.png)

![image](https://user-images.githubusercontent.com/14828358/144409178-0c50bacb-fd50-4ef4-9062-c68b41dff529.png)


![image](https://user-images.githubusercontent.com/14828358/144409355-b2e74ef9-666d-4a6f-b646-a1a19c9fca0c.png)



Specify new inbound rule to allow app to access database

![image](https://user-images.githubusercontent.com/14828358/144412565-c3bad5bd-bd61-4097-819a-990fe6a0c70b.png)



# Amazon Machine Image (AMI)

![image](https://user-images.githubusercontent.com/14828358/144434131-4c2dc9ce-01b4-497a-8493-16f7c04bf090.png)

Image name: eng99_sunny_app_ami
Image description: eng99_sunny_app_ami

Add Tag
Name = eng99_sunny_app_ami

![image](https://user-images.githubusercontent.com/14828358/144455406-f0e4e6c1-1d59-46b9-abce-2ef5a1390444.png)

Click Create Image

On the panel, navigate to AMIs and search for your AMI

![image](https://user-images.githubusercontent.com/14828358/144456271-52cad34e-4946-4ecb-b92d-1d4e61c1125e.png)


# Monitoring

![image](https://user-images.githubusercontent.com/14828358/144445063-6979b7a2-b191-4d01-beae-fa0a7cf7a85f.png)

## CloudWatch - Monitoring Service

Amazon SNS topics:
https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/US_SetupSNS.html

![image](https://user-images.githubusercontent.com/14828358/144445619-10eed2ea-b0ab-4a92-b7bd-42a516950f95.png)

Create an alarm

![image](https://user-images.githubusercontent.com/14828358/144465486-d3bdd426-3654-4ce6-a7cd-927add957484.png)

# AWS Auto Scaling and Load Balancing

Highly Available - Available in multiple Regions and/or Availability Zones

https://docs.aws.amazon.com/autoscaling/plans/userguide/what-is-aws-auto-scaling.html

![image](https://user-images.githubusercontent.com/14828358/144585569-b67f504d-73ae-4cb1-8fbb-3b96b6a3656d.png)

- Create Launch template for autoscaling group
- Create auto scaling group
- Create auto load balancer
- attach vpc - 3 subnets in 3 different AZs
- Configure Security group for app
- all ec2 have nginx installed
- Regions eu - AZs
- Disaster Recovery Plans


- Hybrid Cloud Deployment - Fintech - Banks
- Multi Region Deployment - Large organisations
- Mult Could Deployment - Financial Conduct Authority -> All banks must have multi cloud deployment
- If a bank went down, the information would be available in another cloud network

# Launch Template

![image](https://user-images.githubusercontent.com/14828358/144588389-38922a8b-e28f-42b7-a9cf-221076df1e0a.png)


![image](https://user-images.githubusercontent.com/14828358/144588662-376f730f-e48d-4cf2-8868-ad244f6f30f2.png)


![image](https://user-images.githubusercontent.com/14828358/144588792-400ae5a6-58b0-408e-90b7-968b190be1a6.png)

![image](https://user-images.githubusercontent.com/14828358/144588837-2343bede-5e25-46e6-9f55-8ffd3bed34c2.png)


![image](https://user-images.githubusercontent.com/14828358/144588952-31c2472b-55d6-42ef-a062-16789a82530f.png)

![image](https://user-images.githubusercontent.com/14828358/144589100-58a99eb2-0429-4e3b-b9cd-cfb8588fe733.png)


Advanced Details:


Provisions:

![image](https://user-images.githubusercontent.com/14828358/144589657-8ab30af3-bb06-4fc1-a623-79c91deee194.png)
 
 
 Launch Template


![image](https://user-images.githubusercontent.com/14828358/144589734-55a2b9da-ba53-4439-9cc1-504234460279.png)

![image](https://user-images.githubusercontent.com/14828358/144589916-ebe20a4f-5246-488a-a511-46783f68e109.png)

# Auto Scaling

![image](https://user-images.githubusercontent.com/14828358/144593383-cb1c2388-eac3-4226-9a2a-b46134f3c20a.png)

![image](https://user-images.githubusercontent.com/14828358/144593489-db99a7be-0ce8-440b-bd2c-dddd874bdd1a.png)

## Step 1: Choose Launch Template or Configurations

Name does not allow underscore

![image](https://user-images.githubusercontent.com/14828358/144593685-78d983f2-a44c-4dd2-86ca-b200d2f9d91c.png)

Click Next

## Step 2: Choose Instance Launch Options

default vpc

![image](https://user-images.githubusercontent.com/14828358/144593883-c2387b29-b31a-4c16-9651-d68c3aef6a2e.png)

Click next

## Step 3: Configure Advanced Options

![image](https://user-images.githubusercontent.com/14828358/144594066-022dd23a-f981-49fb-88a0-f88cbca88bc2.png)

![image](https://user-images.githubusercontent.com/14828358/144594226-e5606f32-4506-4947-9174-bb59c17346d2.png)

![image](https://user-images.githubusercontent.com/14828358/144594276-7458b4ef-fd7c-4e7d-aa03-f7e0a7582af7.png)

click next

## Step 4: Condigure Group Size and Scaling Policies

![image](https://user-images.githubusercontent.com/14828358/144594372-5c41f30b-acdf-4eea-a448-e3043420de63.png)

![image](https://user-images.githubusercontent.com/14828358/144594506-5cfed058-fdea-44e2-b048-91f77e667694.png)

click next

## Step 5: Add Notifications

![image](https://user-images.githubusercontent.com/14828358/144594615-b276227a-736e-4ce9-b064-c091d00a723e.png)

click next

## Step 6: Add Tags

![image](https://user-images.githubusercontent.com/14828358/144594690-7670e407-fcf4-421a-af05-48c20a5c1761.png)

click next

## Step 7: Review

check settings -> Click Create Auto Scaling Group


![image](https://user-images.githubusercontent.com/14828358/144598181-a3d870d2-3969-47cf-9959-c056ca5a0a2c.png)



# S3 and AWS CLI

S3 - Simple Storage Service. Used as a database.


![image](https://user-images.githubusercontent.com/14828358/144619065-6247bfa0-ddd4-40c9-8845-3c4b2ac6dc16.png)


 sudo apt-get update -y && sudo apt-get upgrade -y
    4  sudo apt update -y
    5  sudo apt upgrade -y
    6  python --version
    7  sudo apt install python3 -y
    8  sudo apt-get install python3-pip
    9  clear
   10  alias python=python3
   11  sudo apt install awscli -y
   12  python --verison
   13  python --version
   14  python3 -m pip install aswcli
   15  python3 -m pip install awscli
   16  aws configure
   17  history
   
list aws s3 content
$ aws s3 ls
   
creating a bucket, make bucket (mb)
$ aws s3 mb s3://eng99-sunny
   
Copy file into s3 bucket   
$ aws s3 cp README.md s3://eng99-sunny

Copy file from bucket to local machine 

$ aws s3 cp s3://<path_to_file> <location>
   
Remove bucket
$ aws s3 rb s3://eng99-sunny --force
   
   
   
