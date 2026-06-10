<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com


## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use Amazon S3 to store a static website. I'm doing this project to learn how to store objects and host websites using AWS cloud service

### Tools and concepts

Services I used were Amazon S3. Key concepts I learnt include bucket policies, static website hosting, bucket list endpoints and Access Control List(ACL) object access control

### Time, challenges, and wins

This project took me approximately 1/5 hours including quize, demo and secret misssion.The most challenging part was resolving the 403 forbidden error. It was most rewarding to be able to publicly access my website.

---

## How I Set Up an S3 Bucket

### What I did in this step

In this step, I will open Amazon S3 and create a storage space to store files

### How long it took to create the bucket

Creating an S3 bucket took me took me about 6 munites .I was also learning a lot of new stuff in the process so i reckon in future i will be able to do it in 2 minutes

### Region selection

The Region I picked for my S3 bucket was the default US East (N. Virginia) us-east-1 because none of the available regions were close to me(Kenya). I tried to set to South Africa but it supposedly should take time to set up which i di not have

### Understanding bucket name uniqueness

S3 bucket names are globally unique! This means my name cannot be used by anyone else world wide unless i dete my bucket

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### What I did in this step

In this step, I will upload the HTML and zip image files to my S3 bucket because they are the ingradients for static website hosting

### Files I uploaded

I uploaded two files to my S3 bucket - they were the HTML and zip files. The HTML determines the layout of the website while the zip files provides images for the website

### How the files work together

Both files are necessary for this project as the index.html does only provides the sturucture of yhe website. In order to complete it , the zip files provides the required assets like images which makes the website structure functional.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

### What I did in this step

In this step, I will make my website publicly available through static website hosting because withou it my files will just stay as files

### Understanding website hosting

Website hosting means to store and serve HTML and zip files as a website page to be publicly accessible through a server likes aws

### How I enabled website hosting

To enable website hosting with my S3 bucket, I went to the properties tab of my bucket and enabled static web hosting after which i was able to input my HTML file name

### Access Control Lists (ACLs)

An ACL is a set of rules used to control access to individual objects in a bucket. I enabled ACL as it was required for this project. However Bucket Policies is an easier alternative since it allows control from the bucket level

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

### Understanding bucket endpoint URLs

Once static website is enabled, S3 produces a bucket endpoint URL, which is a unique address that can be used to publicly access my website

### What I saw when I tested the endpoint

When I first visited the bucket endpoint URL, I saw a 403 forbidden error message. The reason for this error was that my hosted files i.e HTML and zip are private by default. So to enable the URL i need to make the files public.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

### What I did in this step

In this step, I will make my website publicly accessible because this enables me to view the website contents

### How I resolved the 403 error

To resolve this 403 Forbidden error, I made my object files public using ACL which controls object access

---

## Bucket Policies

### What I did in this extension

In this project extension I'm about to setup a bucket policy which controll access to my files from the bucket level. I'm doing this so that no one can delete my index.html file

### Understanding bucket policies

An alternative to ACLs are bucket policies, which are JSON based policies attached to the S3 buckets. The benefit of using bucket policies is it controls who access the bucket and its objects and what actions the can do while ACLs are useful for object level access control

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

My bucket policy prevents anyone from deleting any object in my bucket. I tested this by trying to delete my index.html file and saw an error that prevented me from compeleting the deletion

---

---
