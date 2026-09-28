<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up Kubernetes Deployment

**Project Link:** [View Project](https://nextwork.ai/projects/ca1e2f05-dd07-5e77-b83c-1e6a6516944c)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks2_45e6c3de5)

## Introducing Today's Project!

In this project, I will clone a backend application from Github, build a docker image of the backend, push my image to Amazon ECR repository, Trobleshhot installationand configuration errors and dive into the backend code on Github because it is part of enhancing my Kubernetic skills in my cloud engineering journey .

### Tools and concepts

I used Amazon EKS, Git & Github, Docker and Amazon ECR to set up the Kubernetes deployment. Key steps include  setting up the environment, pulling the backend code, building container image and pushing the image into ECR.

### Project reflection

This project took about 2 hours. The most challenging part was understanding the commands to create EKS clusters. My favorite part was tracing the app's code as it moved from GitHub to the EC2 instance and into a Docker image!

Something new that I learnt from this experience was how crutial Kubernetes is to maintaining applications especially during downtimes as it provides backups and is always up to date.

## What I'm deploying

To set up today's project, I launched a Kubernetes cluster. Steps I took to do this included creating an EC2 instance and setting up instance connect to allow faster and secure connection. I then installed eksctl tool to easily provision the Amazon EKS cluster, bypassing the complex manual steps required if I were to use the AWS CLI. The tool allowed me to create my Kubernetes cluster.

### I'm deploying an app's backend

Next, I retrieved the backend that I plan to deploy. An app's backend means the part of the app where requests are processed and data is stored/retreived.I retrieved backend code by installing Git in my EC2 console and cloning the App's Github repository which contained the backend code.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks2_1ebb86c71)

## Building a container image

Once I cloned the backend code, my next step is to build a container image of the backend. This is because i need the app to run consistently across every device. I achieved this using Docker.

When I tried to build a Docker image of the backend, I ran into a permissions error because my EC2 instance uses the default AMI, which logs me in as ec2-user. Since ec2-user lacks root-level access by default, it cannot communicate with the Docker without prefixing commands with sudo.

To solve the permissions error, I added my ec2-user to Docker group using "sudo usermod -a -G docker ec2-user" command . The Docker group is a group in Linux systems that gives the user permissions to run Docker commands.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks2_45e6c3de5)

## Container Registry

I'm using Amazon ECR in this project to store the backend image for the app. ECR is a good choice for the job because it is an AWS service and will require minimal authentication setup for the project.

Container registries like Amazon ECR are great for Kubernetes deployment because it provides Kubernetes easy access to up to date, on demand and identical images.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks2_l2m3n4o5)

## EXTRA: Backend Explained

After reviewing the app's backend code, I've learnt that the main files required are requirements.txt for dependencies, Dockerfile which contains instructions for building the app's Docker image and an API files for routing.

### Unpacking three key backend files

The requirements.txt file lists all the Python dependencies (like Flask) used in our app. This allows package managers to easily install all required libraries on our EC2 instance at once.

The Dockerfile gives Docker instructions on how the docker image of the backend should be built. Key commands in this Dockerfile include "FROM python:3.9-alpine" which sets up the environment of the app and "CMD ["python3", "app.py"]" which saya the container should run mmand "python3 app.py" to start thr Flask app.

The app.py file defines the Flask API, handling all key routing, request, and response instructions for our backend application.

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/ca1e2f05-dd07-5e77-b83c-1e6a6516944c)*
