# Deploy-jenkins-aws-ec2

# Docker common commands
  
  To delete all containers including its volumes use \
  **`docker rm -vf $(docker ps -aq)`**
    
  To delete all the images\
  **`docker rmi -f $(docker images -aq)`**

# Download jenkins from dockerhub

  **`docker pull jenkins:2.60.3-alpine`**
  
# Run jenkins image 
  **`docker run --detach --name jenkins-container -p 8080:8080 -p 50000:50000 jenkins:2.60.3-alpine`**
  
# Access docker image
  **`docker exec -it jenkins-container /bin/bash`**
  
# Get initial password
  **`cd /var/jenkins_home/secrets/\`**
  **`cat initialAdminPassword\`**
  By using cat command you will get initial password\
  
# Run your jenkins 
  **`127.0.0.1:8080`**\
  Now you will see jenkins home page\ 
  Paste the password here\
  And finally you are logged in\
  
# Congratulations you can use jenkins


