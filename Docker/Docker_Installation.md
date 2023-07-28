# Install Docker on Amazon EC2
### Installation Steps
- Create EC2 Instance (Follow steps from previous sections)
- Install docker and start docker services (Run as root)
  ```sh
  sudo su -
  yum install docker -y

  # start docker services
  service docker start
  # Verify docker has started
  service docker status
  ```
- Create docker admin user
  ```sh
  useradd dockeradmin
  passwd dockeradmin
  ```
- Add docker user to docker group to manage docker
  ```sh
  usermod -aG docker dockeradmin

### Test Docker
- Pull Tomcat image and build docker container
  ```sh
  docker pull tomcat
  docker run -d --name tomcat-container -p 8081:8080 tomcat
  ```
### Access Container
- Copy Docker Public-Ip with container port into web browser
  ```sh
  Docker-Server-Public-Ip:8081
  ```
- Container will not be succesful due to security group restraints. To resolve issue, proceed to AWS Console > Security Groups > Select Security Group > Inbound Rules > Edit Inbound Rules
- Add Rule to allow port 8081 - 9000 (To allow future ports)
![Security Group](https://github.com/RyanADouglas/DevOpsProject/assets/136330853/9f494556-8bf2-4d57-8c89-978e443a9bb3)
- Now Tomcat container will show a 404 error which is fine because you have succesfully reached Tomcact

### Fix Tomcat Issue
- Run following commands to resolve 404 issue
  ```sh
  docker exec -it tomcat-container /bin/bash
  cd webapps.dist
  cp -R * ../webapps/
  ```
- Verify you can access Tomcat via web browser
  
