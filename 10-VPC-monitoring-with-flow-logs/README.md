<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Monitoring with Flow Logs

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-monitoring)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## VPC Monitoring with Flow Logs

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_3e1e79a1)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a logically isolated section of AWS which provides a virtual network to store and manage resources and it is useful because it gives full control over how the resources are organised, traffic flow and security is monitored.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to to create to VPC each with a public subnet. I then established a peering connection. I also set up a Flow Logs with IAM policies and roles which allowed its connection to my VPC. I used the Flow Logs to analyze a ping test.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the log insights to already have inbuilt inquiries. This made running the inquiry easier.

### This project took me...

This project took me 2 hours to complete.

---

## In the first part of my project...

### Step 1 - Set up VPCs

In this step, I will create two VPCs because it is the first step to monitoring traffic in a network.

### Step 2 - Launch EC2 instances

In this step, I will set up two instances each in a different VPC because i need the two instances to send data to each other in order to monitor network activity.

### Step 3 - Set up Logs

In this step, I will set up VPC Flow Log because it provides a way to track inbound and outbound traffic. It also stores these records.

### Step 4 - Set IAM permissions for Logs

In this step, I will set up IAM roles for my Flow Log because it gives the Flow Log the permission to write and send logs to CloudWatch.

---

## Multi-VPC Architecture

I started my project by launching two VPCs each with a public subnet and not private subnet.

The CIDR blocks for VPCs 1 and 2 are 10.1.0.0/16 and 10.2.0.0/16 respectively. They have to be unique because having overlapping CIDR blocks will cause network issues when the two VPC need to communicate with each other.

### I also launched EC2 instances in each subnet

My EC2 instances' security groups allow all incoming ICMP traffic from all IP addresses. This is because i will use the ICMP ping command to check for the connection between the two instances.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_e7fa8775)

---

## Logs

Logs are a diary of the actions happening in a computer. It is used to troubleshoot and understand the source of problems.

Log groups are related logs usually from the same source or application stored together. They are region specific but logs form different regions can still be brought together using CloudWatch.

### I also set up a flow log for VPC 1

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_e8398869)

---

## IAM Policy and Roles

I created an IAM policy because Flow Logs are not allowed to record and store logs to Cloudwatch by default. You have to create an IAM policy to give the Flow Logs that permission. 

I also created an IAM role because IAM policies have to be associated with IAM role in order to function. I created an IAM policy to allow writing and saving of traffic logs. The IAM role specifies which service is allowed to use the IAM policies which in this case is the VPC Flow Log.

A custom trust policy is used to narrowly specify who can and cannot use an IAM role

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_4334d777)

---

## In the second part of my project...

### Step 5 - Ping testing and troubleshooting

In this step, I will get instance 1 to send a test message to instance 2 because i need to generate traffic which i will it's log using VPC Flow Logs.

### Step 6 - Set up a peering connection

In this step, I will set up a private connection link between VPC 1 and 2 through route tables  because the private connection is required to enable VPC peering.

### Step 7 - Analyze flow logs

In this step, I will analyze Flow Logs because they contain recorded traffic data of VPC1 public subnet.

---

## Connectivity troubleshooting

My first ping test between my EC2 instances had no replies, which means my test message was blocked by  VPC 2.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_99d4ba42)

I could receive ping replies if I ran the ping test using the other instance's public IP address, which means both instances are correctly configured to receive ICMP traffic from the public internet.

---

## Connectivity troubleshooting

Looking at VPC 1's route table, I identified that the ping test with Instance 2's private address failed because there is no route table to privately connect the two VPCs. This makes VPC peering impossible.

### To solve this, I set up a peering connection between my VPCs

I also updated both VPCs' route tables so that they can accept VPC peering traffic between them.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_7316a13d)

---

## Connectivity troubleshooting

I received ping replies from Instance 2's private IP address! This means my VPC peering connection is not being blocked by either VPC since my route table have been updated with the peering connection.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_4ec7821f)

---

## Analyzing flow logs

Flow logs tell us about the source and destination of traffic, data amount, time of data arrival and departure , whether traffic was accepted or rejected.

For example, the flow log I've captured tells us that traffic went from 13.244.141.81  to 10.1.5.225. We also accepted that the traffic was accepted by the security group and network ACL of my VCP.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_d116818e)

---

## Logs Insights

Logs Insights is an analysis feature of Flow Logs used for analysis of data traffic. It filters, process and combine's data through the use of queries to troubleshoot and get a better understanding of the network.

I ran the query to return the top 10 byte transfers by the source and destination IP address. This query analyzes my data traffic to return the top 10 biggest data transfers between the IP addresses.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-monitoring_3e1e79a1)

---

---
