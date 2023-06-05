# tech230-iac

## IaC workflow diagram

![alt text](./assets/2.jpg)

## How IaC beenfits businesses

- Cost:

Helps a business save costs because building and maintaiing own data centers is not required

- Scalability & Availability
- Performance visibility
- Configuration Inconsistencies

Notes from lecture:

Benefits of Ansible:

- It's simple, human readable automation. no coding skills needed.
- Ansible is agentless where ansible being the controller acts as master node. no agent node which means it doesn't require any software to be installed on it.
- Uses SSH protocol for connectivity with servers. i.e. SSH keys

How Ansible works (locally):

- We can use vagrant to create 3 VM's
- Create ansible controller, deploy node js, mongodb
- Aim is to control and configure them without having to ssh in each VM. Controller will do the work.
- Ansible has python dependency (built with python)
- It uses YAML

Hybrid approach:

Controller is local but other VM's are on cloud (aws)

Why learn it?

End goal of implementing IaC:

How to (steps):
vagarntfile in root folder or repo
vagrant up
vagrant status (should see 3 vm's running)

vagrant ssh controller - run update and upgrade
exit

vagrant ssh web - repeat update & upgrade
exit

vagrant ssh db - repeat update & upgrade
