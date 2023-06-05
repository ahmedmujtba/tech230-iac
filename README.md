# tech230-iac

## IaC workflow diagram

![alt text](./assets/2.jpg)

## How IaC benefits businesses

- Cost:

Helps a business save costs because building and maintaiing own data centers is not required

- Scalability & Availability
- Performance visibility
- Configuration Inconsistencies

## Why learn IaC & Ansible

## End goal of implementing IaC

## Benefits of Ansible:

- It's simple, human readable automation. no coding skills needed.
- Ansible is agentless where ansible being the controller acts as master node. no agent node which means it doesn't require any software to be installed on it.
- Uses SSH protocol for connectivity with servers. i.e. SSH keys

## How Ansible works

- We can use vagrant to create 3 VM's
- Create ansible controller, deploy node js, mongodb
- Aim is to control and configure them without having to ssh in each VM. Controller will do the work.
- Ansible has python dependency (built with python)
- It uses YAML

## Ansible workflow diagram

Ansible can also be used with a hybrid approach where ansible controller is hosted locally but our app and db vm's are hosted in the cloud. Diagram to explain how workflow in ansible looks like:

![alt text](./assets/ansible-diagram.png)


## Using Ansible (setup instructions)

1. Make sure Vagarntfile exists in the root folder of your repo.
2. Run `vagrant up`
3. Run `vagrant status` (should see 3 vm's running)

vagrant ssh controller - run update and upgrade
exit

vagrant ssh web - repeat update & upgrade
exit

vagrant ssh db - repeat update & upgrade

