## How to add a slave to a Jenkins?
* We add slave in a Jenkins to distribute the work load to different slaves. 

## Steps
* You need to have two or more instances . One instances which has jenkins installed is called master and the other remaining instances can be considered as slaves.
* Slave can be any machine. This doc . explains adding Linux as a slave.
* First go to master.
* see the /etc/passwd file .. and see if the jenkins user is there and has executable to /bin/bash .. if not change it to /bin/bash
* after changing it, change the password of jenkins user ( passwd jenkins ) --> make sure you have root privilige..
* You can also give jenkins user root privilege.. editing ( visudo ) file
* Now your password is changed. login to the jenkins user using su jenkins
* Make sure you are in jenkins home directory .. After that generate a key. ( ssh-keygen) 
*** This process will generate two keys public and private .

## On slave machine
* ssh into slave machine.
* You don't need to have jenkins installed in the slave machine but make sure you have java installed in it or it won't work.
* Once java is installed, create a user name jenkins and ssh into it.

## Again come back to Master.
* From your home directory of jenkins send the keys to the jenkin user of slave machine.
( ssh-copy-id jenkins@private_ip_of_slave_)
* It has successfully copied the public key and now you can ssh into it without password.
* Now go to the jenkins-console and manage nodes.
* Add new node name slave1 , and add label slave1 .. label is important because it will be used to call the slave.
* Add remote directory as a home directory of jenkins user of slave i.e /home/jenkins
* Launch method : launch via ssh ..
-- Host : give private ip of the slave
-- Enter private key directly : enter private key of the master(jenkins) .
* launch the agent and now your slave should be up and running.
