<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Aurora Database with EC2

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-databases-aurora)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Connect a Web App to Amazon Aurora

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-aurora_44443546)

---

## Introducing Today's Project!

### What is Amazon Aurora?

Amazon Aurora is a type of relational database and it is useful because of clusters which allow for large scale application.

### How I used Amazon Aurora in this project

In today's project, I used Amazon Aurora to create a database instance from scratch in AWS, configured it with appropriate settings and connected it to an EC2 instance.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how costly running a database can be.

### This project took me...

This project took me one hour including the documentation.

---

## In the first part of my project...

### Creating an Aurora Cluster

A relational database is a database that organises data into tables of rows and columns which relate to each other. A relational database can be queried using SQL.

Aurora is a good choice when we need something large scale with peak performance and uptime.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-aurora_44443546)

---

## Halfway through I stopped!

I stopped creating my Aurora database because I needed to create an EC2 instance first  to host the web app i would connect with my Aurora database.

### Features of my EC2 instance

I created a new key pair for my EC2 instance because I want to securely connect my EC2 instance with my Arora database.

When I created my EC2 instance, I took particular note of the Public IPv4 DNS address and name as well as the key pair name so that i know what i can access with the key pair.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-aurora_91b9fd1g)

---

## Then I could finish setting up my database

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-aurora_1fddb0b5)

Aurora Database uses clusters because they are group of database copies that work together to ensure data is always available. The clusters consists of primary "write" instances which can be edited and multiple "read" replicas as database backups.

---

---
