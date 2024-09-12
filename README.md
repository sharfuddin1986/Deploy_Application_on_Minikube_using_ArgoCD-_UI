# Deploy_Application_on_Minikube_using_ArgoCD_UI

# Prerequisite:
  
  Install Docker 
  
  Install minikube
  
  Install kubectl

  
Step-1        ####### Install Docker ########

       page link  for installation of docker 
       https://docs.docker.com/engine/install/ubuntu/

       sudo apt-get update
       sudo apt-get install ca-certificates curl
       sudo install -m 0755 -d /etc/apt/keyrings
       sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
       sudo chmod a+r /etc/apt/keyrings/docker.asc
       echo \
       "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
       $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
       sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
       sudo apt-get update
       sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
       docker --version
       Docker version 27.2.1, build 9e34c9b

Step-2        ####### Install Minikube ########

   
       page link  for installation of minikube 
       https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download

       curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
       sudo install minikube-linux-amd64 /usr/local/bin/minikube
       sudo chmod 777 /var/run/docker.sock  
       cd /usr/local/bin/
       minikube version
       minikube start --driver=docker
       Start Minikube and Check Status:
       minikube start
       minikube status
       
