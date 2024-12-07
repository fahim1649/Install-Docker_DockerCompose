# DOCKER INSTALLATION


 #!/bin/bash

#Update package list

sudo apt update

#Install necessary packages

sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

#Add Docker's official GPG key

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

#Add Docker repository to apt sources

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#Update package list again to include Docker repository

sudo apt update

#Check Docker package versions available
apt-cache policy docker-ce

#Install Docker
sudo apt install -y docker-ce

#Check Docker service start
sudo systemctl start docker

#Install Docker Compose
mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/download/v2.3.3/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
chmod +x ~/.docker/cli-plugins/docker-compose

#Check Docker Compose version
docker compose version
