# Create a Container Web Server with an ARM Template

## Project Scenario

As a Cloud Administrator, I'm going to deploy a legacy containerized web app to an Azure VM. Since I don't want to be doing things manually more that once, I'm then going to convert the solution into an Azure Resource Manager (ARM) template.

I'll create a Key Vault to improve security, and add a custom script extension to help with automating the deployment process.


## Project Stages

* Stage 1 - Manually setup a VM and host a docker web app
* Stage 2 - Create an ARM template to speed-up future deployments
* Stage 3 - Setup Key Vault to store credentials for the deployment
* Stage 4 - Add a custom script to automate the web app config
* Stage 5 - Cleanup



## Stage 1

### Create the VM

I signed into my Azure Portal, then selected Create a Resource, followed by Virtual Machine. I selected the following for my base VM:

* Size: Standard_B1s
* Image: Ubuntu Server 24.04 LTS
* Inboud port rules: Allow SSH (22)

### Configure the Network Security Group

Then, to address the issue of SSH on the VM being open to the Internet, I configured the NSG and locked down all inbound rules to allow only the IP of my local machine. 

To do this, I selected the default resource group created during the VM setup, then selected the NSG, then Settings > Inbound Security Rules.