<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect a Web App with Aurora

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-databases-webapp)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Connect a Web App to Amazon Aurora

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-webapp_1709b26b)

---

## Introducing Today's Project!

### What is Amazon Aurora?

Amazon Aurora is a relational database and it is useful because it can hold large scale databases efficiently.

### How I used Amazon Aurora in this project

In today's project, I used Amazon Aurora to connect with a web app where i could add data through the web app.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how tangible databases are in being able to see added data.

### This project took me...

2 hours including the documentation.

---

## Creating a Web App

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-webapp_b7999168)

To connect to my EC2 instance, I used my terminal to connect using ssh(ssh -i NextWorkAuroraApp.pem ec2-user@ec2-16-28-59-92.af-south1.compute.amazonaws.com) and made sure i had access to do so by modifying the access using command(chmod 400 NextWorkAuroraApp.pem)

To help me create my web app, I first installed an Apache web server, php, php-mysqli extension and MariaDB which is a database management system.

---

## Connecting my Web App to Aurora

I set up my EC2 instance's connection details to my database by using my terminal to create a dbinfo.inc file and adding code into it using nano.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-webapp_1709b25b)

---

## My Web App Upgrade

Next, I upgraded my web app by adding a sample page(php file) that has a header and a form i can add data into.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-webapp_2709b25b)

---

## Testing my Web App

To make sure my web app was working correctly, I used MySQL CLI to make sure all the data added through the web app was accessible from the database.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-webapp_1409z22b)

---

---
