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


## AMI Snapshot

Note down the availability zone. Note down the security group as well. Click on the "Actions" dropdown and click "Create Image" in image and templates. Do not select "No reboot".

> Reserved instances can be used to tell AWS for future compute.
> Reserved instances are instance type exclusive. So a t3 won't reserve coupon won't work for t4 coupon.

In `AWS Cost Management` you can also go for a savings plans which only restricts you to a specific instance type.




















