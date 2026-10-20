<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect a GitHub Repo with AWS

**Project Link:** [View Project](https://nextwork.ai/projects/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_dd9d254e)

## Introducing Today's Project!

In this project, I will demonstrate how to set up Git and Github and connect my web app to a Github repo. I'm doing this project to learn about Git and Github, and how it changes along with the code update as part of my 6-day DevOps challenge.

### Key tools and concepts

Services I used were EC2, Git and Github. Key concepts I learnt include setting up Git configurations, Git and GitHub connections, and README.md features.

### Project reflection

This project took me approximately 2 hours. The most challenging part was connecting the remote SSH to an EC2 instance in a region without slow traffic. It was most rewarding to be able to instantaniously view all my Git versions and review them before pushing.

I did this project because I wanted to build confidence in deploying cloud environments, understanding SSH configuration files, and managing secure file permissions.

This project is part two of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project, Secure Packages with CodeArtifact. In this next stage, I will learn how to securely manage, store, and share your application's software dependencies using AWS CodeArtifact.

## Git and GitHub

Git is like a time machine and filing system for code since it tracks changes enabling me to view who made the change and where while also being able to backtrack to an older version of the code if something goes wrong. I installed Git using the commands "sudo dnf install git -y" and confirmed the installment with "git --version"...

GitHub is a storge space for different versions of my project that Git tracks. I'm using GitHub in this project to to help me use Git and view my file changes in a user friendly way.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_efaadbf7)

## My local repository

A Git repository is a folder that contains all my project's files and the entire version history of the project.

Git init is a command that sets up a directory that acts a local git repository. I ran git init in the dirctory:nextwork-web-project commencing tracking for version control.

A branch in Git is a parallel version of the same project. After running git init, the response from the terminal was a heads up about the standards for naming the main branch.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_7bf21bae)

## To push local changes to GitHub, I ran three commands

### git add

The first command I ran was "git add ." which stages all the files in the project to be saved in the next version of the project. A staging area is is where all modified files are placed for review before commiting.

### git commit

The second command I ran was git commit -m "Updated index.jsp with new content"  which saved all the staged changes as a snapshot in my project's history. Using '-m' means the following message is a brief description of what the commit is about making reviewing it easier.

### git push

The third command I ran was "git push -u origin master" which pushes the committed changes to origin which i bookmarked as my GitHub repo. Using '-u' means setting an upstream for my local branch which will remember to push to master by default.

## Authentication

When I commit changes to GitHub, Git asks for my credentials because it has to authenticate that i have the rights to push said changes to GitHub.

### Local Git identity

Git needs my name and email because it uses this information to track who made the changes. This is useful in a group project with multiple developers

Running git log showed me that the history of commits which includes commits author's name.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_9a27ee3b)

## GitHub tokens

GitHub authentication failed when I entered my password because it has phased out password authentication to connect with repositories over HTTPS due to too many ssecurity risks and passwords can get intercepted over the internet.

A GitHub token is a unique string of characters used to securely authenticate Git operations. I'm using one in this project because  disabled regular password authentication for terminal commands like pushing code.

I could set up a GitHub token by navigating to my GitHub Settings, opening Developer Settings, and selecting Personal Access Tokens. From there, I generate a classic token with the required 'repo' permissions and copy it.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_fa11169d)

## Making changes again

I wanted to see Git working in action, so I updated index.jsp file. I couldn't see the changes in my GitHub repo initially because the local repository in VSCode is separate from your GitHub repository in the cloud.
To make my changes visible in GitHub, I needed to write commands and send (push) them from my local repository into my origin.

I finally saw the changes in my GitHub repo after staging, committing with messages and pushing the changes to GitHub.

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_6becb2bc)

## Setting up a READMe file

As a finishing touch to my GitHub repository, I added a README file, which is a document that introduces and explains my project, like what the project does, how to set it up, and how to use it. I added a README file by using the command "touch README.md".

My README is written in Markdown because it is a text language that lets you format text that you'll display on a webpage. Special characters can help you format text in Markdown, such as **text** to make text bold and # for largest header (H1).

My README file has 6 sections that outline the title, table of contents, introduction, technologies used, set up, contact and conclusion..

![Image](https://nextwork.ai/loving_rose_daring_rose_apple/uploads/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3_c94976902)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/7e90bd3d-4280-57c7-ba1f-0fb7cf5673f3)*
