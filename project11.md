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

## preparing dev env in vsc

cloning git repo

`$ git clone <ansible-config-mgt repo link>`

creating new github branch, prj-11, for development 

creating directories and files within said directories

`$ mkdir playbooks`

`$ cd playbooks`

`$ echo "" >> common.yml`

`$ mkdir inventory`

`$ cd inventory`

`$ echo "" >> dev.yml staging.yml uat.yml prod.yml`

![](images/ansibleprjbranchcommon9.png)

![](images/ansibleinventoryprod10.png)

## configuring ssh agent 

`$ eval `ssh-agent -s` `

`$ ssh-add <path-to-private-key>`

`$ ssh-add -l`

`$ ssh -A <public-ip-address>`

![](images/ansiblesshevalubuntu11.png)

![](images/ansiblesshtest12.png)

updating inventory/dev.yml file with host information

![](images/ansibledevyml13.png)

populating playbooks/common.yml file with ansible scripts that'll trigger the necessary tasks to be completed

![](images/ansibleplaybook14.png)

## updating git with the latest code

`$ git status`

`$ git add .`

`$ git commit -m "commit message"`

`$ git push origin prj-11`

`$ ls /var/lib/jenkins/jobs/ansible/builds/build-number/archive`

checkout to the main branch

`$ git pull`

`$ git merge prj-11`

![](images/ansiblefirstgit15.png)

![](images/ansiblefirstgit155.png)

![](images/ansiblefirstgit1555.png)

![](images/ansiblejenkins5.png)

![](images/ansiblejenkins55.png)

![](images/ansiblejenkinsbuild15555.png)

![](images/ansiblejenkinsbuild155555.png)

![](images/ansiblejenkinsbuild1555555.png)

![](images/ansiblegitpull16.png)

## running ansible test

using remote-ssh plugin on vsc to setup ssh config

![](images/ansiblesshconfig17.png)

`$ cd ansible-config-mgt`

`$ ansible-playbook -i inventory/dev.yml playbooks/common.yml`

![](images/ansibleplaybooktest17.png)

checking each server to confirm that wireshark is installed

`$ which wireshark`

`$ wireshark --version`

![](images/ansibledbwireshark18.png)

![](images/ansiblelbwireshark18.png)

![](images/ansiblewsswireshark18.png)

![](images/ansiblenfswireshark18.png)

![](images/ansiblewswireshark18.png)

updated ansible architecture now looks like this:

![](images/setupfinal.png)