<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy Backend with Kubernetes

**Project Link:** [View Project](https://nextwork.ai/projects/090a4709-f1f4-5d95-ae4d-b8199bf808ed)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/090a4709-f1f4-5d95-ae4d-b8199bf808ed_6cfb382f2)

## Introducing Today's Project!

In this project, I will set up the backend for app deployment, install kubectl because they enable me to deploy the backend on a Kubernetes cluster.

### Tools and concepts

I used Kubernetes, Amazon ECR, and kubectl to securely deploy and manage our containerized backend. Key concepts include using manifests to configure Deployments (for running and scaling pods) and Services (for stable networking).

### Project reflection

This project took me approximately 2 hours. The most challenging part was configuring IAM policies to view resources in the EKS console. My favourite part was being able to view events inside each pod .

I chose to do this project today because it is part of my cloud engineering journey to build my Kubernetes skills. 

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. The cluster's role in this deployment is to manage when to start, stop or scale the containers and keeps them connected to the internet.

### Backend code

I retrieved backend code by installing Git the cloning the repository from Github. Pulling code is essential to this deployment because the code is essential for this Kubernets project to work sice it is what will be containerised.

### Container image

Once I cloned the backend code, I built a container image because it is consistent across multiple devices. Without an image, it would be difficult for Kubernetes to deploy and scale identical continers.

I also pushed the container image to a container registry, which is a secure storage for storing, sharing and deploying images. ECR facilitates scaling for my deployment because it can be tagged to pull from the latest image on demand.

## Manifest files

Kubernetes manifests are a set of instructions that tell Kubernetes how to run my app. Manifests are helpful because they help Kubernetes to know what the app needs like which containers to use, how many copies to create and how much memory to allocate.

A Deployment manifest manages several copies of my app across multiple continers in my cluter. The container image URL in my Deployment manifest tells Kubernetes where to pull the container image from during deployment.

A Service resource exposes the backend code to the outside world of the cluster. My Service manifest sets up the service name, type of service, receiving and target port.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/090a4709-f1f4-5d95-ae4d-b8199bf808ed_b01876554)

## Backend Deployment!

To deploy my backend application, I applied my Deplyment and Service manifests to my backend application using kubectl tool.

### kubectl

kubectl is a tool for deploying and managing resources within a Kubernetes cluster. I need this tool to interact with my Deployment and Service resources. I can't use eksctl for the job because it is only useful for setting up and deleting EKS clusters, and configuring their settings.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/090a4709-f1f4-5d95-ae4d-b8199bf808ed_6cfb382f2)

## Verifying Deployment

My extension for this project was using the AWS EKS console to verify the live deployment. I had to set up IAM access policies because I  I lacked administrative permissions to view Kubernetes cluster resources directly. I set up access by updating my IAM access policies and configuring EKS Access Entries to grant myself cluster admin access

Once I gained access into my cluster's nodes, I discovered pods running inside each node. Pods are the smallest deployable Kubernetes units. Containers in a pod share the same network space and storage so they can communicate and share effectively.

The EKS console shows you the events for each pod, where I could see the pod successfully got the image from ECR, created and started a container based on the image and gave my pod an internal IP address in the cluster. This validated that my backend was successfully deployed.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/090a4709-f1f4-5d95-ae4d-b8199bf808ed_3b391f873)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/090a4709-f1f4-5d95-ae4d-b8199bf808ed)*
