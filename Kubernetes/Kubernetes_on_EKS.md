EKS Is not a free service; If service is not needed delete cluster to not incur charges.

# Kubernetes on EKS
- Create EC2 Instance

### Update AWS CLI
- Update CLI
  ```sh
  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
  unzip awscliv2.zip
  ```

### Install kubectl
- Install kubectl
  ```sh
  sudo su -
  curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.27.1/2023-04-19/bin/linux/amd64/kubectl
  chmod +x kubectl
  mv kubectl /usr/local/bin
  ```

### Install eksctl
- Install eksctl
  ```sh
  sudo su -
  curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"
  tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz
  mv eksctl /usr/local/bin

### Create IAM Role 
- In AWS Console:
  - Search IAM > Roles > Create Role > AWS Service > Common Use Cases > EC2
  - Add following roles:
    - IAM
    - EC2
    - CloudFormation
   <img width="931" alt="IAM" src="https://github.com/RyanADouglas/DevOpsProject/assets/136330853/6478d37a-7bff-43f4-91a0-f72473fcb407">

### Create Cluster Node
- Create Cluster
  ```sh
  eksctl create cluster --name "Name of Cluster" \
  --region "Region-Name" \
  --node-type "Instance-Type"
  ```
### To delete eks cluster
  ```sh
  eksctl delete cluster "Name of Cluster" --region "Region-Name"
  ```
  
