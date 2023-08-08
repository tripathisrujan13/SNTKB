---
id: stwnwuzxtke0ir6kuvig1wx
title: SAM
desc: ''
updated: 1691525178105
created: 1691517169008
---

## AWS Serverless Application Model (SAM)

### Uses
An open source framework for building serverless applications in #AWS. Serverless resources can be deployed using YAML templates.

### Commands
 - `sam build`: Builds application locally and transforms YAML template to [[CloudFormation|AWS.CloudFormation]] template.
 - `sam package`: Uploads [[CloudFormation|AWS.CloudFormation]] template and code to [[S3|AWS.S3]]. 
 - `sam deploy`: Creates and executes a [[CloudFormation|AWS.CloudFormation]] change set, allowing the application to be deployed.