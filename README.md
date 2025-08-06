# Kubernetes & DevOps Advanced Assignment
This repository contains the solution for the Kubernetes & DevOps Advanced assignment for the NAGP 2025 Technology Band III.

# Getting Started
To deploy the solution, follow these steps:

1. Set up a Kubernetes cluster.
2. Run the GitHub Action to build the Docker image for the API project using the provided Dockerfile and push the Docker image to the *iyashvsrathore* Docker Hub repository.
3. Configure the necessary environment variables and secrets using the provided deployment files (*~/.K8s/Configuration & Secret*).
    1. `$ kubectl apply -f configmap.yaml`
    2. `$ kubectl apply -f secret.yaml`
4. Create the Volumes and Storage using the provided deployment files (*~/.K8s/Volumes*).
    1. `$ kubectl apply -f persistent-volume-claim.yaml`
    2. `$ kubectl apply -f storage-class.yaml`
5. Deploy the database and its services on the Kubernetes cluster using the provided deployment files (*~/.K8s/Database*).
    1. `$ kubectl apply -f database-deployment.yaml`
    2. `$ kubectl apply -f database-service.yaml`
6. Create the Database and Tables in the Database using the following commands.\
    
    `SA_PASSWORD=$(kubectl get secret SA_PASSWORD -o jsonpath='{.data.<data-key>}' | base64 --decode)`
   
    `kubectl exec -it <pod-name> -- /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P $SA_PASSWORD -Q 'CREATE DATABASE [User]'`
   
    `kubectl exec -it <pod-name> -- /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P &SA_PASSWORD -Q 'use [User] CREATE TABLE [Users]
      (
          [Id] INT NOT NULL PRIMARY KEY, 
          [Username] NVARCHAR(50) NULL, 
          [Name] NVARCHAR(100) NULL, 
          [EmailID] NVARCHAR(100) NULL
      )'`
7. Install the ingress controller:
    `kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.9.4/deploy/static/provider/cloud/deploy.yaml`
8. Deploy the microservice and its services on the Kubernetes cluster using the provided deployment files (*~/.K8s/Microservice*).
    1. `$ kubectl apply -f api-deployment.yaml`
    2. `$ kubectl apply -f api-service.yaml`
9. Deploy ingress:
    `$ kubectl apply -f api-ingress.yaml`
10. Access the API from outside the cluster using the Ingress Controller external IP.


# Important Resources

## Link for the code repository :
[https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps)


## Docker hub URL for docker images
1. Dot Net API Docker Image: https://hub.docker.com/r/iyashvsrathore/nagp2025kubernetesassignment/tags
2. SQL Server Docker Image: https://hub.docker.com/_/microsoft-mssql-server

## Demo Recording Video URL
https://nagarro-my.sharepoint.com/:v:/r/personal/yash_rathore_nagarro_com/Documents/NAGP%202025/NAGP%202025%20Technology%20band%20III%20-%20Kubernetes%20%26%20DevOps%20YASH%20RATHORE/YashRathore_3183274_Kubernetes_and_DevOps_Advance_Demo_Recording.mp4?csf=1&web=1&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=2EfXGA


## Docker File Path
[Docker File](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/NAGPK8s-2025/Dockerfile): https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/NAGPK8s-2025/Dockerfile


## Kubernetes YAML Files

1. [API Deployment](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Microservice/api-deployment.yaml) File
2. [API Service](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Microservice/api-service.yaml) File
3. [Ingress](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Microservice/api-ingress.yaml) File
4. [Database Deployment](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Database/database-deployment.yaml) File
5. [Database Service](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Database/database-service.yaml) File
6. [Persistence Volume Claim](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Volumes/persistent-volume-claim.yaml) File:
7. [Storage Class](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Volumes/storage-class.yaml) File
8. [Config Map](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Configuration%20%26%20Secret/configmap.yaml) File
9. [Secret](https://github.com/iYashvsRathore/NAGP-2025-Kubernetes-DevOps/blob/master/.K8s/Configuration%20%26%20Secret/secret.yaml) File

