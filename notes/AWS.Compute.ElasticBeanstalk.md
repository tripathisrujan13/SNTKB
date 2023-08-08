---
id: w7ae6vdgexki6jhjmpuavm8
title: ElasticBeanstalk
desc: ''
updated: 1691524713119
created: 1691517157807
---

## Elastic Beanstalk

### Uses
 - Service that accepts code for web application and environment configuration, then automatically provisions and deploys necessary resources to operate the web application.
 - Designed for engineers who do not have the confidence or knowledge to handle #AWS architecture.

### Environments
 - Web Server Environment
     - Architecture:
        ```mermaid
        flowchart LR
        n1["Route 53"]
        n2["ELB"]
        n3["Auto Scaling"]
        n4["EC2 Instances"]
        n5["Security Groups"]
        n1 --> n2
        n2 --> n3
        n3 --> n4
        n4 --> n5
        ```
       1. [[Route 53|AWS.Route53]]: Directs web traffic to correct servers.
       2. [[ELB|AWS.Compute.ELB]] (Elastic Load Balancer): Automatically distributes incoming traffic and scales to meet demand.
       3. #Auto-Scaling: Manage capacity planning based on load received.
       4. #EC2 Instances: Part of [[Auto-Scaling Group|AWS.Compute.EC2.AutoScalingGroup]].
       5. Security Groups: Allows port 80 to be open to all.
   - Each #EC2 instance has a Host Manager that orchestrates it.
- Worker Environment
  - Architecture:
      ```mermaid
      flowchart LR
      n1["SQS Queue"]
      n2["Auto Scaling"]
      n3["IAM Service Role"]
      n4["EC2 Instaces"]
      n1 --> n2
      n2 --> n3
      n3 --> n4
      ```
    1. [[SQS Queue|AWS.SQSQueue]]: Automatically created by #AWS Beanstalk.
    2. #Auto-Scaling: Same as #3 above.
    3. [[IAM Service Role|AWS.IAMServiceRole]]: Allows #EC2 instances to interface with [[SQS Queue|AWS.SQSQueue]].
    4. #EC2 Instances: Same as #4 above.
  
Both environments can be used in conjuction, coupled by [[SQS|AWS.SQSQueue]]. This allows each environment to scale independently.

### Deployment
 - All at Once (Default): Updates all resources at once. Can cause interruptions.
 - Rolling: Deploys in batches, minimizing disruption.
 - Rolling with additional batch: Same as rolling, but adds additional batches to maintain availabilty.
 - Immutable: Creates entirely new instances, then old environment is deleted.

### Health Check Colors
 - Basic
     - Grey: Environment is being updated.
     - Green: Environment has passed the most recent health check. At least one instance in the environment is available and taking requests.
     - Yellow: Environment has failed at least one health check. Some requests are failing.
     - Red: Environment has failed 3 or more health checks, and an environment resource has become unavailable. Requests are consistently failing.
 - Enhanced:
     - Green to Red: OK, Warning, Degraded, Severe (respectively)
     - Grey to White: Pending, Unknown, Suspended (respectively)