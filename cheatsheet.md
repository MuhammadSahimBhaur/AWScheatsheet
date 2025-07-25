# AWS Setup

When starting off we create a root account. Using the root account we create an IAM account and give ourselves access. 

We can give ourselves "User and Role Access to Billing Information";
1. Click the edit button on the right
2. Click "Activate IAM Access"

![screenshot of access panel](https://github.com/MuhammadSahimBhaur/AWScheatsheet/blob/main/img.png?raw=true)

## IAM Setup

To gain almost all access use the `AdministratorAccess`.

### User Groups

Creating user groups allows for easier allocation of pollicies. We can also create and test custom policies. User groups have ARN's. Everything on AWS has an `ARN`.

### Add a user

> ⚠️ Do note: Select the credential type; "Access key - Progammatic access" so to be able to use the CLI tooling and "Password" thingy.


We can assign a new user the user group when are creating the new user. We can then download the .csv file containing the credential's to our new user's account

> ⚠️ Do note: You can only access this .csv file once. Not later.

`AWS identity` center can be used for tons of employees. `AWS organization` is an overall governing account for different subaccounts.

## AWS Billing

Go to cost explorer (in the "AWS Cost Management" page) to check if all the resources have been turned off and deleted.

Search in the top search bar `billing` and click on the first entry to open the billing dashboard. You can now go to `Billing preferences` to get alerts when a free tier is running out.

### Set a budget to save money

![screenshot](https://github.com/MuhammadSahimBhaur/AWScheatsheet/blob/main/img2.png?raw=true)

# EC2 setup

How to configure EC2 including;
- AMI
- Instance type
- Key Pair Login


```bash
AMI - Amazon Machine Image
```

## Intance Types

A brief overview of the ec2 classes.

![ec2 classes](https://miro.medium.com/v2/resize:fit:1400/0*1Ko4Oy89bieuKj6_.jpg)


## Key Pair Login

 A key pair login is used to SSH into our instance. A .PEM file will download. 

 > ⚠️ Note: this will also be only be able to be downloaded once.

Next allow SSH traffic from anywhere to be able to connect to your own EC2 instance. Also allow HTTP traffic for public access.

## Setting up a web server

AMI's aren't neccesarily up to date. So we can update the server using the following;

```bash
sudo apt update
sudo apt upgrade
```

> Note; we restart the intance if a kernal update is done.


## Clone a server; AMI Snapshot

Note down the availability zone. Note down the security group as well. Click on the "Actions" dropdown and click "Create Image" in image and templates. Do not select "No reboot".

> Reserved instances can be used to tell AWS for future compute.
> Reserved instances are instance type exclusive. So a t3 won't reserve coupon won't work for t4 coupon.

 ----- Money Saving tip! -----

> 💸 In `AWS Cost Management` you can also go for a savings plans which only restricts you to a specific instance type.


#  Security Groups

Scurity groups are like simple firewalls that only allow traffic to flow that has originated from our server. You can't edit security group name once they've been created. 

> 🚨 You can **copy** security groups! And then change eacgh instance's security group.

An instance can have multiple security groups, which means the rules **get added up**.


# Virtual Private Cloud

VPC is indicated by a $${\color{green}green}$$ box. Every VPC has non-routable IPs which are used to hookup to other services. Search "vpc" and go to "your vpcs" to check all vpc you have. 

> ⚠️ NEVER DELETE THE DEFAULT VPC


We can create different VPCs for different businesses. You have A LOT of usable IP addresses. You can then create `subnets` and divide these IP addresses. This allows for appyling different networking rules for different subnets.

There are default subnets that already exist in the default VPC. 

Create a public subnet for servers exposed to public internet traffic. Then create a private subnet which includes more protected internal services like database and file servers. 

![local availability zones and VPCs](https://github.com/MuhammadSahimBhaur/AWScheatsheet/blob/main/img3.png?raw=true)

> A Local Zone is an extension of an AWS Region in geographic proximity to your users. Local Zones have their own connections to the internet and support AWS Direct Connect, so that resources created in a Local Zone can serve applications that require low latency.
> To use a Local Zone, you must first enable it. Next, you create a subnet in the Local Zone. Finally, you launch resources in the Local Zone subnet. For more detailed instructions, see Getting started with AWS Local Zones.
> The following diagram illustrates an account with a VPC in the AWS Region us-west-2 that is extended to the Local Zone us-west-2-lax-1. Each zone in the VPC has one subnet, and each subnet has one EC2 instance.


# Internet and NAT gateways

NAT gateways allow one way traffic with a single IP address while a internet gateway allows for two-way traffic and can allow public access. We can assign a NAT gateway to a private subnet.

## Elastic IP Address

A public IP is assigned at random when an instance is spun up however whenever an instance reboots a new random IP is assigned. This becomes a major problem when the IP address is hard coded in DNS. 

Elastic IPs are billed even when not in used unless they are released. You can select elastic IPs and under the Actions pulldown click on the "Associate Elastic IP Address" to bind the elastic ip to an instance.


## Elastic Load Balancers

1. Application Load Balancer; Great for web traffic
2. Network Load Balancer; Fast but not very specific
3. Gateway Load Balancer;  Switching traffic

> Note: Select public subnet if private and public subnets are created.


You will also create a new security group for load balancers. While creating the security group you set the destination as other security groups that have the desired EC2 instances associated with them. This way they can recieve directly from the ALB (Application Load Balancer).


# IaaS Storage

Virtual drives (Elastic Block Store) are used to store data with strectchable storage. You can create a volume (a new drive) and "attach" to an instance. This new volume has to be formatted to be made useful. To do this you will need to access your machine via SSH and set it up.

You can reattach (to add it to another instance) and upgrade the space. If you add more space you'll need to format it too. 

For backups you can take periodic AMI snapshots. 

> ⚠️ Once an EBS is attached to an intance there is no way to "share files" with other instacnes.


EFS isn't as fast as EBS. Obviously because EBS is closer to your instance. 

## EFS

You can create and attach volumes to your instances. You will then use linux commands to connect the EFS to your instances.

## S3

Like dropbox. 































