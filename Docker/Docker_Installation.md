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
- Create docker amdin user
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
  
