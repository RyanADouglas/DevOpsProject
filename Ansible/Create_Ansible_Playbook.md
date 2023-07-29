# Ansible Playbook
### Create Hosts
- Edit hosts file
  ```sh
  vi /etc/ansible/hosts
  add ansible server private ip
  ```
<img width="204" alt="Hosts" src="https://github.com/RyanADouglas/DevOpsProject/assets/136330853/54212fbe-6266-4851-a309-6b7f4b804fc6">

### Copy ansadmin ssh key onto ansible
- Become ansadmin if you are nnot
  ```sh
  sudo su - ansadmin
  ssh-copy-id "Ansible Server Private-Ip
  ```
### Ansible Playbook to create image
- Create playbook
  ```sh
  vi regapp.yml
  ---
  - hosts: ansible
    tasks:
    - name: create docker image
      command: docker build -t regapp:latest .
      args:
        chdir: /opt/docker
  ```
- Run ansible playbook
  ```sh
  ansible-playbook regapp.yml
  ```

### Login to Docker via cli
- Login to Docker
  ```sh
  docker login
  ```
- Enter Docker Credentials

### Push Image to Docker
- Create image
  ```sh
  docker tag "Image ID" "Dockerusername"/regapp:latest
  docker push Dockerusername/regapp:latest
  ```
