<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Peering

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-peering)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## VPC Peering

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-peering_88727bef)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a logically isolated section of AWS where resources are virtually stored and it is useful because it allows for traffic control and security.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to to test VPC peering between two EC2 instances using EC2 Instance Connection. I also updated security group rules to run a successful connectivity test to validate the peering setup.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was a public IPv4 address being a requirement for the instances to communicate.

### This project took me...

This project took me about 2 hours to complete.

---

## In the first part of my project...

### Step 1 - Set up my VPC

In this step, I will create two VPC using a resource map because it is the fast step to VPC peering.

### Step 2 - Create a Peering Connection

In this step, I will set up a peering connection between my two VPCs because it is a component designed for VPC to communicate with each other.

### Step 3 - Update Route Tables

In this step, I will update route tables because it enables the traffic coming from VPC 1 to get to VCP 2 and vice versa.

### Step 4 - Launch EC2 Instances

In this step, I will launch EC2 instances for each  because they will be used to test the peering connection between VPC resources..

---

## Multi-VPC Architecture

I started my project by launching two VPC,S each with two subnets i.e a public and private subnet.

The CIDR blocks for VPCs 1 and 2 are 10.1.0.0/16 and 10.2.0.0/16 respectively. They have to be unique because once a VPC peering connection is set route tables need unique dresses for correct routing across VPCs.

### I also launched 2 EC2 instances

I didn't set up key pairs for these EC2 instances as AWS manages a default key pair with EC2 instance Connect. 

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-peering_11111111)

---

## VPC Peering

A VPC peering connection is a component used for direct connection between VPC private addresses. Without it the VPC would have to use the internet to communicate.

VPCs would use peering connections to prevent using the internet for VPC connection which is not as direct and secure compared to VPC peering.

The difference between a Requester and an Accepter in a peering connection is that a Requestor is the VCP that initiates peering connection while an Acceptor is the VCP that receives the invitation.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-peering_1cbb1b88)

---

## Updating route tables

After accepting a peering connection, my VPCs' route tables need to be updated because without a new route to the respective VPC traffic wont be accepted.

My VPCs' new routes have a destination of each other's private IP addresses. The routes' target was the peering connection between the two VPC.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-peering_4a9e8014)

---

## In the second part of my project...

### Step 5 - Use EC2 Instance Connect

In this step, I will EC2 instance Connect to connect my  FIRST EC2 instance because we need to use our EC2 instance for connectivity test later in the project.

### Step 6 - Connect to EC2 Instance 1

In this step, I will use EC2 Instance Connect to connect to instance 1 because the IP requirement has been provided.

### Step 7 - Test VPC Peering

In this step, I will get instance 1 to send a confirmation message to instance 2 because it test if the peering connection works as intended.

---

## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect to directly connect with Instance-Nextwork VPC 1 just by using the Management Console.

I was stopped from using EC2 Instance Connect as our instance did not have a public IPv4 address. In order for EC2 instance connect to work it must have a public IPv4 address and be in a public subnet.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-peering_7685490c)

---

## Elastic IP addresses

To resolve this error, I set up Elastic IP addresses. Elastic IP addresses are public static IPv4 addresses that can be requested for our AWS account and delegate to specific resources in our subnet.

Associating an Elastic IP address resolved the error because it gives our EC2 instance a public IP addresses fulfilling all the requirements for instance connect to function.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-peering_45663498)

---

## Troubleshooting ping issues

To test VPC peering, I ran the command ping 10.2.9.21

A successful ping test would validate my VPC peering connection because ping test would not get replies from the other instance if the peering connections did not successfully connect the two VPCs.

I had to update my second EC2 instance's security group because it blocked any ICMP traffic form my ping message. I added a new rule that allowed ICMP traffic coming from my VPC 1.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-peering_7a29d352)

---

---
