<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a Web App in the Cloud

**Project Link:** [View Project](https://nextwork.ai/projects/b71d29bd-8a1b-5fe0-9572-1c575423d558)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_7a1de541)

## Introducing Today's Project!

In this project, I will demonstrate how to launch an EC2 instance, use VScode to set up a remote SSH connectionto the EC2 instance, Install Maven and Java and generate a basic web app. I'm doing this project to learn how to set up a web app in the cloud as part of my 6 day DevOps challenge.

This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project in the series, Connect a GitHub Repo with AWS, where I will connect my server to my repository to enable automatic triggers for the next build stages.

I did this project because understanding virtual networking, host security, and remote developer environments is crucial for building reliable, real-world deployment pipelines and setting up production-ready cloud architectures.

### Key tools and concepts

Services I used were Amazon EC2 and VPC. Key concepts I learnt include hosting web application using EC2 and setting up remote-SSH to manage files.

### Project reflection

This project took me approximately 2.5 hours. The most challenging part was realising I couldn't run Windows icacls commands directly inside a Linux-style terminal.. It was most rewarding to set up VS Code Remote-SSH to edit files directly on my EC2 instance and seeing them sync instantly.

One thing I didn't expect in this project was how seamless the remote editing experience would be. I didn't expect my terminal edits to sync with my VS Code window instantly.

## Launching an EC2 instance

### What I did in this step

In this step, I will launch an EC2 instance, set up key pair for secure access and set up network settings for the instance because it provides a space to house the development work.

I started this project by launching an EC2 instance because it will provide the enironment for developing the web .

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_7852fbf3)

### I also enabled SSH

SSH is a protocal that ensures only authorised users can access a remote server. It is also a type of network traffic which ensures all data transfered between the user an the remote server is encrypted. I enabled SSH so that only I, can be able to acces my EC2 instance using my private key.

### Key pairs

A key pair is a pair of private and public access logins to unlock a virtual server/computer. The public key is kept by AWS while I download the private key to my local device.

### Downloaded key pair file

Once I set up my key pair, AWS automatically downloaded my private key with .pem formart for local storge.

## Set up VS Code

### What I did in this step

In this step, I will set up a terminal in my VS Code so i can communicate with my EC2 instance and update my key pair's permission settings so that I can log in to my EC2 instance later because it enables me to access my EC2 instance from remotely from a local device.

### What is VS Code?

VS Code is  a tool for creating and managing coding projects by providing a platform for writing editing code.

I installed VS Code to be able to communicate with my EC2 instace remotely.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_53d05e68)

## My first terminal commands

A terminal is where you send instructions to your computer with texts instead ofclicks. The first command I ran for this project is "cd ~\Desktop\DevOps" in order to navigate to the folder containing the private SSH key pair login.

### Updating file permissions

I also updated my private key's permissions by running the command "icacls "nextwork-keypair.pem" /grant:r "hp:R"" so that noone except me can read the file. I also ran "icacls "nextwork-keypair.pem" /inheritance:r" to stop the file from inheriting any permission from the parent folder.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_9328ada1)

## SSH connection to EC2 instance

### What I did in this step

In this step, I will connect my EC2 instance because it enables me to work inside the instance remotely through VS code.

### Connecting to EC2

To connect to my EC2 instance, I ran the command "
ssh -i "C:\Users\HP\Desktop\DevOps\nextwork-keypair.pem" ec2-user@ec2-13-200-246-141.ap-south-1.compute.amazonaws.com" which used my instance's public DNS to connect to my file through VS Code.

### This command required an IPv4 address

A server's IPV4 DNS is the public address that the internet uses to find and connect to it. The local computer I'm using to do this project will find and connect to my EC2 instance through the DNS address.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_e3069dca)

## Maven & Java

### What I did in this step

In this step, I will install Apache Maven and Amazon Corretto 8 on my EC2 instance because they help set up the web app.

### Why I'm using Maven

Apache Maven is a tool that helps developers to build and organise software projects. It is also a package manager and provides archetypes(templates) for various types of projects like web apps.

Maven is required in this project because I will be using its tools, package manager and web app archetypes when building and setting up my web app.

### Why I'm using Java

Java is a popular programming language used to build different types of applications.

Java is required in this project because we are using Maven to build our web app. Maven NEEDS Java to operate.

## Create the Application

### What I did in this step

In this step, I will run Maven commands in my terminal because I need to generate a Java web app.

### Creating the Java web app

I generated a Java web app using the command "
mvn archetype:generate 
-DgroupId=com.nextwork.app 
-DartifactId=nextwork-web-project 
-DarchetypeArtifactId=maven-archetype-webapp 
-DinteractiveMode=false".

### Installing Remote - SSH

I installed Remote - SSH, which is an extension tool for connecting to remote servers/computres seurely. I installed it to edit files and run programmes in my EC2 instance as if I was doing it in my own computer.

### SSH configuration details

Configuration details required to set up a remote connection include my EC2 instance public DNS and my private key file path.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_2939cf01)

## Create the Application

### Exploring the project structure

Using VS Code's file explorer, I could see the nextwork web project folder in my instance which icluded sub-folders and files like src, pom.xml and more.

Two of the project folders created by Maven are src and webapp, which holds all the source code files which define how the web app will look and function.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_45f91fd7)

## Using Remote - SSH

### What I did in this step

In this step, I will connect my VS Code to the EC2 instance directly using an extension in VS Code because it will enable me to explore and edit my Java web app's files using VS Code.

### Updating the web app

The index.jsp is a file used in Java web app similar to HTML because it contains markup to display web pages. index.jsp can also include Java code which makes it generate dynamic content.

I edited index.jsp by adding a heading and paragraph:
<h2>Hello Bildad!</h2>
<p>This is my NextWork web application working!</p>

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_7a1de541)

## Using nano

### Additional improvements

In this secret mission, I will edit code using the terminal instead of the IDE because it enables me to edit the files without the Remote-SSH access.

### Terminal vs IDE

An alternative to using IDEs is the terminal. To edit index.jsp, I ran the command nano index.js.

Compared to using an IDE, editing index.jsp in the terminal felt old school. I'd be more likely to use an IDE if I need to make large changes since it unlocks file navigation and modern editor features.

### Verifying my work

To verify my editing work in the terminal, I switched back to my Remote-SSH window. It was possible to see my changes in VS Code right away because both VS Code and terminal are connected directly to the same EC2 instance and any changes are updated across both views instantly.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_a3324ad41)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/b71d29bd-8a1b-5fe0-9572-1c575423d558)*
