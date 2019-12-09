# ECS scalable cluster

## Overview

The repository contains three Jenkins pipelines for building and deploying a containerized Petclinic application to a scalable AWS ECS cluster.

The project structure is as described below:
* **Job 1/** folder contains a Jenkinsfile for the first job that runs tests, builds the project, bakes a Docker image and uploads it to an ECR repository. Tags with version numbers are pushed both to ECR and to the Git repo. A Dockerfile for the Petclinic app is included.

* **Job 3/** contains a Jenkinsfile and Cloudformation templates used to create a simple scalable infrastructure out of nested stacks. See the diagram below.
To use nested stacks, make sure to update the S3 bucket in the Jenkinsfile:
'''
    environment {
        stack_name= '*your-stack-name*'
        s3_bucket = 's3://*path-to-your-s3-bucket*'
    }
'''

* **Job 2/** The last job allows you to deploy a specific version of the application to the existing stack. You can select a specific version from the drop-down list in Jenkins.
> *Note:* The initial task definition created in Job 3 uses a dummy Nginx image on port 80.