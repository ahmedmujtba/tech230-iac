# tech230-iac

## Definition of IaC

Infrastructure as code (IaC) is the process of managing and provisioning computer data centers through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools

## How IaC benefits businesses

- Cost:

  - Helps a business save costs because building and maintaining own data centers is not required

- Boosts Productivity:

  - Improves prodcutivity of operations teams
  - Allows you to automate infrastructure hecne saves time, money and minimizes the risk of human error
  - More focus can be on mission critical tasks

- Consistent Configuration:
  - Standardised conifrguartion and setup for infrastercuture deployment during cloud migration
  - Reduces human error and expediates the migration process
- Visibility:

  - With IaC, everyone can know the current configuration of the infrastructure. Anyone with permission to access the code can see what the current configuration is.

- Easy to Scale:
  - With Infrastructure as Code, you can scale your infrastructure easily by just copying the existing code or adding a few extra lines

## Benefits of Ansible:

- Free as it's open source tool
- It's simple, human readable automation. no coding skills needed.
- Ansible is agentless where ansible being the controller acts as master node. no agent node which means it doesn't require any software to be installed on it.
- It's efficient because you don’t need to install any extra software, there’s more room for application resources on your server.
- Uses SSH protocol for connectivity with servers. i.e. SSH keys

## Ansible workflow diagram

Ansible can also be used with a hybrid approach where ansible controller is hosted locally but our app and db vm's are hosted in the cloud. Diagram to explain how workflow in ansible looks like:

- Vagrantfile to provision 3 VM's (Controller, App, DB)
- VirtualBox creates the VM's
- Aim is to control and configure them without having to ssh in each VM. Controller will do the work.
- Setup SSH connections to App and DB in Controller
- Ansible has python dependency (built with python)
- It uses YAML to exceute playbooks (set of instrcutions to complete tasks)
- Connection between App and DB is password protected

![alt text](./assets/ansible-vagrant-diagram.png)

## IaC workflow diagram

![alt text](./assets/2.jpg)

## Using Ansible (setup instructions)

Follow the steps in the guide [here](./ansible-setup.md) to setup Ansible and learn how to use it

## Why learn IaC & Ansible

## End goal of implementing IaC
