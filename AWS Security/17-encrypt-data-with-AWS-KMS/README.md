<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Encrypt Data with AWS KMS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-kms)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-kms_w0x1y2z3)

---

## Introducing Today's Project!

In this project, I will demonstrate how to create an encryption key with AWS Key Management Service(KMS) and use it to encrypt a DynamoDB database, add and retrieve data from the database to test encryption and observe how AWS stops unauthorised access to my data. The goal is to set up a secure access to resources.

### Tools and concepts

Services I used include AWS Key Management Service, DynamoDB, AWS IAM. Key concepts I learnt include encryption, decryption, database table security, KMS management.

### Project reflection

This project took me approximately 1.5 hours including the documentation. The most challenging part was understanding how different encryption tools other than KMS work.  It was most rewarding to view data after changing permission policy to allow decryption.

I chose to do this project today because it is part of my cloud engineering journey.

---

## Encryption and KMS

Encryption is the process of using algorithms to convert data into a secure format called cipher text. Companies and developers do this to to control access to resources securely. Encryption keys are instruction manuals for how the encryption algorithm will transform the normal text to cipher text.

AWS KMS is a secure vault for my encryption keys. Key management systems are important because they enable me to create, manage and use encryption keys that protect my data from unauthorised access.

Encryption keys are broadly categorized as symmetric or asymmetric. I set up a symmetric key because it uses a single key to encrypt and decrypt which is faster and efficient especially for large data sets which is why I am using DynamoDB.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-kms_a2b3c4d5)

---

## Encrypting Data

My encryption key will safeguard data in DynamoDB, which is a non-relational database that stores items with different attributes. DynamoDB uses a partition key to split and search for data in the table quickly.

The different encryption options in DynamoDB include AWS owned key, AWS managed key and customer managed key. Their differences are based on access and management. I selected customer managed key because i want to have full control of my encryption  key.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-kms_q8r9s0t1)

---

## Data Visibility

Rather than controlling who has access to the key, KMS manages user permissions by specific permissions which allow users to do a specific action like encrypt or decrypt.

Despite encrypting my DynamoDB table, I could still see the table's items because I am authorised to have full control as an admin and user to the key. DynamoDB uses transparent data encryption, which means data is stored securely at rest yest still accessible to authorised users with the right permissions.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-kms_c0d1e2f3)

---

## Denying Access

I configured a new IAM user to have to my AWS management console . The permission policies I granted this user are full access to my Amazon DynamoDB tables but not the KMS key.

After accessing the DynamoDB table as the test user, I encountered an decryption error because the test user does not have permission to access the KMS key used to encrypt the database. This confirmed that the KMS key actually protects my data from unauthorised users who do not have the right permissions.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-kms_w0x1y2z3)

---

## EXTRA: Granting Access

To let my test user use the encryption key, I added the test user in the key policy as a key user. My key's policy was updated to allow the test user to encrypt, decrypt, and re-encrypt .

Using the test user, I retried to view the data in DynamoDB table and observed that the test user can view the data which confirmed that only user with permissions keys for decryption can view the data.

Encryption secures data instead of an entire service or resources. I could combine encryption with other access control tools like security groups and permission policies to have two security layers: the resource level and the data level.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-kms_feffb2fb8)

---

---
