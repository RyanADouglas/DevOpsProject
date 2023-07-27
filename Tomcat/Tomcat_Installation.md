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
