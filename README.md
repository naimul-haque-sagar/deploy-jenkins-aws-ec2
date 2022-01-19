# Deploy-jenkins-aws-ec2

# Install docker in ec2
  
**`sudo apt update`**

**`sudo apt install apt-transport-https ca-certificates curl software-properties-common`**

**`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`**

**`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"`**

**`apt-cache policy docker-ce`**

**`sudo apt install docker-ce`**

**`sudo systemctl status docker`**

# Run docker without sudo permission

**`sudo groupadd docker`**

**`sudo usermod -aG docker $USER`**

**`newgrp docker`**


# Docker common commands
  
  To delete all containers including its volumes use \
  **`docker rm -vf $(docker ps -aq)`**
    
  To delete all the images\
  **`docker rmi -f $(docker images -aq)`**

  Force remove images\
  **`docker rmi -f <image_id> `**
  
  See docker container logs\
  **`docker logs --details <container-name>`**
  
  Run image with env value\
  **`docker run --name service-discovery-8761 -d -p 80:8761 -e ENVIRONMENT=peeronedev service-discovery-8761`**
  
# You can Directly Pull jenkins image and run

  **`docker pull jenkins/jenkins`**

  **`docker run --detach --name my-jenkins -p 80:8080 -p 50000:50000 jenkins/jenkins`**
  
# Or Download and run Jenkins in Docker (DIND)

  **`docker network create jenkins`**
  
  **`docker run --name docker-dind --detach --privileged --network jenkins --network-alias docker 
     --env DOCKER_TLS_CERTDIR=/certs --volume jenkins-docker-certs:/certs/client --volume 
     jenkins-data:/var/jenkins_home --publish 2376:2376 docker:dind --storage-driver overlay2`**
     
  **`docker pull jenkins/jenkins`** or  Write or Copy the jenkins Dockerfile and build
  
  **`docker run --name jenkins-server --detach --network jenkins --env DOCKER_HOST=tcp://docker:2376 
     --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 --publish 80:8080 
     --publish 50000:50000 --volume jenkins-data:/var/jenkins_home --volume jenkins-docker-certs:/certs/client:ro jenkins/jenkins`**
  
# Access jenkins image

  **`docker exec -it <image name> /bin/bash`**
  
# Get jenkins initial password

  **`cd /var/jenkins_home/secrets/`**
  
  **`cat initialAdminPassword`**
  
  By using cat command you will get initial password
  
# Run your jenkins 

  **`your-ec2-public-ip`**
  
  Now you will see jenkins home page
  
  Paste the password here
  
  And finally you are logged in
  
# Congratulations you can use jenkins and create pipeline as your needs


