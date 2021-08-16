# CloudFormation - This is a collection of resources to help train on CloudFormation

CFN_Tutorials:



CFN_Primitives:
cloudformation-primitives
==================================
## Description

AWS best practice dictates the use of nested CloudFormation stacks wherever possible. The CloudFormation templates included here constitute reusable resource primitives which can be called as many times as desired from a root CloudFormation template.

AWS Cloudformation Documentation for nested stacks:

https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-nested-stacks.html

## Usage

Per AWS docs, these primitives must be referenced via an S3 URL by the root/parent stacks:

The URL of a template that specifies the stack that you want to create as a resource. Template files can use any extension, such as .json, .yaml, .template, or .txt. The template must be stored on an Amazon S3 bucket, so the URL must have the form: https://s3.amazonaws.com/.../TemplateName.extension

## Parent Examples

The parent template examples use the NestedTemplateBaseUrl parameter to set the S3 bucket/prefix where the nested template primitives can be called from by the parent. Set this parameter to a bucket/prefix which you have read access to and store the primitives there.

The parent_ec2_vpc.yaml template is an example parent template using nested CloudFormation primitives to create a complete set of resources necessary for a functional VPC, including the VPC itself, IGW, public and private subnets, Route Tables, DHCP Option set, etc. In this case, the parent template assumes three AZs with one public and one private subnet in each.

The parent opsworks-cm.yaml template is an example parent template using nested CloudFormation primitives to create a complete set of resources necessary for an OpsWorks for Chef Automate deployment.

Note: there is currently an issue with setting a custom PivotalKey parameter. OpsWorks for Chef Automate doesn't currently allow you to download a starter kit with that custom pivotal key during the resource creation process. This appears to be a bug in the OpsWorks console when an opsworks-cm resource is created with CloudFormation, which never activates a starter kit download link while the server resource is created. You will have to use the OpsWorks for Chef Automate console to regenerate a new starter kit after the opsworks-cm server resource creation finishes. A custom PivotalKey should still be generated and passed into the PivotalKey parameter for the purpose of maintaining consistency with the eventual intended functionality.

Author: Allan Webb

Email: awebb@witsolutions.com



cli-cfn:
# aws-cli-cfn
Explorations in IaC on AWS

# CloudFormation (CFN) build files are *.yaml.  This has the script that CFN uses to build resources
# AWS CLI commands are included in the *cli file(s) as examples to help get you started.



aws-vpc-cfn:
# AWS_VPC_CFN_basic
CloudFormation Basic AWS VPC with 2 public, 2 private subnets and 2 NATs.
