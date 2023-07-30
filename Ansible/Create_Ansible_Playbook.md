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
    - name: create tag to push image onto dockerhub
      command: docker tag regapp:latest nayrx07/regapp:latest
    - name: push docker image
      command: docker push nayrx07/regapp:latest 
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
### Create Container using Ansible Playbook
- Create docker_deployment.yml
```sh
 ---
- hosts: dockerhost

  tasks:
  - name: stop existing container
    command: docker stop regapp-server
    ignore_errors: yes

  - name: remove the container
    command: docker rm regapp-server
    ignore_errors: yes

  - name: remove image
    command: docker rmi nayrx07/regapp:latest
    ignore_errors: yes

  - name: create container
    command: docker run -d --name regapp-server -p 8082:8080 nayrx07/regapp:latest
  ```
