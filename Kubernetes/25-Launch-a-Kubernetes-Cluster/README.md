<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launch a Kubernetes Cluster

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-eks1)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Launch a Kubernetes Cluster

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks1_e5f6g7h8)

---

## Introducing Today's Project!

In this project, I will launch and connect to an EC2 instance, create a Kubernetes cluster, monitor the cluster with CloudFormation, access the cluster using an IAM access entry and test the resilience of my cluster because it is part one of my Kubernetes project in my cloud engineering journey.

### What is Amazon EKS?

### One thing I didn't expect

### This project took me...

---

## What is Kubernetes?

Kubernetes is a container orchestration platform which is to say they coordinate containers so that they run smoothly across all servers. Companies and developers use Kubernetes to maintain large container based applications and to scale them with high traffic.

I used eksctl to create a kubernetes cluster. The create cluster command I ran defined the cluster name, node group, node type, number of nodes, version and region.

I initially ran into two errors while using eksctl. The first one was because I tried to create the cluster without downloading the eksctl tool. The second one was because my EC2 instance lacked IAM access to create a cluster.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks1_ff9bfc221)

---

## eksctl and CloudFormation

CloudFormation helped create my EKS cluster because eksctl uses it under the hood to automate infrastructure as code. It created VPC resources because I needed a fresh, isolated network instead of making manual modifications to my default VPC settings.

There was also a second CloudFormation stack for node groups which is a group of EC2 instances that will run my containers. The difference between a cluster and node group is that the cluster is the entire environment managed by the kubernetes while a node group is a group of nodes organised together within the cluster...

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks1_w3e4r5t6)

---

## The EKS console

I had to create an IAM access entry in order to to view nodes in my EKS console. An access entry is an IAM feature that maps my IAM credentials to Kubernetes RBAC(Role Based Access) .I set it up by attaching AmazonEKSClusterAdminPolicy to my IAM principle ARN.

It took 15 minutes to create my cluster. Since I'll create this cluster again in the next project of this series, maybe this process could be sped up if I ran the create cluster command first, then worked on other setup tasks.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks1_e5f6g7h8)

---

## EXTRA: Deleting nodes

Did you know you can find your EKS cluster's nodes in Amazon EC2? This is because node in Kubernetes clusters in AWS are actually EC2 instances. Kubernetes use the generic term node because different platforms have different cloud resources to be the nodes.

Desired size means the number of nodes I want in my node group... Minimum and maximum sizes are helpful for for adjusting to the demand of the application. These settings can be edited to get a bigger or smaller node group.

When I deleted my EC2 instances the are terminated then shortly replaced. This is because Kubernetes replaces the terminated role to keep the service running in the desired state.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-eks1_q7r8s9t0)

---

---
