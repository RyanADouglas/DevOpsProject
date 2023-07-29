# Ansible Configuration on Jenkins

### Connect Ansible Control Node with Jenkins
- Manage Jenkins > System > Publish over SSH > SSH Servers
  - SSH Servers:
  - Name: ansible-server
	- Hostname: <Ansible-Server-Private-IP>
	- username: ansadmin
  -  Advanced > choose Use password authentication, or use a different key Password: *******
  -  Apply > Save

### Create Deply_on_Container_using_Ansible on Jenkins
- Enter an item name: Deploy_on_Container_using_ansible
  - Copy from: Deploy_on_Container 
- *Source Code Management:*
  - Repository: https://github.com/RyanADouglas/hello-world.git
  - Branches to build : */master
- *Poll SCM* : * * * * *
- *Build:*
  - Root POM: pom.xml
  - Goals and options: clean install

- *Post-build Actions*
- Send build artifacts over SSH
- *SSH Publishers*
  - SSH Server Name: ansible-server
  - Transfers >  Transfer set
  - Source files: webapp/target/*.war
	- Remove prefix: webapp/target
  - Remote directory: //opt//docker
	- Exec command: 
   ```sh 
   ansible-playbook -i /opt/docker/hosts /opt/docker/create-docker-image.yml;
   ```
- Apply > Save

### Create OPT/DOCKER on Ansible Server
- On Ansible Server
  ```sh
  cd /opt/
  mkdir docker
- Change docker ownership to ansadmin
  ```sh
  chown ansadmin:ansadmin docker
  ```
