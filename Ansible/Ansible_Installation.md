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
