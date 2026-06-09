# 01 — Getting Started with the AWS Free Tier

**Author:** Bildad Masaga
**Platform:** [NextWork](https://nextwork.org)

---

## What This Project Is About

Setting up an AWS account is the first step in any cloud engineering journey. This project covers creating an account, understanding the Free Tier, securing the account with MFA, and setting up billing alerts to avoid unexpected charges.

---

## What I Did

### 1. Created My AWS Account
- The signup process took about 10 minutes, but account approval took a few days
- AWS asks for credit card details during signup — this is just to verify you're a real person, not to charge you
- Once approved, I got access to the AWS Management Console

### 2. Explored the AWS Free Tier
The Free Tier includes three types of offers:

| Type | Duration | Example Services |
|------|----------|-----------------|
| Always Free | No expiry | Lambda, DynamoDB (limited usage) |
| 12 Months Free | From signup date | EC2, S3, RDS, CloudFront |
| Short-term trial | 6 months | $100 AWS credits for select services |

> ⚠️ After the 12-month period, free access to services like EC2, S3, RDS, and CloudFront ends — save your signup date!

### 3. Set Up Billing Alerts
- Enabled Free Tier usage alerts in the Billing console
- This sends an email notification if I'm approaching or exceeding free usage limits
- Helps avoid surprise charges while learning

### 4. Secured the Account with MFA
- Enabled Multi-Factor Authentication (MFA) on the root account
- MFA adds a second layer of security — even if your password is stolen, attackers can't get in without the second factor
- Best practice: never use the root account for day-to-day work

---

## Key Concepts Learned

- **Root user vs IAM user** — the root account has unrestricted access; you should create an IAM user for everyday tasks
- **AWS Free Tier** — three tiers of free access; knowing the limits prevents accidental charges
- **MFA** — essential security step for any AWS account
- **Billing alerts** — proactive cost monitoring from day one

---

## Challenges & Wins

**Challenge:** Waiting a few days for account approval was unexpected — I assumed it would be instant.

**Win:** Understanding the difference between the 6-month credits, 12-month Free Tier, and always-free services. They're easy to confuse at first.

---

## Next Steps

- Create an IAM user and stop using the root account
- Start the first hands-on project: web hosting on AWS
