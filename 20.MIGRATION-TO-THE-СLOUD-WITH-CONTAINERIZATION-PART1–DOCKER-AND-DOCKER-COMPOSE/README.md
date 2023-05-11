# MIGRATION TO THE СLOUD WITH CONTAINERIZATION. PART 1 – DOCKER & DOCKER COMPOSE

![pro20.PNG](./images/pro20.PNG)

Until now, you have been using VMs (AWS EC2) in Amazon Virtual Private Cloud (AWS VPC) to deploy your web solutions, and it works well in many cases. You have learned how easy to spin up and configure a new EC2 manually or with such tools as Terraform and Ansible to automate provisioning and configuration. You have also deployed two different websites on the same VM; this approach is scalable, but to some extent; imagine what if you need to deploy many small applications (it can be web front-end, web-backend, processing jobs, monitoring, logging solutions, etc.) and some of the applications will require various OS and runtimes of different versions and conflicting dependencies – in such case you would need to spin up serves for each group of applications with the exact OS/runtime/dependencies requirements. When it scales out to tens/hundreds and even thousands of applications (e.g., when we talk of microservice architecture), this approach becomes very tedious and challenging to maintain.

In this project, we will learn how to solve this problem and practice the technology that revolutionized application distribution and deployment back in 2013! We are talking of Containers and imply Docker. Even though there are other application containerization technologies, Docker is the standard and the default choice for shipping your app in a container!

## Install Docker and prepare for migration to the Cloud

First, we need to install `Docker Engine`, which is a client-server application that contains:

* A server with a long-running daemon process `dockerd`.
* APIs that specify interfaces that programs can use to talk to and instruct the `Docker` daemon.
* A command-line interface (CLI) client docker.

This [link](https://docs.docker.com/engine/install/) can be used for the installation of `Docker Engine` based on respective OS paltforms.

## Docker Engine
In this project, I would use an `ubuntu` Linux host as my `Docker Engine` to host my `Docker Containers`

Spin up the Ubuntu based EC2 instance and installed Docker and relevant dependencies

## MySQL in container
Using  a pre-built `MySQL` database container, configure it, and make sure it is ready to receive requests from our PHP application.

***Step 1: Pull MySQL Docker Image from [`Docker Hub Registry`](https://hub.docker.com/)***

Pull `MySql Docker Image` and confirm the image successful download with `docker image ls`

`docker pull mysql/mysql-server:latest`

![image-ls.PNG](./images/image-ls.PNG)

***Step 2: Deploy the MySQL Container to your Docker Engine***

`docker run --name <container_name> -e MYSQL_ROOT_PASSWORD=<my-secret-pw> -d mysql/mysql-server:latest`


![mysql-container.PNG](./images/mysql-container.PNG)

***Step 3: Connecting to the MySQL Docker Container***

I can either connect directly to the container running the MySQL server or use a second container as a MySQL client

**Approach 1**

Connecting directly to the container running the MySQL server using:



```
$ docker exec -it mysql bash

or

$ docker exec -it mysql mysql -uroot -p
```

![mysql-connect.PNG](./images/mysql-connect.PNG)

**Approach 2**

At this stage you are now able to create a docker container but we will need to add a network. So, stop and remove the previous mysql docker container.

```
docker ps -a
docker stop mysql 
docker rm mysql or <container ID> 04a34f46fb98
```

![remove-containers.PNG](./images/remove-containers.PNG)

***First, create a network:***

`docker network create --subnet=172.18.0.0/24 tooling_app_network `


![network.PNG](./images/network.PNG)


Creating a custom network is not necessary because even if we do not create a network, Docker will use the default network for all the containers you run. By default, the network we created above is of `DRIVER Bridge`. So, also, it is the default network. You can verify this by running the `docker network ls` command.

But there are use cases where this is necessary. For example, if there is a requirement to control the cidr range of the containers running the entire application stack. This will be an ideal situation to create a network and specify the `--subnet`

For clarity’s sake, we will create a network with a subnet dedicated for our project and use it for both MySQL and the application so that they can connect.

Run the MySQL Server container using the created network.

First, let us create an environment variable to store the root password:

`export MYSQL_PW=password`

verify the environment variable is created:

`echo $MYSQL_PW`

Then, pull the image and run the container, all in one command like below:

`docker run --network tooling_app_network -h mysqlserverhost --name=mysql-server -e MYSQL_ROOT_PASSWORD=$MYSQL_PW  -d mysql/mysql-server:latest`

Verify the container is running:

`docker ps -a`

As it is best practice not to connect to the MySQL server remotely using the root user. Therefore, we will create an SQL script that will create a user we can use to connect remotely.

Create a file and name it `create_user.sql` and add the below code in the file:

`CREATE USER ''@'%' IDENTIFIED BY ''; GRANT ALL PRIVILEGES ON * . * TO ''@'%';`

Run the script:
Ensure you are in the directory create_user.sql file is located or declare a path

`docker exec -i mysql-server mysql -uroot -p$MYSQL_PW < create_user.sql`


![sql-script.PNG](./images/sql-script.PNG)

***Note***: If you see a warning like below, it is acceptable to ignore:

`mysql: [Warning] Using a password on the command line interface can be insecure.`

Run the MySQL Client Container:

`docker run --network tooling_app_network --name mysql-client -it --rm mysql mysql -h mysqlserverhost -u  -p` 


![mysql-login.PNG](./images/mysql-login.PNG)


## Prepare database schema

Preparing a database schema so that the Tooling application can connect to it.
















