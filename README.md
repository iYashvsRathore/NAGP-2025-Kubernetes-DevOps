# Kubernetes & DevOps Advanced Assignment
This repository contains the solution for the Kubernetes & DevOps Advanced assignment for the NAGP 2025 Technology Band III.

# Getting Started
To deploy the solution, follow these steps:

1. Set up a Kubernetes cluster.
2. Run the GitHub Action to build the Docker image for the API project using the provided Dockerfile and Push the Docker image to *iyashvsrathore* Docker Hub repository.
3. Configure the necessary environment variables and secrets using the provided deployment files (*~/.K8s/Configuration & Secret*).
    1. `$ kubectl apply -f configmap.yaml`
    2. `$ kubectl apply -f secret.yaml`
4. Create the Volumes and Storage using the provided deployment files (*~/.K8s/Volumes*).
    1. `$ kubectl apply -f persistent-volume-claim.yaml`
    2. `$ kubectl apply -f storage-class.yaml`
5. Deploy the microservice and database and their services on the Kubernetes cluster using the provided deployment files (*~/.K8s/Microservice* and *~/.K8s/Database*).
    1. `$ kubectl apply -f api-deployment.yaml`
    2. `$ kubectl apply -f api-service.yaml`
    3. `$ kubectl apply -f database-deployment.yaml`
    4. `$ kubectl apply -f database-service.yaml`
6. Create the Database and Tables in the Database using folowwing commands.\
    
    `SA_PASSWORD=$(kubectl get secret SA_PASSWORD -o jsonpath='{.data.<data-key>}' | base64 --decode)`
   
    `kubectl exec -it <pod-name> -- /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P $SA_PASSWORD -Q 'CREATE DATABASE [User]'`
   
    `kubectl exec -it <pod-name> -- /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P &SA_PASSWORD -Q 'use [User] CREATE TABLE [Users]
      (
          [Id] INT NOT NULL PRIMARY KEY, 
          [Username] NVARCHAR(50) NULL, 
          [Name] NVARCHAR(100) NULL, 
          [EmailID] NVARCHAR(100) NULL
      )'`
8. Access the API from outside the cluster using the LoadBalancer service.


# Important Resources

## Link for the code repository :


## Docker hub URL for docker images
1. Dot Net API Docker Image: https://hub.docker.com/r/iyashvsrathore/nagpkubernetesassignment/tags
2. SQL Server Docker Image: https://hub.docker.com/_/microsoft-mssql-server

## Demo Recording Video URL


## Docker File Path


## Kubernetes YAML Files
