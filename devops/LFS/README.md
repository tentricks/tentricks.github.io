---
title: Git on AWS
layout: default
nav_order: 3
parent: DevOps
permalink: /devops/git-on-aws
---

While working on a UE5 project, I initially used GitHub as the repo server. However, it quickly found out that it is not ideal for hosting projects with large binary files, as the free LFS allowance is a measly 1GB/month. This won't do, so I looked for other options.

One route I'm considering is using an AWS EC2 instance as the git lfs endpoint.

