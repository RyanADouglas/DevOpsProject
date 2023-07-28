# Tomcat Dockerfile
- Dockerfile to install tomcat on centos
  ```sh
  # using centos 8 will have an issue when downloading, instead use centos:7
  FROM centos:7
  RUN yum install java -y
  RUN mkdir /opt/tomcat/
  WORKDIR /opt/tomcat
  ADD https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.54/bin/apache-tomcat-9.0.54.tar.gz /opt/tomcat
  RUN tar xvfz apache*.tar.gz
  RUN mv apache-tomcat-9.0.54/* /opt/tomcat 
  EXPOSE 8080
  CMD ["/opt/tomcat/bin/catalina.sh", "run"]
  ```
### Build Docker Image
- Build image using dockerfile
  ```sh
  docker build -t "name of image(mytomcat)" .

### Build Tomcat Container
- Build Container
- docker run -d --name "container name (mytomcat-server)" -p 8083:8080 mytomcat
- 
  

