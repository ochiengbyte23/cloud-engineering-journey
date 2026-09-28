<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create Kubernetes Manifests

**Project Link:** [View Project](https://nextwork.ai/projects/ccc2aecf-ba9e-5ebe-98ec-e0c4aec9c4ea)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks3_b01876555)

## Introducing Today's Project!

In this project, I will set up deployment manifest and service manifest because they control how backend is deployed and its exposure to the users respectively .

### Tools and concepts

I used Amazon EKS, eksctl, and EC2 to configure our cluster. Key concepts include using Deployment and Service manifests to declaratively define how Kubernetes pulls our ECR images, runs our backend pods, and exposes them to traffic.

### Project reflection

I chose to do this project today because I'm building my cloud architecture portfolio. 

This project took me approximately 2 hours. The most challenging part was configuring the correct image URI in the Deployment manifest. My favourite part was successfully pushing my custom Docker image to Amazon ECR!

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. Steps I took to do this included:
1. Launching an EC2 instance and  connecting it for virtual access,
2. Adding IAM roles to authenticate the EC2
3. Installing eksctl tool to set up EKS clucter with minimal commands and settings
4.  Finally setting up my EKS cluster.

### Backend code

I retrieved the backend that I plan to deploy by first installing git in my EC2 connect then cloning the backend repository from Github. Backend is the part of the application processing requests, storing and retreiving data.

### Container image

Once I cloned the backend code, I built a container image because its copies will be used by Kubernetes to create identical containers for deployment. I used Docker to build the image containers following instructions from the Dockerfile in the backend code.

I also pushed the container image to a container registry, because it keeps deployment simple and makes sure every Kubernetes instance is up to date. To push the image to ECR, I first created n ECR repository then authenticated Docker and used push commands from AWS console to upload the image.

## Manifest files

Kubernetes manifests are  set of instructions that tell Kubernetes how to run the app. Manifests are helpful because they help Kubernetes to know what the app needs like which continer to run, number of copies it needs to create and memory allocation.

A Kubernetes deployment manages containerized applications. The container image URL in my Deployment manifest tells Kubernetes which container images to use, how many copies to create and how to allocates memory.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks3_b01876554)

## Service Manifest

A Kubernetes Service exposes the containerized application to the outside world or  other parts of the system. You need a Service manifest to to create and update the traffic controller which ensures traffic flows to the right pod.

My Service manifest sets up an external traffic port 8080 on any pod labaled "app: nextwork-flask-backend" using TCP.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks3_b01876555)

## Deployment Manifest


Annotating the Deployment manifest helped me understand how Kubernetes maps configurations because it breaks down how replica counts, ECR image paths, and target ports work together to run and scale our application pods.


A notable line in the Deployment manifest is the number of replicas, which means the number of copies of the app that Kubernetes shiuld run. Pods are relevant to this because it is the smalles Kubernetes unit that can be deployed.

One part of the Deployment manifest I still want to know more about is replicas because I want to understand how Kubernetes detects pod failures and automatically deploys new instances to ensure self-healing.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks3_6aae73e71)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/ccc2aecf-ba9e-5ebe-98ec-e0c4aec9c4ea)*
