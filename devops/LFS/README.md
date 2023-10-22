---
title: Git on AWS
layout: default
nav_order: 3
parent: DevOps
permalink: /devops/git-on-aws
---

While working on a UE5 project, I initially used GitHub as the repo server. However, it quickly found out that it is not ideal for hosting projects with large binary files, as the free LFS allowance is a measly 1GB/month. This won't do, so I looked for other options.

One route I'm considering is using an AWS EC2 instance as the git lfs endpoint.

---

### Milestone 1 - Setup EC2 instance
As a first step, I need to setup an EC2 instance. 

* Setup a new instance via the EC2 console
    * Choose AWS Linux as the OS
    * Allot 30 GB of storage
* Assign a security group that would allow a few inbound rules
    * Add SSH support
    * Add ICMP echo request support
    * Add HTTP and HTTPS TCP support on ports 80 and 443 respectively
* Assign elastic IP to the instance
* Create an entry on Route 53 for the EC2 instance
    * Create an alias record for the domain, pointing to the elastic IP

---

### Milestone 2 - Setup git repo on an EC2 instance

* [Download](https://git-scm.com/downloads) and install git
* Setup git user on the EC2 instance
    * add os user
    * setup ssh keys
    * add user (sender) public keys to known_hosts
* Add the remote to the sender repo, and test push

---

### Milestone 3 - Setup S3 bucket

---

### Milestone 4 - Setup git lfs endpoint


---

* My attempts to follow the steps in [Derma's blog](https://blog.dermah.com/2020/05/26/how-to-be-stingy-git-lfs-on-your-own-s3-bucket/) has led to little progress. I have been able to sort of setup node-git-lfs in my ec2 instance but the server isnt accepting the files I'm pushing. It might be because I havent really configured my s3 buckets, or setup IAM in aws - I tried to see how it can be done and it seems a whole can of worms that I dont want to deal with right now.

So for now, I'm back to the drawing board with another potential solution - self hosted gitlab. I know gitlab supports LFS, but as with all live services, it would probably have file throughput limits in its free version. I can, however, try setting up a self-hosted instance on the ec2 machine. Maybe I can keep using github for the main repo and replace the lfs endpoint with the self hosted gitlab one?