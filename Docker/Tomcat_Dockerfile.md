# Tomcat Dockerfile
- Dockerfile to install tomcat
  ```sh
  FROM tomat
  RUN cp -R /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps
  COPY ./webapp.war /usr/local/tomcat/webapps
  ```
### Build Docker Image
- Build image using dockerfile
  ```sh
  docker build -t "name of image(demotomcat)" .

### Build Tomcat Container
- Build Container
  ```sh
  docker run -d --name "container name (demotomcat-container)" -p 8085:8080 demotomcat
  ```
  

