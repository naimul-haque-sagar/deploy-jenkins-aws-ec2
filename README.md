# Deploy-jenkins-aws-ec2

# Install docker in ec2
  
**`sudo apt update`**\
**`sudo apt install apt-transport-https ca-certificates curl software-properties-common`**\
**`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`**\
**`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"`**\
**`apt-cache policy docker-ce`**\
**`sudo apt install docker-ce`**\
**`sudo systemctl status docker`**

# Run docker without sudo permission
**`sudo groupadd docker`**\
**`sudo usermod -aG docker $USER`**\
**`newgrp docker`**


# Docker common commands
  
  To delete all containers including its volumes use \
  **`docker rm -vf $(docker ps -aq)`**
    
  To delete all the images\
  **`docker rmi -f $(docker images -aq)`**

# Pull jenkins image from dockerhub

  **`docker pull jenkins/jenkins`**
  
# Run jenkins image 
  **`docker run --detach --name my-jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins`**
  
# Access jenkins image
  **`docker exec -it my-jenkins /bin/bash`**
  
# Get jenkins initial password
  **`cd /var/jenkins_home/secrets/`**\
  **`cat initialAdminPassword`**
  By using cat command you will get initial password\
  
# Run your jenkins 
  **`your-ec2-public-ip:8080`**\
  Now you will see jenkins home page\ 
  Paste the password here\
  And finally you are logged in\
  
# Congratulations you can use jenkins and create pipeline as your needs


