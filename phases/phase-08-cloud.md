# Phase 8: Cloud Security Basics

Cloud platforms like AWS and Azure run a huge share of the world's systems, and most cloud breaches come from simple misconfigurations, not advanced hacking. This week you create your own free cloud accounts, launch a real server and storage bucket, break a bucket policy on purpose on your own bucket, then clean everything up so you are never charged.

## Day 71: What the cloud is and the shared responsibility model
- **Learn:** The cloud means renting computers and storage from big providers like AWS, Azure, and Google Cloud instead of buying your own hardware. The shared responsibility model splits the work: the provider secures the physical data centers and the core platform, while you secure your data, your accounts, and how you configure your resources.
- **Do:** Write down three examples from your daily life that match IaaS (renting a virtual server, like EC2), PaaS (a managed platform that runs your code), and SaaS (software you just use in a browser, like email). Next to each example, write one security task that is yours under the shared responsibility model, not the provider's.
- [ ] Done: You have one IaaS, one PaaS, and one SaaS example written down, each with one of your own security tasks.

## Day 72: Your first AWS account and IAM basics
- **Learn:** IAM (Identity and Access Management) controls who can do what in your AWS account through users, groups, and policies. Least privilege means every user gets only the permissions they truly need, and nothing more.
- **Do:** Create a free AWS account at https://aws.amazon.com/free/ (you need an email address and a card for identity verification, but the free tier costs nothing if you stay within its limits). Sign in to the console, open IAM, turn on MFA for your root account, and create one IAM user with the ReadOnlyAccess policy attached for your daily exploring.
- [ ] Done: You are signed in to the AWS console, MFA is on for the root account, and one read-only IAM user exists.

## Day 73: EC2, S3, and security groups
- **Learn:** EC2 gives you a virtual server you rent by the hour, S3 stores files as objects inside containers called buckets, and a security group is a virtual firewall that controls which network traffic can reach your EC2 instance.
- **Do:** Launch a free-tier EC2 instance (t2.micro or t3.micro with Amazon Linux), create one S3 bucket with the Block all public access setting turned on, then open the instance's security group and replace any SSH rule open to 0.0.0.0/0 with a rule that allows only your own IP address.
- [ ] Done: Your EC2 instance is running, your S3 bucket blocks all public access, and no inbound rule is open to the whole internet.

## Day 74: Azure basics through Microsoft Learn
- **Learn:** Azure is Microsoft's cloud, and its ideas map closely to AWS: a resource group is a folder that holds related resources, a virtual machine is like an EC2 instance, and Blob Storage is like S3. Once you learn one cloud, the second one is mostly new names for ideas you already know.
- **Do:** Work through the free cloud concepts module of the Azure fundamentals learning path at https://learn.microsoft.com (the sandbox exercises run in your browser, no paid account needed). Then write a small table that maps five AWS ideas (EC2, S3, IAM user, security group, region) to their Azure names.
- [ ] Done: You finished the Azure cloud concepts module and wrote a five-row AWS-to-Azure mapping table.

## Day 75: Cloud misconfigurations with your own S3 bucket
- **Learn:** Misconfigured storage is one of the most common causes of real cloud breaches, and attackers scan the internet for open S3 buckets every day. A bucket policy is a JSON document that decides who can read or write a bucket, and a single wrong line can expose everything inside it.
- **Do:** Using only the test bucket you created on Day 73, first confirm that Block all public access is on, then attach a bucket policy that allows public reads and refresh the page to see the console's public warning badge appear. Delete the policy right away, confirm the bucket is private again, and never try this on anyone else's bucket.
- [ ] Done: You watched the public warning badge appear and disappear on your own test bucket, and it ends the day fully private.

## Day 76: Docker and containers basics
- **Learn:** A container packages an application with everything it needs to run, so it behaves the same on any machine. Docker is the most common tool for running containers, and Docker Hub is a public registry of ready-made images, so always check what an image contains before you run it.
- **Do:** Open https://labs.play-with-docker.com in your browser (free, runs in the browser, no install needed), start a new session, and run this command: docker run -d -p 80:80 nginx. Click the port 80 badge to see the nginx welcome page, then stop and remove the container with docker stop and docker rm.
- [ ] Done: You ran an nginx container, saw its welcome page in your browser, and stopped and removed the container.

## Day 77: Review, clean up, and notes
- **Learn:** Reviewing from memory locks the week's ideas in place, and cleaning up resources is a professional habit because forgotten servers and storage keep billing you. Today you test yourself first, then shut down everything you built this week.
- **Do:** Without looking at your notes, write down the top five cloud misconfigurations from memory (examples: public S3 buckets, security groups open to the world, missing MFA, overprivileged IAM users, unencrypted storage). Then open the AWS console, terminate your EC2 instance, delete your S3 bucket and extra IAM user, and check the Billing dashboard to confirm nothing billable is still running.
- [ ] Done: You listed five misconfigurations from memory, deleted every resource you created this week, and the billing dashboard shows nothing still running.
