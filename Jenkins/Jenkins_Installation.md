# Install Jenkins on AWS EC2

### Jenkins Installation
- Download the latest version of jenkins from https://pkg.jenkins.io/redhat-stable/ and install. In this demo I used Red Hat/CentOS. Then execute the following commands:
  ```sh
  sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
  sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

  yum install fontconfig java-11-openjdk
  yum install jenkins
  ```
### Start Jenkins
  ```sh
  service jenkins start

  # To check if jenkins is running
  service jenkins status
  ```

### Accessing Jenkins
- Once Jenkins is running, select your Jenkins Server Public IP address, open your web browser and enter http://Jenkins-Server-Public-IP:8080
- Default username is "admin"
- Default Password is located in /var/lib/jenkins/secrets/initialAdminPassword
  ```sh
  cat /var/lib/jenkins/secrets/initialAdminPassword
  ```
### Configuring Jenkins
- To change password select: Admin > Configure > Password
