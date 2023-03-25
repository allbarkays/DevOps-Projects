# Project 4

**Project task**


To implement a simple Book Register web form using MEAN stack.

started by running `sudo apt update` followed by `sudo apt upgrade`

Got a prompt requesting kernel upgrade:

![kernel-upgrade.PNG](./images/kernel-upgrade.PNG)

restarted the Ubuntu server from the terminal so that the kernel upgrade will complete

changed to windows terminal afterwards and added required certificates which also confirmed kernel was upgraded


![Added-certificates-kernel-upgraded.PNG](./images/Added-certificates-kernel-upgraded.PNG)


Then, installed node.js

`sudo apt install -y nodejs`


## Install MongoDB

Experienced a series of errors below while installing MongoDB as it appeared that Ubuntu version 22.04 does not support the MongoDB version as it populates *DEPRECATED* error

![sudo-apt-key-and-echo-deb-result.PNG](./images/sudo-apt-key-and-echo-deb-result.PNG)

![Mongo-Db-failed.PNG](./images/Mongo-Db-failed.PNG)

After going through a lot of write ups to scale this blocker, I used the steps in this link to address the error: *https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/* 

*installed MongoDB community edition*

![mongod-used.PNG](./images/mongod-used.PNG)

installed npm and checked version:

![npm-version.PNG](./images/npm-version.PNG)

Followed the documentation to create required directories and files... I also copied and pasted required scripts and html 

![Required-steps.PNG](./images/Required-steps.PNG)

Added TCP port 3300 in my security group in Ubuntu server EC2 instance in AWS.

![TCPport3300.PNG](./images/TCPport3300.PNG)


### **webpage result**


![test-page-lemp.PNG](./images/test-page-lemp.PNG)

![result-lemp.PNG](./images/result-lemp.PNG)

![Tested-OK.PNG](./images/Tested-OK.PNG)

![test-delete.PNG](./images/test-delete.PNG)

![delete-worked.PNG](./images/delete-worked.PNG)

![Terminal.PNG](./images/Terminal.PNG)



With this done, I can't wait to start more complex and fun *‘PBL Professional’* projects!!!
