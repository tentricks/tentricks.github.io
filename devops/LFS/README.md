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



