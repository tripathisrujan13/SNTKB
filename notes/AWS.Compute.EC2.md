---
id: al7h3bpzkog71s39amkbxgy
title: EC2
desc: ''
updated: 1691520935232
created: 1691517134108
tags: EC2
---

## Elastic Cloud Compute (EC2)

### Uses
 - Allows for deployment of virtual servers within #AWS environment.

### Components
 - **Amazon Machine Images (AMIs)**: Preconfigured #EC2 templates that contain OS, binaries, etc
 - **Instance Types**: Different combinations of various parameters such as number of virtual CPUs, clock speed, memory, etc. There are different presets that are designed for different workloads.
 - **Instance Purchaising Options**: Can be on-demand, reserved, scheduled, or spot (fluctating price)
 - **Tenancy**: Which underlying host the EC2 instance will reside on. Can be shared tenancy or dedicated.
 - **User Data**: Commands that will be executed during the boot sequence of the instance.
 - **Storage Options**: Persistent or ephemeral (temporary) storage. Persistent storage uses [[EBS|AWS.EBS]] (Elastic Block Storage).
 - **Security**: Security groups, which dictate what inbound & outbound traffic is permitted.

### Health Monitoring Status Checks 
 - **System**: Failure indicates issue with underlying host. Restarting process will allow for instance to spin up on a different host, most likely resolving issue.
 - **Instance**: Failure indicates issue with instance configuration. Must be manually debugged.

 ### EC2 #Auto-Scaling
  - Mechanism that allows for automatic increase/decrease of EC2 resources to meet demand based on custom metrics/thresholds.
  - Launch Configuration/Launch Template defines how an [[Auto Scaling Group|AWS.Compute.EC2.AutoScalingGroup]] builds new EC2 instances
  - Scaling Policy Types:
    - Manual Scaling
    - Schedule Scaling
    - Dynamic Scaling
    - Predictive Scaling