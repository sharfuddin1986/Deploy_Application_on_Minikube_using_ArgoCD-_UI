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

Step-2       ####### Install Minikube #############

   
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
       
Step-3     #######  Install Kubectl ##################

         sudo snap install kubectl --classic
         kubectl version

Step-4     ######## Install ArgoCD  ##################

       kubectl create namespace argocd
       kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
       kubectl get pod -n argocd
       kubectl port-forward svc/argocd-server -n argocd --address 0.0.0.0 8080:443
       
       After Port forwading need to access through Public ip of ec2 instance with port
       https://54.87.56.123:8080/
       Retrieve the initial admin password for ArgoCD:
       kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

       
   ![1.png](https://github.com/user-attachments/assets/0a6ef1e5-3fd3-4fc9-81b1-d09e793f3210)
   ![2.jpg](https://github.com/user-attachments/assets/68fc010f-8ccb-4127-b48f-f983a067fb10)
   ![3.jpg](https://github.com/user-attachments/assets/9fa69d0e-fc83-4525-ac12-fb1c65e396d9)
 

Step-5    ####### Deploy Guest book Applicaion  from ArgoCD UI ####################

       Deploy your first application using deployment.yaml
       Click new app + button 
       Application name-helm-guestbook 
       Project name-default
       sync policy-manual
       source Repository-https://github.com/argoproj/argocd-example-apps
       Path-helm-guestbook
       Destination-https://kubernetes.default.svc  (Bydefault come)
       Namespace-default      (Because i set default namespace in minikube)
       Create
       click app  then sync after syncronise click
       kubectl get pods
       kubectl get svc
       kubectl get deploy
       Need to access application with specific port

      kubectl port-forward --address 0.0.0.0 svc/helm-guestbook 9090:80
      http://54.87.56.123:9090/
      After that Application is runing and working fine
      
         
       
       
