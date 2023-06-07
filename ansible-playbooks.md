# Ansible Playbooks

## Ansible Playbook Attributes

- `name`: Description for the task
- `become user`: For privilige escalation
- `apt`: Manages pacakges
- `update_cache`: Does not update cache, equivalent of apt-get update before the operation
- `state`: Indicates desired package state
- `shell`: To execute a shell command
- `args`: To pass additional parameters
- `chdir`: Change into this directory before running the command
- `gather_facts`: To gather facts about remote hosts i.e. app,db
- `synchronize`: wrapper around rsync to make common tasks in playbook quick

NOTE: rsync is a command line tool for copying files and directories between local and remote systems.

## Nginx Playbook

We can create Ansible Playbooks to codify steps to install/setup (using yaml) webserver called nginx in the web node.

1. To make sure you're in the right directory run `cd /etc/ansible`

2. Run `sudo nano config_nginx_web.yml` to create a playbook to install nginx in web-server or any other servers.

NOTE: make sure to add --- to start our yaml file. this is how intepretor knows when our yaml code starts in the file.

3. Setup your file as follows:

```
# add the name of the host in the file (dash below starts a code block)

- hosts: web

# gather facts
  gather_facts: yes

# to add admin access in this file:
  become: true

# add instructions/tasks to install nginx:

  tasks:

  - name: Installing Nginx
    apt: pkg=nginx state=present
```

4. Save and run the file using `sudo ansible-playbook config_nginx_web.yml`

output:

![alt text](./assets/nginx-config.png)

5. We can now check nginx status to see if nginx is active and running:

`sudo ansible web -a "sudo systemctl status nginx"`

![alt text](./assets/nginx-status.png)

### Above steps can be repeated for `db`

your final output for db should be:

![alt text](./assets/nginx-db-status.png)

## NodeJS Playbook

This playbook is created to copy app folder to web, install NodeJS and start the application.

NOTE: we can use the following command to copy app folder to our web agent. However for the purpose of the exercise we will be creating a playbook to accomplish this

`ansible web -m copy -a "src=/etc/ansible/app dest=/home/vagrant"`

1. Creating the playbook:

```
sudo nano config_app.yml
```

2. Adding tasks to the playbook:

We can add tasks to accomplish following tasks in this playbook:

- Install Nginx
- Copy App folder to web
- Install NodeJS
- Start the Application
- Add reverse proxy (yet to be completed)

Code inside the playbook should look like this:

![alt text](./assets/app-config.png)

3. Execute playbook with `sudo ansible-playbook app-config.yml`

![alt text](./assets/nodejs-playbook.png)

4. Copy the web IP and paste in the browser with `port 3000` at the end

Working App:

![alt text](./assets/app-working.png)





# DB

we want to make sure a ping is still active with status 200

NOTE: If any playbook return error run it with `-vvv` at the end to get readable error

sudo ansible all -m ping

use controller to 

- create a playbook setup mongodb in db-server
- required version of mongo
- change mongo.conf to facilitate required connections
- end goal to cnnect app to db & see the /posts in the browser

TO create a playbook
```
cd /etc/ansible
sudo nano setup_mongo.yml
```

Code within the playbook:

```
  GNU nano 2.9.3                   setup_mongo.yml

# to install required version of mongodb in db-server

---
# hosts name

- hosts: db

# gather facts/logs

  gather_facts: yes

# admin access

  become: true

# add instrcutions

  tasks:
  - name: Setting up MongoDB
    apt: pkg=mongodb state=present
# status check - ensure app is running


```
To run the playbook
```
sudo ansible-playbook setup_mongo.yml
```

output:

![alt text](./assets/setup-mongo-output.png)


TO check the status of mongodb
```
sudo ansible db -a "sudo systemctl status mongodb"
```

To SSH into db:

```
ssh vagrant@192.168.33.11
```

cd /etc

sudo nano mongod.conf

change following two lines as follows:

bind_ip = 0.0.0.0
port = 27017

To make sure our conifguration kicks in we re run mongodb

```
sudo systemctl restart mongodb
sudo systemctl enable mongodb
sudo systemctl status mongodb
```

exit back into controller

ssh into web 
create a db host =db-ip:27017/posts (only put in bashrc file if it works)
export DB_HOST=192.168.33.11:27017/posts
printenv DB_HOST
.bashrc (only put in bashrc file if it works)
navigate to app folder
npm start
should load all three pages


in controller 