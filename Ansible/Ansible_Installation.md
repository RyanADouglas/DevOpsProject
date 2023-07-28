# Ansible Installation
### Create EC2 Instance
- Create EC2 Instance
- Add previous security group; Ansible runs on Port 22

### Configure Ansible Server
- Create ansadmin user (on Control node and Managed host)
  ```sh
  sudo su -
  useradd ansadmin
  passwd ansadmin
  ```
- Grant sudo access to ansadmin
  ```sh
  visudo
  ```
- under ## Same thing without a password #% wheel ... add
  ```sh
  ansadmin ALL=(ALL) NOPASSWD: ALL
  ```
<img width="446" alt="Visudo" src="https://github.com/RyanADouglas/DevOpsProject/assets/136330853/9e2e93db-27fd-45ad-b4da-335e65543564">

- Edit sshd_config
  ```sh
  vi /etc/ssh/sshd_config
  ```
- uncomment PasswordAuthintication Yes
- comment PasswordAuthentication No
<img width="448" alt="sshd_config" src="https://github.com/RyanADouglas/DevOpsProject/assets/136330853/62ef2e0d-dec6-473d-9591-2642fe8d01a4">
- Reload sshd service
  ```sh
  service sshd reload
  ```
- Log into ansible server as ansadmin
  ```sh
  sudo su - ansadmin
  ```
- Generate ssh key
  ```sh
  ssh-keygen
  ```
- Install Ansible
  ```sh
  amazon-linux-extras install ansible2
  ```
- Create ansadmin user on Docker Server
  - ssh into Docker Server
  ```sh
  sudo su -
  useradd ansadmin
  passwd ansadmin
  ```
- Grant sudo access to ansadmin
  ```sh
  visudo
  ```
- under ## Same thing without a password #% wheel ... add
  ```sh
  ansadmin ALL=(ALL) NOPASSWD: ALL
  ```
<img width="446" alt="Visudo" src="https://github.com/RyanADouglas/DevOpsProject/assets/136330853/9e2e93db-27fd-45ad-b4da-335e65543564">

- Log Back into Ansible Server
- Add Docker Server as Manage Host
  ```sh
  vi /etc/ansible/hosts
  Add Private Ip of Docker Server to file
  ```
- Copy ansadmin ssh key onto Docker Server
  - sudo su - ansadmin
  - ssh-copy-id "Private Ip of DockerHost"
  
