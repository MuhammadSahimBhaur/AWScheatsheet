# AWS Setup

When starting off we create a root account. Using the root account we create an IAM account and give ourselves access. 

We can give ourselves "User and Role Access to Billing Information";
1. Click the edit button on the right
2. Click "Activate IAM Access"

![screenshot of access panel](https://github.com/MuhammadSahimBhaur/AWScheatsheet/blob/main/img.png?raw=true)

## IAM Setup

To gain almost all access use the `AdministratorAccess`.

### User Groups

Creating user groups allows for easier allocation of pollicies. We can also create and test custom policies. User groups have ARN's. Everything on AWS has an ARN.

### Add a user

> ⚠️ Do note: Select the credential type; "Access key - Progammatic access" so to be able to use the CLI tooling and "Password" thingy.


We can assign a new user the user group when are creating the new user. We can then download the .csv file containing the credential's to our new user's account

> ⚠️ Do note: You can only access this .csv file once. Not later.

AWS identity center can be used for tons of employees. AWS organization is an overall governing account for different subaccounts.

## AWS Billing

Go to cost explorer (in the "AWS Cost Management" page) to check if all the resources have been turned off and deleted.

Search in the top search bar `billing` and click on the first entry to open the billing dashboard. You can now go to `Billing preferences` to get alerts when a free tier is running out.

### Set a budget to save money

![screenshot](https://github.com/MuhammadSahimBhaur/AWScheatsheet/blob/main/img2.png?raw=true)














