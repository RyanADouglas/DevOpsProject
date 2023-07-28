# Deploy on a Tomcat server

### Creating Jenkins Job

### Install deploy to container plugin. This plugin needs to deploy on Tomcat server. 

- Install deploy to container plugin without restart  
    - Manage Jenkins > Plugins > available plugins > deploy to container
  
- Configure Jenkins credentials
  - Manage Jenkins > Jenkins > Credentials > System > Global Credentials > Add Credentials
    - Username	: deployer
    - Password : deployer
    - id      :  deployer
    - Description: deploy on tomcat

### Create BuildAndDepolyJob
 - Select New Item
   - Enter an item name: BuildAndDeployJob
   - Select Maven Project
   
 - *Source Code Management:*
      - Repository: https://github.com/RyanADouglas/hello-world.git
      - Branches to build : */master
   - *Poll SCM* : * * * * *

   - *Build:*
     - Root POM:pom.xml
     - Goals and options: clean install

 - *Post-build Actions*
   - Deploy war/ear to container
      - WAR/EAR files : **/*.war
      - Containers : Tomcat 8.x
         - Credentials: deployer (user created on above)
         - Tomcat URL : http://<PUBLIC_IP>:8080

Apply and save, run the job now.
