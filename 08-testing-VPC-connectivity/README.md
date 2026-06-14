<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Testing VPC Connectivity

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-connectivity)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Testing VPC Connectivity

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-connectivity_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a logically isolated section of AWS where you can virtually store AWS resources and it is useful because enables us to modify the VPC to our requirements

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to test the VPC connectivity both internally with its resources and externally with the internet.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how the curl command returned a full HTML message.

### This project took me...

This project took me took me about 1.5 hours. Most of the time was spent setting up the VPC per my previous project.

---

## Connecting to an EC2 Instance

Connectivity means how well different parts of the network talk to each other and with external networks.

My first connectivity test was whether I could connect to two EC2 instances in each a public and private subnet.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-connectivity_88727bef)

---

## EC2 Instance Connect

I connected to my EC2 instance using EC2 Instance Connect, which is a short way of getting direct access to SSH using the EC2 console.

My first attempt at getting direct access to my public server resulted in an error, because my security group was to only accept HTTP inbound traffic, The EC2 connect however was using SSH traffic.

I fixed this error by editing my security group to also allow SSH traffic as inbound.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-connectivity_1cbb1b88)

---

## Connectivity Between Servers

Ping is a message sent to another computer or device to check whether they can communicate with each other. I used ping to test the connectivity between the EC2 instance in the private subnet and EC2 instance in the public subnet.

The ping command I ran was ping 10.0.1.126. 10.0.1.126 is private subnet IP address.

The first ping returned an error. This meant on of the checkpoints in the private subnet i.e ACL or Security Group was preventing the message sent from reaching the EC2 instance.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-connectivity_defghijk)

---

## Troubleshooting Connectivity

I troubleshooted this by making sure the inbound and outbound rules for both the ACL and the Security Group allowed ICMP IPv4 ping message.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-connectivity_4a9e8014)

---

## Connectivity to the Internet

Curl is a connectivity command that transfers data to or from a server.

I used curl to test the connectivity between my public subnet and an internet URL.

### Ping vs Curl

Ping and curl are different because ping only checks if two devices can communicate whereas curl can transfer data to and from a server.

---

## Connectivity to the Internet

I ran the curl command curl https://learn.nextwork.org/projects/aws-host-a-website-on-s3 which returned a HTML message for the website.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-connectivity_8ee57662)

---

---
