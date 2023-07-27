# Tomcat Installation

### Install Apache Tomcat
- Create EC2 Instance (Can follow steps from Jenkins instructions)
- Install Java 11 on Tomcat Server
  ```sh
  amazon-linux-extras install java-openjdk11
  ```
- Download tomcat from https://tomcat.apache.org/download-90.cgi
  ```sh
  # Create tomcat directory
  cd /opt
  wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.78/bin/apache-tomcat-9.0.78.tar.gz.sha512
  tar -xvzf apache-tomcat-9.0.78.tar.gz
  mv apache-tomcat-9.0.78 tomcat
  cd tomcat/
  ```

- To start and stop tomcat
    ```sh
    # In the tomcat directory
    cd bin
    # start tomcat
    ./startup.sh
    # stop tomcat
    ./shutdown.sh
    ```
- Check tomcat is running:
  ```sh
  http://"TomcatServerPublic-Ip:8080
  # Although Jenkins is running on port 8080 we can access Tomcat on 8080 due 
  to Tomcat being another server
  ```
- Once on the Tomcat homepage if you attempt to access the Manager App or the Host Manager, it will provide a 403 Access Denied. To resolve the issue follow these commands:
  ```sh
  cd tomcat
  find / -name context.xml
  # we will edit both files:
  # /opt/tomcat/webapps/host-manager/META-INF/context.xml
  # /opt/tomcat/webapps/manager/META-INF/context.xml
  # comment out by adding <!-- before <Valve and after /> --> in both context.xml files
  ```
![Tomcat context](https://github.com/RyanADouglas/DevOpsProject/assets/136330853/294b53a2-4684-4282-84f0-e7acd0c9579e)

- Restart Tomcat and it should then ask for credentials to log in
- Update the tomcat-users.xml file with the following information
  ```sh
  For the demo I used simple passwords, you may choose your own password
  <role rolename="manager-gui"/>
  <role rolename="manager-script"/>
  <role rolename="manager-jmx"/>
  <role rolename="manager-status"/>
  <user username="admin" password="admin" roles="manager-gui, manager-script, manager-jmx, manager-status"/>
  <user username="deployer" password="deployer" roles="manager-script"/>
  <user username="tomcat" password="tomcat" roles="manager-gui"/>
  ```
![tomcat-users](https://github.com/RyanADouglas/DevOpsProject/assets/136330853/f34c4554-63cd-4555-9759-140da5e89bad)

