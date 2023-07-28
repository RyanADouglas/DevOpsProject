# Deploy on Docker host server using Jenkins 

### Configure Docker host to use password base authentication
- Log into Docker host and become root
  ```sh
  sudo su -
  ```
- Edit sshd_config
  ```sh
  vi /etc/ssh/sshd_config
  ```
- uncomment PasswordAuthintication Yes
- comment PasswordAuthentication No
<img width="448" alt="sshd_config" src="https://github.com/RyanADouglas/DevOpsProject/assets/136330853/62ef2e0d-dec6-473d-9591-2642fe8d01a4">

- Reload sshd service
  ```shh
  service sshd reload
  ```

### Configuration between Docker-host and Jenkins

Install "publish Over SSH"
 - Manage Jenkins > Plugins > Available > Publish over SSH

Enable connection between Docker-host and Jenkins

- Manage Jenkins > Configure System > Publish Over SSH > SSH Servers

	- SSH Servers:
                - Name: docker-host
		- Hostname: ServerIP
		- username: dockeradmin
               
       -  Advanced > choose use password authentication, or use a different key
		 - password: *******
 
### Steps to create "Deploy_on_Docker_Host" Jenkin job
 #### From Jenkins home page select "New Item"
   - Enter an item name: `Deploy_on_Docker_Host`
     - Copy from: `Deploy_on_Tomcat_Server`
     
   - *Source Code Management:*
      - Repository: `https://github.com/yankils/hello-world.git`
      - Branches to build : `*/master`  
   - *Poll SCM* :      - `* * * *`

   - *Build:*
     - Root POM:`pom.xml`
     - Goals and options: `clean install package`

 - *Post-build Actions*
   - Send build artifacts over SSH
     - *SSH Publishers*
      - SSH Server Name: `docker-host`
       - `Transfers` >  `Transfer set`
            - Source files: `webapp/target/*.war`
	       - Remove prefix: `webapp/target`
	       - Remote directory: `//home//ansadmin` or `.`
	 

Save and run the job now.
