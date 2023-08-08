# Be-MLE
Become a Machine Learning Engineer Project. 
## Table of Contents.
  * [Deplyment Link](#deployment-link)
  * [Credentials for the login/signin](#testing-credentials)
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Purpose](#purpose)
  * [Demo Video](#demo-video)
  * [Architecture Design](#bemle-architecture-design)
  * [Flow Diagram](#bemle-flow-diagram)
  * [Technical Aspect](#technical-aspect)
  * [Admin Portal](#admin-portal)
  * [Continous Integrations](#continous-integrations)
  * [Continous Deployments](#continous-deployments)
  * [Environment Variables](#environment-variables)
  * [Installation](#installation)
  * [Run](#run)
  * [Docker](#docker-setup)
  * [Run with anaconda environments](#to-run-main-bemle-with-anaconda-environments)
  * [Kubernatives BeMLE Local SetUp with minikube](#local-setup-with-minikube)
  * [Kubernatives BeMLE Cloud SetUP with eksctl](#kubernatives-cloud-setup)
  * [License](#license)
## Deployment Link 
- Deployment is done on ec2 AWS  <a href= http://35.194.69.17:5000/ target="_blank"> Click here</a>
## Testing Credentials
#### Note: Credentials for the login/signin page but we strongly encouraged you to signUp
| Email | Password |
| :---: | :---: |
| be.mle.project@gmail.com | <i>bemleproject </i> |
## Overview
Machine Learning process is tiresome process where you get a decent dataset, preprocess it, deal with null values, standardize or normalize the data then pick a decent model to
train it. Be MLE (Become a Machine Learning) is a system that automates the process a normal
machine learning engineer goes through in his/her job.

### Login/SignUp page
<img width="960" alt="bemle_login" src="https://user-images.githubusercontent.com/62692329/216952140-93c0ad77-64f9-494c-9d90-d0716c737a3f.png">


## Motivation
With the growing scope of Machine Learning and Deep Learning, it is a must in most of the applications we use. From recommendation systems to smart searches, from prediction systems to computer vision AI and ML is being used in most of the software's we interact with in our daily life. Our system is supposed to help all those developers around the globe that need an AI module in their system but don’t have any/little bit knowledge of machine learning. With our system everyone will become a machine learning engineer.
## Purpose
Machine Learning is a blooming discipline of the present times. Almost every application or system we use have involvement of AI one way or another. From recommender systems to weather predictions machine learning is an essential part of new systems being developed. BeMLE makes it easy for a software developer to get the AI part of the app done with easy. The system takes data and trains a bunch of models on its own and provides with the best model. This way the software developer need not to know anything about the working of machine learning, which model to choose, what hyperparameters to set or how to maximize the accuracy. With BeMLE developers will get trained models on provided data.
## Demo Video
<p align="center">
<img src="https://user-images.githubusercontent.com/62692329/216953315-b2a608de-2a18-493a-bd8e-fefa5a4ca16b.gif" alt="demo_video" />
</p>

## BeMLE Architecture Design
High Level Architecture Design.
![BEMLE drawio (3)](https://user-images.githubusercontent.com/62692329/216922231-2ba730e7-82b3-4cd7-ab58-fb2d0d8e7c11.png)

## BeMLE Flow Diagram
![image](https://user-images.githubusercontent.com/62692329/216988017-c7d03459-2384-49e0-89c0-955e02354eb1.png)

## Technical Aspect
This project is divided into five part:
1. Processing Data, Analyzing, Training, Storing, using different Machine Learning And Deep Learning(Neaural Networks) Techniques.
2. Building deployed, and hosting a Flask web app on Amazon Web Services(AWS)( http://35.194.69.17:5000/ ). And also Deploying on Kubernatives.
3. Microservice Level Architecture.
4. [CircleCI](#continous-integrations) for continous integration
5. [ArgoCD](#continous-deployments) for continous Deployment

## Admin Portal
To see logs of the apps we aso create an admin portal so that we keep records of the steps taken by the user or system and is used to detect error so the admins will know where and in which project module/microservice/line the system faces errors. In short Admins, can check Loggings to see system status at each point of time. It helps for the admin to detect problems and eventually to solve them.

![ezgif com-video-to-gif (1)](https://user-images.githubusercontent.com/62692329/217845329-4a0e500b-028e-4471-9128-b5fcbfb7f698.gif)

## Continous Integrations
For contiouns Integration we use CircleCI pipelines
#### CircleCI Responsibilities
1. Unit Testing, for this I use pytest
2. If all test pass then it will create docker containers of all the microservices.
3. After creating, it will push all these containers to DockerHub.
4. Deply these applications to ec2 instance (by pulling these containers from dockerhub, and setting their environment variables via script).
#### CircleCI builds
<img width="960" alt="circleci" src="https://user-images.githubusercontent.com/62692329/216989836-809c31da-98ba-408b-b9c9-25548239d1ae.png">

## Continous Deployments
For continous deployment, we use ArgoCD.
#### ArgoCD Responsibilities
1. Monitors progress and when the Kubernetes cluster is ready, reports that the application is in sync.
2. Continously see the repo after every 3 minutes and deploy the changes if there is any.
3. Change the pod deployment in kubernatives if we change the version in k8 branch of GitHub.
#### ArgoCD
![argocd (1)](https://user-images.githubusercontent.com/62692329/217079906-199bf7b7-dc23-45de-b49d-2d1bcb1a9078.gif)

## Environment Variables
#### Project Environment Variables
| Variable Name | Description |
| :---: | :---: |
| AWS_ACCESS_KEY_ID | <i>AWS ACESS KEY Credential, can get from IAM </i> |
| AWS_SECRET_ACCESS_KEY | <i>AWS SECRET ACESS KEY Credential, can get from IAM </i> |
| MONGODB_CLUSTER_CONNECTION_STRING | <i>MongoDB connection String To acess mongodb for logs or user informations </i> |
| ML_API_HOSTNAME_WITH_PORT | <i>Add the ML API APP link, so that BeMLE can acess it when user wants to predict </i> |
| PRIVATE_KEY_LINK | <i>Add the private key to acess EC2 instance for premium user </i> |
#### <a href= https://github.com/IamVicky90/Be-MLE/blob/main/config/params.yaml target="_blank"> Configurations</a> of the Project
``` yaml
db:
  dbname: BeMle
  ML_COLLECTION_NAME: BeMle-ML
  contact_us: contact_us
  user_credentials_collection_name: user_credentials
  COMMON_COLLECTION_NAME: common_resources
timeZone:
  "Asia/Karachi"
emails:
  sender_email: "vickyaiproduction@gmail.com"
environment_variables:
  ENVIRONMENT_VARIABLE_FOR_MONGODB_CLUSTER_CONNECTION_STRING: MONGODB_CLUSTER_CONNECTION_STRING
  ENVIRONMENT_VARIABLE_EMAIL_PASSWORD: MAIL_PASSWORD
  ENVIRONMENT_VARIABLE_ML_API_LINK: ML_API_HOSTNAME_WITH_PORT
  ENVIRONMENT_VARIABLE_PRIVATE_KEY_LINK: PRIVATE_KEY_LINK
feature_store:
  bucket_name: my-bemle-0
  record_bucket_name: bemle-records-0
  models_bucket_name: bemle-models-0
ec2_instance_infos:
  image_id: ami-06878d265978313ca
  key_name: arslan_bemle
  security_group_ids: sg-00d915926d82ef341
  max_tries_to_create_an_instance: 20
bemle_premium_container_info:
  repo_name: iamvicky90
  name: beml_premium_docker_file
  tag: 0.1.204
```
#### CircleCI Environment Variables
| Variable Name | Description |
| :---: | :---: |
| AWS_ACCESS_KEY_ID | <i>AWS ACESS KEY Credential, can get from IAM </i> |
| AWS_SECRET_ACCESS_KEY | <i>AWS SECRET ACESS KEY Credential, can get from IAM </i> |
| MONGODB_CLUSTER_CONNECTION_STRING | <i>MongoDB connection String To acess mongodb for logs or user informations </i> |
| ML_API_HOSTNAME_WITH_PORT | <i>Add the ML API APP link, so that BeMLE can acess it when user wants to predict </i> |
| PRIVATE_KEY_LINK | <i>Add the private key to acess EC2 instance for premium user </i> 
| DOCKERHUB_USER | <i>Dockerhub username, to push the docker images to DockerHUB </i> |
| DOCKERHUB_PASSWORD | <i>Dockerhub Password, to push the docker images to DockerHUB </i> |
| DOCKER_IMAGE_NAME | <i>Name of the Docker Image </i> |
| EC2_HOSTNAME | <i>EC2 host name to dploy the applications or changes in ec2 instance via ssh connection </i> |
| EC2_USER_NAME | <i>EC2 user name to dploy the applications or changes in ec2 via ssh connection </i> |
| MAIL_PASSWORD | <i>Password of the mail to send automatic mails to the clients </i> |

## Installation
The Code is written in Python 3.8. If you don't have Python installed you can find it [here](https://www.python.org/downloads/). If you are using a lower version of Python you can upgrade using the pip package, ensuring you have the latest version of pip. To install the required packages and libraries, run this command in the project directory after [downloading it](https://github.com/IamVicky90/Be-MLE/archive/main.zip):
#### To run main Be-MLE Application
```bash
pip install -r requirements.txt
```
#### To run Be-MLE Admin
```bash
pip install -r requirements_for_bemle_admin.txt
```
#### To run Be-MLE Premium
```bash
pip install -r requirements_for_premium.txt
```
#### To run Be-MLE ML API For Prediction
```bash
pip install -r requirements_ml_api.txt
```
## Run
To run the app in a local machine, shoot this command in the project directory:

__Run the follwing command after installing their requirements file__

For BeMLE
```bash
python app.py
```
For Be-MLE Admin( To see logs and user Information)
```bash
python bemle_admin.py
```
For BeMLE ML API( For Prediction )
```bash
python ml_api_app.py
```
## Docker SetUp
To run the app n docker, you first need dockers installation by using the following steps:
```
For windows go to the link then download and install it : https://docs.docker.com/docker-for-windows/install/
For Ubuntu/Linux, run the command: apt install docker.io  
```
__Follow the following steps to run in dockers, Please add your credentials__
```bash
>> sudo docker run -it -d -p <Select your port>:5000 --name be-mle -e MONGODB_CLUSTER_CONNECTION_STRING= [MONGODB_CLUSTER_CONNECTION_STRING] -e PRIVATE_KEY_LINK=[PRIVATE_KEY_LINK] -e AWS_SECRET_ACCESS_KEY=[AWS_SECRET_ACCESS_KEY] -e AWS_ACCESS_KEY_ID=[AWS_ACCESS_KEY_ID] -e MAIL_PASSWORD=[MAIL_PASSWORD] -e ML_API_HOSTNAME_WITH_PORT=[ML_API_HOSTNAME_WITH_PORT] iamvicky90/be-mle:<tag>
>> sudo docker run -it -d -p <Select your port>:5001 --name ml_api_docker_file -e MONGODB_CLUSTER_CONNECTION_STRING=[MONGODB_CLUSTER_CONNECTION_STRING] -e ML_API_HOSTNAME_WITH_PORT=[ML_API_HOSTNAME_WITH_PORT] -e AWS_SECRET_ACCESS_KEY=[AWS_SECRET_ACCESS_KEY] -e AWS_ACCESS_KEY_ID=[AWS_ACCESS_KEY_ID] -e MAIL_PASSWORD=[MAIL_PASSWORD] iamvicky90/ml_api_docker_file:<tag>
>> sudo docker run -it -d -p <Select your port>:8050 --name be-mle-admin -e MONGODB_CLUSTER_CONNECTION_STRING=[MONGODB_CLUSTER_CONNECTION_STRING]  iamvicky90/bemle_admin:<tag>
```
## To Run main BeMLE with anaconda environments
#### STEP 01 - To execute the initial setup run the following command:
```bash 
bash ./init_setup.py
```
#### STEP 02 - Enable the conda environment -
```bash
conda activate ./env
```
#### STEP 03 - Run only main BeMLE App -
```bash
python app.py
```
## Local SetUp with Minikube
#### k8's(kubernates) setup with minikube
<i><b>(Not Recommended you may face issues, better to use [kubernatives cloud setup](#kubernatives-cloud-setup))</b></i>
###### Follow the following commands for project setup with k8's cluster.
- To start the minikube with docker
    ```bash
    minikube start --driver=docker
    ```
- To point your shell to minikube's docker-daemon
    ```bash
    eval $(minikube -p minikube docker-env)
    ```
- Apply the secrets for the cluster.
    ```bash
    kubectl apply -f kubernates/microservices/mongo-secret.yaml
    ```
- To confirm/see the secrets.
    ```bash
    kubectl get secrets
    ```
- Apply the configmap for the cluster.
    ```bash
    kubectl apply -f kubernates/microservices/mongo-configmap.yaml
    ```
- To confirm/see the configmaps.
    ```bash
    kubectl get configmap
    ```
- Apply the Deployment snd Service for mongo.yaml
    ```bash
    kubectl apply -f kubernates/microservices/mongo.yaml
    ```
- Apply the Deployment snd Service for mongo-express
    ```bash
    kubectl apply -f kubernates/microservices/mongo-express.yaml
    ```
- Apply the Deployment snd Service for app (Be-MLE Project)
    ```bash
    kubectl apply -f kubernates/microservices/app.yaml
    ```
- To see all the pods state
    ```bash
    kubectl get po
    ```
- To see all the pods state with some more information
    ```bash
    kubectl get po -o wide
    ```
- To see the logs of the pods
    ```bash
    kubectl describe pod
    ```
- To see all the pods state with their replicas
    ```bash
    kubectl get all
    ```
- To get/see all the services
    ```bash
    kubectl get svc
    ```
- To get the external IP for mongo-express
    ```bash
    minikube service mongo-express-service
    ```
- To get the external IP for bemle-service
    ```bash
    minikube service bemle-service 
    ```
## Kubernatives Cloud Setup
(Recommended)
For cloud setup you must have [awscli2](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html), [kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html) and [eksctl](https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html)
- Create eksctl cluster from the following command
```bash
eksctl create cluster --name [any name] --region [enter region]  --version 1.22 --nodegroup-name [specify your name] --node-type [specify node name] --nodes [enter number of nodes]
```
Apply Following commands
- Run Microservices but must change the environment variables from secrets and configmaps
```bash
kubectl apply -f kubernates/microservices/
```
- To Run efs for volume persistance

Note: must change the server link of efs in efs/deployment.yaml file
```
kubectl apply -f kubernates/efs/
```
- Run mongodb cluster
```bash
kubectl apply -f kubernates/mongodb_k8s_configrations
```
- To expose the mongo link to third party app outside the kubernatives cluster
```bash
kubectl expose pod mongo-deployment-0  --port 11392 --target-port 27017 --type LoadBalancer
kubectl expose pod mongo-deployment-1  --port 11392 --target-port 27017 --type LoadBalancer
kubectl expose pod mongo-deployment-2  --port 11392 --target-port 27017 --type LoadBalancer
```
- Apply ArgoCD 

To apply ArgoCD you first need to install it by following commands
```bash
# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo

```
- Change source and destination in kubernates/argocd-application.yaml file and apply it by following command
```bash
kubectl apply -f kubernates/argocd-application.yaml
```
- Apply BeMLE ML API microservice

Note: You must change ML_API_HOSTNAME_WITH_PORT in kubernates/bemle_ml_api_configmap.yaml file and apply it by following command
```bash
kubectl apply -f kubernates/bemle_ml_api_configmap.yaml
```
## License
```
MIT License

Copyright (c) 2022 Waqas Bilal

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
