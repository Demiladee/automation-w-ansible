## installing & configuring ansible on ec2 instance

i'm using the jenkins server i configured in the previous project for this ansible project 

`$ sudo apt update`

`$ sudo apt install ansible`

`$ ansible --version`

![](images/ansibleupdate1.png)

![](images/ansibleinstall2.png)

![](images/ansibleversion3.png)

creating github repo, ansible-config-mgt, for the project

![](images/ansiblegitrepo4.png)

creating jenkins job - freestyle project - and pointing it to the ansible repo

configuring webhook to trigger ansible build

configuring post-build job to save all files

testing config by editing readme file

confirming jenkins saves the file in remote folder

`$ ls/var/lib/jenkins/jobs/ansible/builds/build-number/archive/`

![](images/ansiblejenkins5.png)

![](images/ansiblejenkins55.png)

![](images/ansiblewebhook7.png)

![](images/ansiblebuildtest8.png)

![](images/ansiblebuildtest88.png)

![](images/ansiblebuildtest888.png)

![](images/ansiblebuildtest8888.png)

![](images/ansiblebuildtest88888.png)

setup should look like this now:

![](images/setup.png)