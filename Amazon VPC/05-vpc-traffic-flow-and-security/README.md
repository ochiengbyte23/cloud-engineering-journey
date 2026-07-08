<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-security)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## VPC Traffic Flow and Security

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is is service for hosting resources across the cloud and it is useful because because it gives us control over who and what type of data can leave or enter the VPC.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to set traffic rules for filtering inbound and outbound data based on IP address, protocols and ports.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the ability to view all the VPC created across different regions in one place. It is a really efficient way to manage resources.

### This project took me...

This project took me 1.5 hours to complete including the extended mission.

---

## Route tables

Route tables are traffic guides for the resources in my instances. The help to control which traffic should be public through the gateway and which traffic is sent within the locally AWS resources. Route tables are evaluated from the most restrictive to the least restrictive.

Routes tables are needed to make a subnet public because they are able to direct traffic from the public subnet to the internet gateway which connects to the internet.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Routes are defined by their destination and target, which mean the destination describes the IP address range that the traffic wants to reach while the target is the path taken to reach that destination.

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0./0. and a target of igw-097b149d99500c192.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups are checkpoints for AWS resources in order to control the inbound and outbound traffic. The traffic is filtered based on IP addresses, protocols and ports.

### Inbound vs Outbound rules

Inbound rules are traffic rules that control which data can enter my resource in the security group. I  configured an inbound rule that that allows traffic from any IP address since it is supposed to be publicly accessible. This is typical for public subnets since it ensures anyone can access it.

Outbound rules are traffic rules that control which data my resource can send out. By default, my security group's outbound rule allows all outbound traffic unless specified otherwise.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are traffic checkpoints for data packets in and out of subnets.

### Security groups vs. network ACLs

The difference between a security group and a network ACL is that a security group operates within the scope of an AWS resource while a network ACL  operates within the scope of a subnet.

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will be set to rule number 100 which means all the traffic is allowed in to and out of the subnet unless specified otherwise.

In contrast, a custom ACL’s inbound and outbound rules are automatically set to rule number 100 which should allows all traffic but the traffic is denied by default unless set otherwise.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

I created additional VPC with a gateway and security group .Instead of my usual region, I used us-east-1(N.Virginia).Teams would use multiple regions to improve latency for all users and also as a security risk incase one region experiences an outage

EC2 Global View is a tool where you can find all my VPC and EC2 instances. I could even narrow down my search by specific regions, VPCs and more. Without EC2 Global View, you'd have to manually switch between regions to track my resources

Now that I've learnt about EC2 Global View, I'd use it again to view multiple resources across different region since it is a simpler and faster method compared to manually changing

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-security_b03ea6162)

---

---
