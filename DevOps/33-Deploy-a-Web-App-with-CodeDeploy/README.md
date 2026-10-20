<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy a Web App with CodeDeploy

**Project Link:** [View Project](https://nextwork.ai/projects/836cda66-f725-5082-bdb3-0152b1d7a61b)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-27)

## Introducing Today's Project!

In this project, I will demonstrate how to build  a CI/CD pipeline that automats build and deployment. I'm doing this project to learn how to set up and use AWS CodeDeploy to deploy a web app to an EC2 instance.

### Key tools and concepts

Services I used were CodeBuild, CodeDeploy, EC2, S3, CloudFormation and IAM. Key concepts I learnt include packaing my scipts and code into artifacts and confiurin their deployment settins.

### Project reflection

This project took me approximately 3 hours. The most challenging part was troubleshooting script errors after pushing and trying rebuilding. It was most rewarding to see my web app render successfuly.

This project is part five of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project with CodePipeline.

## Deployment Environment

To set up for CodeDeploy, I launched an EC2 instance and VPC because I needed a separate deployment environment from development environment.

Instead of launching these resources manually, I used AWS CloudFormation. When I need to delete these resources I do not need to manually click through the console.

Other resources created in this template include Subnet, Route Tables, Internet Gateway and Security Group. They're also in the template because they are need for managing routing and secure network traffic entering and leaving the VPC environment.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-5)

## Deployment Scripts

Scripts are text files containing commands packaged togather to run automatically in sequence. To set up CodeDeploy, I also wrote scripts to configure network permissions, install Tomcat(Java application server) and start the application.

The 'install_dependencies will install dependencies needed to run and host the application like Tomcat and Apache which automate the the setup of the server environment before deployment.

The start_server.sh not only fires up the application but it also  ensures it stays running even if the server restarts by setting Tomcat and Apache to auto-start.

The stop_server.sh will ensure that the server is actively running before stoping the application in order to prevent errors that would occur from stoping inactiver servers.

## appspec.yml

Then, I wrote an appspec.yml file to provide an instruction manual for CodeDeploy to ensure the deployment moves in the right sequence. The key sections in appspec.yml are BeforeInstall, AfterInstall and ApplicationStart which are triggered at specific points during deployment.

I also updated buildspec.yml because I needed to include the scripts as part of the artifacts to outline automated the steps to take with the compiled code during deployment.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-12)

## Setting Up CodeDeploy

A deployment group is a collection of EC2 instances that are grouped to deploy something togather. A CodeDeploy application is a folder that organises everything related to the application's deployment.

To set up a deployment group, you also need to create an IAM role to provide permission to access other AWS services on my behalf.

Tags are helpful for identifying the target EC2 instance for deployment. I used the tag Key:role, Value:webserver to identify the instance I created using CloudFormation.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-18)

## Deployment configurations

Another key settings is the deployment configuration, which affects speed and security of the deployment. I used CodeDeployDefault.AllAtOnce, so all the instances in the deployment group deploy at the same time. Other options are CodeDeployDefault.OneAtATime and CodeDeployDefault.HalfAtATime.

In order to connect to the EC2 instance a CodeDeploy Agent is also set up to send the deployment instructions to the instance.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-20)

## Success!

A CodeDeploy deployment is a single update to an application with its unique ID and history. The difference to a deployment group is that it orchestrates the deployment process as opposed to the target EC2 insrtance.

I had to configure a revision location, which means where the CodeDeploy finds my artifact during deployment. My revision location was in S3.

To check that the deployment was a success, I visited the web app using the public DNS. I saw texts from my index.jsp file rendered  in the browser.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-27)

## Disaster Recovery

In a project extension, I decided to introduce an intentionl error in my stop_server.sh script. The intentional error I created was "sudo systemctll stop httpd.service". This will cause the deployment to fail because it was misspelled.'

I also enabled rollbacks with this deployment, which means if my deployment fails it reverts to the previous sccuessful deployment.

When my deployment failed, the automatic rollback also failed because the rollback only retries the deployment configuration not the artifact. To actually recover from unsuccessful deployment I'd have to implement a deployment recovery by rebuildin the application after fixin the scripts. In production environments automated rollbacks are implemented with more advanced tools like AWS CodePipeline eliminating the need for manual intervention.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_rollback-validation-upload)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/836cda66-f725-5082-bdb3-0152b1d7a61b)*
