<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Packages with CodeArtifact

**Project Link:** [View Project](https://nextwork.ai/projects/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_1d79e699)

## Introducing Today's Project!

In this project, I will demonstrate how to set up CodeArtifact as a repository for my project's dependencies, use IAM roles and policies to give my web app access to CodeArtifact and verify my web app's connection to CodeArtifact. I'm doing this project to learn how to secure packages with CodeArftifacts.

### Key tools and concepts

Services I used were CodeArtifact, EC2 and IAM. Key concepts I learnt include creating CodeArtifact repositories, creating policies to allow EC2 instance to access CodeArtifact, attaching the policy to an IAM role of the instance, creating a custom package and validating it via dowloadeding.

### Project reflection

This project took me approximately 2.5 hours. The most challenging part was upgrading my instance type for more RAM since my previous RAM was too small for the project. It was most rewarding to retrieive the file I used to create a custom package from the repository.

This project is part three of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project Continuous Integration with CodeBuild, to automate the packaging of my Java web application..

## CodeArtifact Repository

CodeArtifact is a secure and central place to store all my software packages for the project. Engineering teams use artifact repositories because it ensures the team can retrieve the packages from a secure source, it provides backup incase public package websites goes down and ensures the team uses and shares the same versions of the packages.

A domain is like a folder that holds multiple repositories beloging to the same project. My domain is manager for security settings and permissions acrooss all the repositories inside it.

A CodeArtifact repository can have an upstream repository, which means it will have a backup library when it lacks a package that I need. My repository's upstream repository is Maven Central which is the most popular public library for java .

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_n4o5p6q7)

## CodeArtifact Security

### Issue

To access CodeArtifact, we need an authorisation token which gives me the permission to access the Codertifacts. I ran into an error when retrieving a token because the EC2 instance dosen't have permission to access other AWS services by default which includes CodeArtifact.

### Resolution

To resolve the error with my security token, I created an IAM role which included policies giving my instance permission to access CodeArtifact and attached it to the instance. This resolved the error because it generated a tempoary token that is used any time i need to grab something from the CodeArtifact.

It's security best practice to use IAM roles because you can attach the same policy to multiple roles and a role can have multiple policies attached.

## The JSON policy attached to my role

The JSON policy I set up grants permission to get authorisation token from CodeArtifacts, retrieve the endpoint of a CodeArtifact repository and read its packages. A second statement employs the principle of least privillege to ensure the temporary token is only used for CodeArtifact access.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_23rp7q8r9)

## Maven and CodeArtifact

### To test the connection between Maven and CodeArtifact, I compiled my web app using settings.xml

The settings.xml file configures Maven to access CodeArtifact when it needs a dependency, telling it which repository to draw from and how.

Compiling means tranlating code into a language that computers can understand.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_c17eace8)

## Verify Connection

After compiling, I checked for packages in my CodeArtifact console. I noticed a list of packages from Maven after refreshing the console.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_1d79e699)

## Uploading My Own Packages

In a project extension, I also decided to create a custom package, publish it to CodeArtifacts repository and experience the full package lifecycle by downloading it. This is useful in situations where companies need internal libraries they can share among themselves privately.

To create my own package, I created a sample file, bundled it and compressed it. I also generated a security hash because it ensures the file is not corrupted during transfer to the CodeArtifact repository.

To publish the package, I deployed a custom package using AWS CLI. When I look at the package details in CodeArtifact, I can see when it was published, the version , the origin,  and the security hashes calculated for the package.

I validated the package by downloading it directly from the CodeArtifact repository. Viewing the extracted content confirmed that the exact text from my sample file was successfully preserved.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_sm12-upload)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67)*
