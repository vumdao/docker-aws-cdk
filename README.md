<p align="center">
  <a href="https://dev.to/vumdao">
    <img alt="Create AWS-CDK image container" src="https://dev-to-uploads.s3.amazonaws.com/i/45ftdv41mae8bagj90wn.png" width="160" />
  </a>
</p>
<h1 align="center">
  Create AWS-CDK image container
</h1>

<h3 align="center">
  ⚛️ 📄 🚀
</h3>
<h3 align="center">
  All CDK developers need to install Node.js 10.3.0 or later, even those working in languages other than TypeScript or JavaScript such as python
</h3>
<p align="center">
  <b>Important</b>: Node.js versions 13.0.0 through 13.6.0 are not compatible with the AWS CDK.
</p>


## Create AWS-CDK image container from amazon/aws-lambda-python (or any python base images) and install nodejs 12

## What’s In This Document 
- [Dockerfile](#-Dockerfile)
- [Build and Test container image](#-Build-and-Test-container-image)


### 🚀 **Dockerfile**
- Base image: `amazon/aws-lambda-python:3.8`
- Install nodejs 12 and aws-cdk version 1.73.0
- Install some cdk libaries
```
FROM amazon/aws-lambda-python:3.8

ENV AWS_CDK_VERSION=1.73.0
ENV AWS_DEFAULT_REGION=ap-northeast-2

WORKDIR /opt/stack

RUN yum -y update && \
    curl -sL https://rpm.nodesource.com/setup_12.x | bash - && \
    yum list available nodejs && \
    yum install -y python3-pip && \
    yum install -y nodejs && \
    npm install -g aws-cdk@${AWS_CDK_VERSION} && \
    pip3 install aws-cdk.aws-ec2 aws-cdk.aws-route53 aws-cdk.aws-iam aws-cdk.aws-elasticloadbalancingv2 aws-cdk.core

CMD ["cdk version"]
```

### 🚀 **Build and Test container image**
```
⚡ $ docker build -t awscdk .
⚡ $ docker run -d --name test -it awscdk
30d272c6ad8abaa4162fdc090d81d0641d287f4ae161606bcc365da6ffe2284e
⚡ $ docker exec test cdk version
1.73.0 (build eb6f3a9)
⚡ $ docker exec test node --version
v12.20.0
⚡ $ docker exec test npm --version
6.14.8
⚡ $ docker exec test cdk init -l python
Applying project template app for python

# Welcome to your CDK Python project!

This is a blank project for Python development with CDK.

The `cdk.json` file tells the CDK Toolkit how to execute your app.

This project is set up like a standard Python project.  The initialization
process also creates a virtualenv within this project, stored under the `.venv`
directory.  To create the virtualenv it assumes that there is a `python3`
(or `python` for Windows) executable in your path with access to the `venv`
package. If for any reason the automatic creation of the virtualenv fails,
you can create the virtualenv manually.

To manually create a virtualenv on MacOS and Linux:

Enjoy!

Initializing a new git repository...
/bin/sh: git: command not found
Unable to initialize git repository for your project.
Please run 'python3 -m venv .venv'!
Executing Creating virtualenv...
✅ All done!

⚡ $ docker exec -it test ls
app.py  cdk.json  README.md  requirements.txt  setup.py  source.bat  stack

⚡ $ docker exec -it test ls stack
__init__.py  stack_stack.py
```

**Read More**
- [Pelican-resume with docker-compose and AWS + CDK](https://dev.to/vumdao/pelican-resume-with-docker-compose-and-aws-cdk-33e5)
- [Using Helm Install Botkube Integrate With Slack On EKS](https://dev.to/vumdao/using-helm-install-botkube-integrate-with-slack-on-eks-gmn)
- [Ansible AWS EC2 Dynamic Inventory Plugin](https://dev.to/vumdao/ansible-aws-ec2-dynamic-inventory-plugin-3bme)
- [How To List All Enabled Regions Within An AWS account](https://dev.to/vumdao/list-all-enabled-regions-within-an-aws-account-4oo7)
- [Using AWS KMS In AWS Lambda](https://dev.to/vumdao/using-aws-kms-in-aws-lambda-2jm2)
- [Create AWS Backup Plan](https://dev.to/vumdao/create-aws-backup-plan-a0f)
- [Techniques For Writing Least Privilege IAM Policies](https://dev.to/vumdao/techniques-for-writing-least-privilege-iam-policies-4fc7)
- [EKS Persistent Storage With EFS Amazon Service](https://dev.to/vumdao/eks-persistent-storage-with-efs-amazon-service-14ei)
- [Create k8s Cronjob To Schedule Delete Expired Files](https://dev.to/vumdao/create-k8s-cronjob-to-schedule-delete-expired-files-1i41)
- [Amazon ECR - Lifecycle Policy Rules](https://dev.to/vumdao/amazon-ecr-lifecycle-policy-rules-1l59)
- [Connect Postgres Database Using Lambda Function](https://dev.to/vumdao/connect-postgres-database-using-lambda-function-1mca)
- [Using SourceIp in ALB Listener Rule](https://dev.to/vumdao/using-sourceip-in-alb-listener-rule-377b)
- [Amazon Simple Systems Manager (SSM)](https://dev.to/vumdao/amazon-simple-systems-manager-ssm-2pb0)
- [Invalidation AWS CDN Using Boto3](https://dev.to/vumdao/invalidation-aws-cdn-using-boto3-2k9g)
- [Create AWS Lambda Function Triggered By S3 Notification Event](https://dev.to/vumdao/create-aws-lambda-function-triggered-by-s3-notification-event-9p0)
- [CI/CD Of Invalidation AWS CDN Using Gitlab Pipeline](https://dev.to/vumdao/ci-cd-of-invalidation-aws-cdn-using-gitlab-pipeline-34op)
- [Create CodeDeploy](https://dev.to/vumdao/create-codedeploy-4425)
- [Gitlab Pipeline With AWS Codedeploy](https://dev.to/vumdao/gitlab-pipeline-with-aws-codedeploy-30cl)


<h3 align="center">
  <a href="https://dev.to/vumdao">:stars: Blog</a>
  <span> · </span>
  <a href="https://vumdao.hashnode.dev/">Web</a>
  <span> · </span>
  <a href="https://www.linkedin.com/in/vu-dao-9280ab43/">Linkedin</a>
  <span> · </span>
  <a href="https://www.linkedin.com/groups/12488649/">Group</a>
  <span> · </span>
  <a href="https://www.facebook.com/CloudOpz-104917804863956">Page</a>
  <span> · </span>
  <a href="https://twitter.com/VuDao81124667">Twitter :stars:</a>
</h3>
