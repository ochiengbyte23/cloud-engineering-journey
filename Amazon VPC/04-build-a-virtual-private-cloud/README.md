<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-vpc)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

In this project, I will demonstrate how to create a virtual private cloud with a public subnet and internet gateway. I'm doing this project to learn about VPC set up and operation and how to make them publicly accessible to the internet.

### What is Amazon VPC?

Amazon VPC is is service used for running amazon resources like the EC2 instance. and it is useful because it allows to choose whether to make our resources private or public and helps to organise the resources per the desired access and restrictions.

In today's project, I used Amazon VPC to launch a VPC in which i created a subnet for resource organisation and communication with other networks. I also created and attached a gateway to the subnet to make it available in the internet.

### Personal reflection

This project took me 1.5 hours to complete. The command alternative took less time of 15 minutes to complete.

One thing I didn't expect in this project was how easier the command line alternative of launching a VPC would be compared to using the management console.

---

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I will access the VPC console in AWS and create a VPC because because it is part of Nextwork cloud beginner challenge.

### How VPCs work

VPCs are a services to store AWS resources in organised manner and even choose to make them public or private. You also use VPC to choose how the resources communicate with each other without the public internet.

### Why there is a default VPC in AWS accounts

There was already a default VPC in my account ever since my AWS account was created. This is because a VPC is required to launch AWS services like EC2 instance. Only a few services like AWS S3 and AWS Lambda can function without the VPC.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-vpc_2facf927)

### Defining IPv4 CIDR blocks

To set up my VPC, I had to define an IPv4 CIDR block, which is which is a unique address assigned to a AWS VPC. The VPC uses this address to communicate with other networks. 

---

## Subnets

### What I did in this step

In this step, I will launch a subnet inside my VPC because it creates subdivisions the VPC which are used to organise where each resource will live and operate.

### Creating and configuring subnets

Subnets are subdivisions in a VPC that are used to group resources with similar access rules and restrictions together. There are already subnets existing in my account, one for every Availability Zone(AZ) in my region. Each subnet is placed in a different availability zone in the region to create a backup if one fails.

### Public vs private subnets

The difference between public and private subnets are their accessibility to external networks. For a subnet to be considered public, it has to be connected to an internet gateway.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-vpc_157c4219)

### Auto-assigning public IPv4 addresses

Once I created my subnet, I enabled auto-assign public IPv4 address. This setting makes sure the public subnet has an public IPv4 address so that it can communicate with other networks outside of its own VPC. 

---

## Internet gateways

### What I did in this step

In this step, I will attach my VPC to an internet gateway because only then will my VPC be able to communicate with the internet.

### Setting up internet gateways

Internet gateways are the key to making applications available to the internet. By attaching an internet gateway my instances will be able to be accessed by users in the internet

Attaching an internet gateway to a VPC means my AWS resources can access the internet. If I missed this step i would not be able to access my resources like EC2 instance in the internet.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

### What I'm doing in this extension

In this project extension, I will launch a VPC with AWS CloudShell .I will use the  AWS CloudShell to run AWS CLI to set up the VPC, subnet and internet gateway because it is an easier and faster  alternative to manually setting up the VPC.

### Exploring CloudShell and CLI

### Debugging my setup

To set up a VPC or a subnet, you can use the command "aws ec2 create-subnet --vpc-id [VPC ID] --cidr-block [CIDR adress]". Make sure to avoid errors by including the right CIDR block address.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-vpc_9b2465411)

### Comparing CloudShell vs AWS Console

Compared to using the AWS Console, an advantage of using commands is the speed and precision. An advantage of using the Console is the ease. Overall, I preferred using the command over the console because of how quickly i was able to launch the VPC.

---

---
