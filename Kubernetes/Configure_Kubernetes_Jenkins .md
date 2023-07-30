# Configue Kubernetes on Jenkins

### Registration_App_CD Job
- Select "New Item" from Jenkins Dashboard
- Enter name: Registration_App_Cd
- Freestyle Project
- Post-build Actions
  - Send build artifacts over SSH
  - SSH Publishers
  - Exec command:
    ```sh
    ansible-playbook -i /opt/docker/hosts /opt/docker/kube_deploy.yml;
    ```
### Registration_App_CI Job
- Select "New Item" from Jenkins Dashboard
- Enter name: Registration_App_CI
- Freestyle Project
- Source Code Managemet
  - Git
  - Repository URL: https://github.com/RyanADouglas/hello-world.git
- Build Triggers
  - Poll SCM: * * * * * 
- Post-build Actions
  - Send build artifacts over SSH
  - SSH Publishers
  - Exec command:
    ```sh
    ansible-playbook /opt/docker/create_image_regapp.yml;
    ```
