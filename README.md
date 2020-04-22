# Node Packer
This repository includes files which are used to create an AMI (Amazon Machine Image) in AWS containing NodeJs, Nginx, Npm, Pm2. With some tweaks, the files can also be used to create machine images in other cloud providers which will not be shown here.

## Pre-requisites
I have run the cookbook using the below prerequisites:
- Packer v1.5.5
- Chef Workstation:
  - Infra Client v15.7.32
  - ChefDK v4.7.73
  - Test Kitchen v2.3.4
  - Foodcritic v16.2.0
  - Cookstyle v5.20.0
- AWS account

## Packer
Packer is a tool used to create machine images using your choice of configuration management tools (a provisioner such as Chef) and/or cloud provider (a builder such as Amazon EC2). These machine images will have a pre-configured operating system and already installed software which can be used to make machines instantly.

## How to use
Clone and navigate into the nodePacker directory and follow the below steps.
- Run berkshelf to pull the latest mongo cookbook.
```bash
$ berks vendor
```
- Configure packer.json to use your AWS details and keys (lines 10, 12, 13, 15, & 20). Also make sure your AWS credentials are saved in your environment variables.
- verify the packer.json file.
```bash
$ packer validate packer.json
```
- If the above validation passes, run the packer.json file.
```bash
$ packer build packer.json
```
- The above will open a connection with AWS and will create an EC2 instance, provision the machine, create an AMI and delete the temporary instance.

## Author
**Kevin Monteiro** - *DevOps Engineer* - [km-aero](https://github.com/km-aero)
