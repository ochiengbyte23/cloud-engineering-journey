<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Continuous Integration with CodeBuild

**Project Link:** [View Project](https://nextwork.ai/projects/92664c9b-5395-50c5-82bc-e72e574a6140)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_35588a47)

## Introducing Today's Project!

In this project, I will demonstrate how to automte the build process of my web app using AWS CodeBuild. I'm doing this project to learn about the CI/CD pipeline that automates the build and development process of a web app.

### Key tools and concepts

Services I used were AWS CodeBuild, CodeArtifact,IAM, S3 andEC2 instance. Key concepts I learnt include CI pipeline automation using CodeBuild, managing secure buildspec.yml configurations, Maven dependency retrieval, and S3 artifact storage..

### Project reflection

This project took me approximately 3 hours to complete. The most challenging part was getting an error due an indentation in the  buildspec.yml file which resulted in an unsucessful build. It was most rewarding to successfully pass all my test phase of my run-test.sh file.

This project is part four of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project Deploying an App with CodeDeploy.

## Setting up a CodeBuild Project

CodeBuild is a continuous integration service, which means it constantly checks that everything works as expected by compiling the source code, testing and packaging it. Engineering teams use it because you don't have to manually set up and manage it, and you only pay for the compute time you use building your project instead of entire servers that are idle most of the time.

My CodeBuild project's source configuration means the location of the code it will fetch, compile and package into a deployable file, and I selected Github.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_fewgrhte)

## Connecting CodeBuild with GitHub

There are multiple credential types for GitHub, like GitHub App, personal access token and OAuth app. I used GitHub App because it is the simplest and most secure option to set up.

The service that helped connect my AWS account to Github is CodeConnect. Instead of connecting using API keys or tokens, CodeBuild handles these complexities so that I can focus on building the application.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_a7c98e2d)

## CodeBuild Configurations

### Environment

My CodeBuild project's Environment configuration means setting up the blueprint for the machine, operating sysytem and resources used to execute build, it includes settings like provisioning model, environment image, compute and running mode.

### Artifacts

Build artifacts are outputs of the build process. They're important because they're what are distribted to servers or users for deployment. My build process will create one build artifact that packages everything a server could need to host a web app in one bundle (WAR file). To store them, I created an S3 storage since it is safe and scalable.

### Packaging

When setting up CodeBuild, I also chose to package artifacts in a Zip file because it is small in size, simple to share and manages all the files in one place.

### Monitoring

For monitoring, I enabled CloudWatch Logs, which is a monitoring srvice that collects and tracks logs from AWS services. In this project, it will record everything that happens in the build process.

## buildspec.yml

My first build failed because my GitHub repository lacked a buildspec.yml file. A buildspec.yml file is needed because it outlines how to build the project step by step.

The first two phases in my buildspec.yml file (install and pre-build) lay the ground work before building by specifiying what to do and what to install. The third phase in my buildspec.yml file (build) is where the actual building of the project starts. The fourth phase in my buildspec.yml file (post_build) are where the finishing touches after main build like packaging everything into a WAR file is done.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_35588a47)

## Success!

My second build also failed, but with a different error that said "COMMAND_EXECUTION_ERROR: Error while executing command: CODEARTIFACT_AUTH_TOKEN=...". To fix this I need to give my CodeBuild access to CodeArtifacts which is needed to access some dependencies.

To resolve the second error, I gave my CodeBuild permission to access CodeArtifact. When I built my project again, I saw all the phases succeed.

To verify the build, I checked my S3 bucket for an artifact. Seeing the artifact tells me that all the phases of the build process were successfully completed.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_d9cc6191)

## Automating Testing

In a project extension, I'm creating a simple test unit to view automatic test run during build. I added a test script that checks wether the src directory and index.js file exists.

To add the test script to the build process, I created a test file in the project's root folder, updated my buildspec.yml to include the test, pushed these changes to GitHub and started a new buld in CodeBuild with the updated GitHub repository.

I pushed my buildspec.yml to GitHub and initiated a new CodeBuild run. The build logs confirmed that the pre-build phase successfully triggered run-tests.sh, resulting in a clean test pass!

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_sm-test-script-upload)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/92664c9b-5395-50c5-82bc-e72e574a6140)*
