# auxillary-projects

# Aux project using shell script

This project is entirely to test knowledge of the linux commands learnt thus far and the shell scripting knowledge.

I will be onboarding 20 new users to the Ubuntu linux server, adding them to a specified group and assign them some defined permissions to designated file and directory.

I will be creating a .csv file consisting all 20 users and create the script that will read the csv file that contains the first name of the users to be onboarded.

## Project steps

I created and navigated into the Shell directory

`mkdir Shell && cd Shell`

Then, I created the csv file using

`touch names.csv`

used `vi names.csv` to add all 20 names in the csv file

**Added the following users:**

- albaka
- abolad
- adades
- adadeb
- adazee
- adeda
- adokel
- adolow
- azayo
- joomai
- foaded
- chokoli
- hadisa
- hinaph
- chichu
- chopit
- sambas
- sauzor
- komoga
- joimha


Then, I confirmed all 20 users in the csv file with 

`cat names.csv` command

![csv-names.PNG](./images/csv-names.PNG)


**Created the developers group and confirmed creation**

`sudo groupadd developers`

`sudo grep developers /etc/group`

![developers-group.PNG](./images/developers-group.PNG)


**I created the public and private keys**

public key: `touch id_rsa.pub`


and populate with the following text: `vi id_rsa.pub`


`ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCzKZyicHxIkklSrNlxsJyyTrcIdBIt84Z0cQb3R4k0jH53kxkaT5hP8tfWTe62LXi7vV86fY+SX7TBNM76XGCbw/6vrMGegm6J1x2i1AiLNwq5nqTjOGn0AIwku4IlCCLAB7tdfRyVuCarmBlwny3lzRyybIUAWXR/D6vpN09MsDILbKdhay+Q/p9OUBMSLPqXdY/QIh/Oe3rVv1lwY3AohNfq7V3tO88zKswfA5iiexNiSYX1myT0OrX8cBE771j9quoNZhQgaLI1mIMtAvnHQChrn9k2nUaO/BMBCQGol5XzGv1ado7hgoVPoluIUD+FGNo/pH4zcmDLICH6drXY/C9MESnkMUPLFxBXKO/OitApY71vRao9nAhAwpVMsy6FqiOb5uawhvhoHYIHTV/f4EtagVagRMP2PxYMYR6jykIV4MPJTkCm+lGhTyMlRu+qRQjdLn8AAtHf4aEV8dIkoGh088DI7eA/4o0wz4OV4upH5ewSFS+5IHmRECEW5Nc=`


private key: `vi id_rsa`

and populate with the following text:

`-----BEGIN OPENSSH PRIVATE KEY-----
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
kmaSGj362OnCCNAAAACWRhcmVARGFyZQE=
-----END OPENSSH PRIVATE KEY-----`


Then, I created the ***onboarding_users.sh*** file so that I can add the script to it using text editor

`vi onboarding_users.sh`

populate the following script in it:


```
    #!/bin/bash
userfile=$(cat names.csv)
PASSWORD=password

#Ensure the user running this script has sudo priviledge
   if [ $(id -u) -eq 0 ]; then

#Read the csv file
    for user in $userfile;
    do
       echo $user
    if id "$user" &>/dev/null
    then
        echo "User Exist"
    else

#Create a new user and specify a group "developer" the user should be in
   useradd -m -d /home/$user -s /bin/bash -g developers $user
   echo "New user $user has been created"
   echo

#Create .ssh folder in the user home directory
   su - -c "mkdir ~/.ssh" $user
   echo ".ssh directory created for user $user"
   echo

#Set "rwx" user permission for the .ssh directory 
   su - -c "chmod 700 ~/.ssh" $user
   echo "$user permission for .ssh directory is set"
   echo

#Create an authorized_key file
   su - -c "touch ~/.ssh/authorized_keys" $user
   echo "Authorized key file created for user $user"
   echo

#Set "rw" user permission for the key file
   su - -c "chmod 600 ~/.ssh/authorized_keys" $user
   echo "user permission for the Authorized key file set"
   echo

#Create and set public key for users in the server
   cp -R "/home/ubuntu/Shell/id_rsa.pub" "/home/$user/.ssh/authorized_keys"
   echo "Public key has been copied successfully to new user $user authorized_keys file"
   echo

   echo "ALL THE USER HAS BEEN CREATED SUCCESSFULLY"

#Generate a password.
 sudo echo -e "$PASSWORD\n$PASSWORD" | sudo passwd "$user"
 sudo passwd -x 7 $user
        fi
     done
   else
 echo "Only Admin can Onboard users"
    fi
```

**Made script executable and ran it with the sudo command**

`chmod +x onboarding_user.sh`


![execute-script.PNG](./images/execute-script.PNG)


`sudo ./onboarding_user.sh`


![script-success.PNG](./images/script-success.PNG)

**I confirmed all users were created and already added to the developers group earlier created**

command `ls -la /home`

![ls-la-home.PNG](./images/ls-la-home.PNG)


Then, I confirmed with the following commands that user ***albaka*** who is the first user in the csv file ahows with user id 1001 and has all the required set up per the shell script we ran

The user appears to be in the developer group, has .ssh folder created in his home directory, the authorized_key file also exist for him in the .ssh file as shown in the image below:


![user-albaka.PNG](./images/user-albaka.PNG)


**Also did same for user chopit with same result as below:**

![user-chopit.PNG](./images/user-chopit.PNG)


***The above completed the requirements set from the documentation as listed 1 - 5...***

1. The script you created should read the CSV file, create each user on the server, and add to an existing group called developers 

2. Ensure that your script will first check for the existence of the user on the system, before it will attempt to create that it.

3. Ensure that the user that is being created also has a default home folder

4. Ensure that each user has a .ssh folder within its HOME folder. If it does not exist, then create it.

5. For each user’s SSH configuration, create an authorized_keys file and add ensxure it has the public key of your current user.


**Now test user access the ubuntu server via ssh**



From my local system, I created a pem key which replicates the content of the private keys

From VS code terminal, I did `nano auxproj.pem` command in the documents folder and copied the private keys contents into it then saved.

ran `cat auxproj.pem` to confirm the content as same as the private keys

After which I tried login as user albaka from the terminal via ssh using

`ssh -i "auxproj.pem" albaka@ec2-23-22-57-197.compute-1.amazonaws.com`


![user-albaka-ssh.PNG](./images/user-albaka-ssh.PNG)

Also tried logging in with a few other users just to confirm access

![adolow.PNG](./images/adolow.PNG)


![chichu.PNG](./images/chichu.PNG)


## Project completed ##



Below is the Youtube link to my screen record demo on how the users were onboarded onto the server for review


[Project demo](https://www.youtube.com/watch?v=9IOvwizIHhI)







