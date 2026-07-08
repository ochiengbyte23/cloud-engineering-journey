<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Creating a Private Subnet

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-private)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Creating a Private Subnet

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-private_afe1fdbd)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a service for creating subnets to store resources. It is useful because it can be modified to make the resources public or private to our liking.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to to create a private subnet and its associated route table and Access Control List. This made the resources in my private subnet inaccessible publicly.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project is the lack of security group. 

### This project took me...

This project took me 1.5 hours to complete. Most of the time was taken recreating the a new VPC which i have been doing more quickly with each project.

---

## Private vs Public Subnets

The difference between public and private subnets is that a public subnet can be accessed outside the VPC while a private subnet cannot be accessed outside the VPC.

Having private subnets are useful because not all resources in our VPC are meant to be shared publicly since some may contain sensitive information.

My private and public subnets cannot have the same CIDR IP address since it would result in a redundancy of the same zone having similar address. This is required in order to route traffic correctly.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-private_afe1fdbd)

---

## A dedicated route table

By default, my private subnet is associated with is associated with the default default route table unless set otherwise.

I had to set up a new route table because the default route table is associated with a public gateway that allows public access to the resources which is not private.

My private subnet's dedicated route table only has one inbound and one outbound rule that allows traffic locally within the VPC.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-private_b4b904b5)

---

## A new network ACL

By default, my private subnet is associated with the default Access Control List which allows all traffic

I set up a dedicated network ACL for my private subnet because it does not allow any traffic by default unless set otherwise. This helps to keep it private.

My new network ACL has two simple rules -the Inbound and the Outbound rule which both deny any traffic by default unless set otherwise.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-private_1ed2cb07)

---

---
