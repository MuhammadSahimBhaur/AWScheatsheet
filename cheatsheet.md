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

> ⚠️ Do note: You can only access this once. Not later.











