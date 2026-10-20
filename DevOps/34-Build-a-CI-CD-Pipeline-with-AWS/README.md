<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a CI/CD Pipeline with AWS

**Project Link:** [View Project](https://nextwork.ai/projects/7ade5e2f-0020-55fb-9bba-abede6ce1de9)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7ade5e2f-0020-55fb-9bba-abede6ce1de9_fbdetger)

## Introducing Today's Project!

In this project, I will demonstrate how to automate the CI/CD pipeline using AWS CodePipeline. I'm doing this project to learn how to avoid manual confiurations during the CI/CD process like manually building artifacts.

### Key tools and concepts

Services I used were CodeDeploy, CodeBuild, CodePipeline, EC2, CloudFormation and S3 . Key concepts I learnt include CodePipeline stage configuration and how CodeDeploy handles automated deployment rollbacks.

### Project reflection

This project took me approximately 2.5 hours. The most challenging part was. It was most rewarding to view the rendered web app after updating my code.

I chose to do this project today because it is part of my CI/CD pipeline upskilling journey. 

## Starting a CI/CD Pipeline

AWS CodePipeline is a service used to automate the build and deployment stages automatically whenever there is change in the code.

CodePipeline offers different execution modes based on number of execution taking place at a time. I chose Superseded because it cancels the an old execution if a new one is triggered while the old one is still in progress. Other options include Queued and Paralled.

A service role gets created automatically during setup so that the CodePipeline can have the right permission to access other AWS services.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7ade5e2f-0020-55fb-9bba-abede6ce1de9_gdnhtm)

## CI/CD Stages

The three stages I've set up in my CI/CD pipeline are the Source, Build and Deploy. While setting up each part, I learnt about fetching the source artifact of each stage from the previous stage to enable continuous communication.

CodePipeline organizes the three stages into a pipeline diagram. In each stage, you can see more details on the stage ID.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7ade5e2f-0020-55fb-9bba-abede6ce1de9_fbdetger)

## Source Stage

In the Source stage, the default branch tells CodePipeline where to fetch the latest version of my code whenever i make an update.

The source stage is also where you enable webhook events, which notify the CodePipeline whenever you puch a code to a set branch so that a new pipeline execution can start.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7ade5e2f-0020-55fb-9bba-abede6ce1de9_sergt)

## Build Stage

The Build stage sets up to use AWS CodeBuild. I configured the input artifact to SourceArtifact. The input artifact for the build stage is the zip file from the previous source code.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7ade5e2f-0020-55fb-9bba-abede6ce1de9_j1k2l3m4)

## Deploy Stage

The Deploy stage is where I configured the deployment of the artifact from the Build stage to the EC2 server. I configured Deploy provider, application name and deployment group.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7ade5e2f-0020-55fb-9bba-abede6ce1de9_m4n5o6p7)

## Success!

Since my CI/CD pipeline gets triggered by pushing changes to my GitHub's master repository. I tested my pipeline by adding a line in index.jsp and puching the updated code to Github.

The moment I pushed the code change the CodePipeline started a fresh build. The commit message under each stage reflects the message i used to push the code to GitHub and shows that the CodePipeline is in action.

Once my pipeline executed successfully, I checked my public IPv4 DNS to confirm that my update was rendered.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7ade5e2f-0020-55fb-9bba-abede6ce1de9_e1f2g3h4)

## Testing the Pipeline

In a project extension, I initiated a rollback on the Deploy stage. Automatic rollback is important for undoing a deployment when an error is encountered by reverting to previous deployment.

During the rollback, the source and build stage are unaffected because only the deployment configuration should have failed for te execution to reach the deploy stage. I could verify this by comparing the deploy stage commit hash with stages for source and build. 

After rollback, the live web app reverted to the previous render minus the update.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7ade5e2f-0020-55fb-9bba-abede6ce1de9_sdfgsdfgdf)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/7ade5e2f-0020-55fb-9bba-abede6ce1de9)*
