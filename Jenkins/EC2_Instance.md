# Jenkins Server
- Create Linux EC2 Instance
  
![Launch Jenkins Server Instance -1](https://github.com/RyanADouglas/DevOpsProject/assets/136330853/d69b10fc-11aa-4240-995e-9c4b48317dfe)

![Jenkins Security Group -2](https://github.com/RyanADouglas/DevOpsProject/assets/136330853/9feddb61-a684-48dc-86cf-dad280f095f3)

- You may use the default Security Group or Create your own. However, we will need to, add a security group rule by selecting "Add security group rule." Add Port 8080 from source 0.0.0.0/0 due to Jenkins running on port 8080.
  
- The Default storage will remain as default and select launch instance.

![Jenkins Server IP address - 4](https://github.com/RyanADouglas/DevOpsProject/assets/136330853/5382b1ff-e897-472e-adf8-4f1ce0f41e97)

- Once the Instance is running we will use the Public IPv4 address to ssh into our instance.
- First open your terminal and change the permissions of your key file to read-only by using
  ```sh
  chmod 400 "EC2key.pem"
  ```
- Next we will ssh into our instance with the following command:
  ```sh
  ssh -i "EC2key.pem" ec2-user@3.95.199.165
  ```
![ssh command](https://github.com/RyanADouglas/DevOpsProject/assets/136330853/b3216dc5-a0c7-477d-a60d-b056f7ada7bb)
