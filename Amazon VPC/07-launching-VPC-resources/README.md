<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launching VPC Resources

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-ec2)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Launching VPC Resources

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-ec2_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is an architectural layout of the VPC and it is useful because it shows the  number of subnets, which subnets are associated with which route table, and which route tables have routes to an internet gateway.

### How I used Amazon VPC in this project

I used Amazon VPC to to launch EC2 instances and modified their access to my liking i.e private or public.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how easier it was to create a VPC using a resource map. It made the whole process easier to comprehend visually.

### This project took me...

This project took me about 2 hours. Most of my time was spent recreating the the two public and private subnets .

---

## Setting Up Direct VM Access

Directly accessing a virtual machine means logging in and managing the machine's software as if it were right in front of you.

### SSH is a key method for directly accessing a VM

SSH traffic means communication between a user and the VPC insurance is assured using SSH protocol. SSH can only be established if the user has a private key corresponding to the instance's public key.

### To enable direct access, I set up key pairs

Key pairs are authentication details to help user login into a specific AWS resource. There two key pairs i.e private and public key pairs

A private key's file format means it is able to be processed by a specific application or system. My private key's file format was .pem(Private Enhanced Mail) which is the most common key file format. Choosing the right format is crucial since not all formats will be supported by your specific application or system.

---

## Launching a public server

Start your response with 'I had to change my EC2 instance's networking settings by switching from the default VPC and and specifying which subnet i wanted to place my EC2 instance in. I also had to choose my already created security group.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

My private server has its own dedicated security group because it does need to communicate with any other resource unless set otherwise. A dedicated security group helps to manage who and what can interact with EC2 the instance.

My private server's security group's source is my public security group which means it is the only resource which can communicate with my EC2 private instance.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

I used an alternative way to set up an Amazon VPC! This time, I use a resource map to view the layout of my VPC architecture dynamically as i modified it. It was easier to understand very fast compared to manually switching to console tabs.

A VPC resource map is an architectural layout of the subnets, route table , internet gateways and how they are connected to each other.

My new VPC has a CIDR block of 10.0.0.0/16 It is possible for my new VPC to have the same IPv4 CIDR block as my existing VPC because they are not in the same network and would therefore not interact with one another.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

When determining the number of public subnets in my VPC, I only had two options:0 or 2.This was because it needed to enforce redundancy incase one of the subnet went down. More subnets can be added manually after the VPC is created.

The set up page also offered to create NAT gateways, which are a way for private subnets to access the internet usually for updates while blocking inbound traffic.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-ec2_8ee57662)

---

---
