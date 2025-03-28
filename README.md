# Cloudmart IT Modernization Project

**Project Overview**


CloudMart, a leading e-commerce company, is facing growing challenges with IT inefficiencies and rising customer support costs. The company is losing its competitive edge to Klarna, which offers similar products at lower prices while leveraging modern cloud infrastructure and AI-driven automation.
To regain its market position, CloudMart’s CTO has initiated a digital transformation project aimed at rearchitecting and migrating its application to a modern cloud-based infrastructure. This initiative integrates MultiCloud, DevOps, and AI automation to enhance IT efficiency, scalability, and customer experience.

As part of this transformation, we are participating in a 5-day hands-on challenge to deploy CloudMart’s IT infrastructure using modern cloud and DevOps practices. 

![Screenshot 2025-02-25 120721](https://github.com/user-attachments/assets/e77bba2c-a6d1-44c6-a262-87a1b7f9cb0e)

![_- visual selection (2)](https://github.com/user-attachments/assets/03221002-30aa-4c18-9005-bf1a02a94bdc)


**Day 1 - AWS Setup**

On Day 1, I worked on setting up Terraform using Claude as an AI assistant. I created an S3 bucket and DynamoDB tables, launched an EC2 instance, and configured IAM roles for managing AWS resources.

**Resources Used**:
AWS Services: S3, EC2, IAM, DynamoDB
Tools & Technologies: Terraform, AWS CLI, Claude AI

**Steps Performed**:
1. Used Claude AI to Generate Terraform Code : Generated Terraform code for an S3 bucket
2. Created an IAM Role for EC2 : Created an IAM role named EC2Admin with AdministratorAccess attached.
3. Launched an EC2 Instance :
     + Used Amazon Linux 2 AMI
     + Attached the EC2Admin IAM role
     + Enabled SSH access
5. Installed Terraform on EC2 Instance
6. Created and Applied Terraform Configuration
7. Created DynamoDB Tables for CloudMart

![Screenshot 2025-02-26 145233](https://github.com/user-attachments/assets/ec6c8e7e-ed83-4f31-9483-d73a7af86f0c)


Set up Terraform, launched an EC2 instance, installed Terraform, and created AWS resources (S3, DynamoDB). 

Day 1 was focused on infrastructure automation using Terraform and AI-driven assistance.




**DAY 2 - Docker & Kubernetes Implementation**

**Part 1: Docker Setup on EC2**

I worked on setting up Docker and running containerized applications for CloudMart.

✅ Installed Docker on EC2 Instance

✅ Created Docker Images for CloudMart Backend & Frontend

**Backend**:
+ Downloaded backend source code.
+ Created .env file with API keys & configurations.
+ Wrote a Dockerfile for building the backend container.
+ Built and tested the container.

**Frontend**:
+ Downloaded frontend source code.
+ Created a Dockerfile for building the frontend container.
+ Built and tested the container.

**Part 2: Kubernetes Deployment on AWS EKS**

Worked on setting up a Kubernetes cluster using AWS EKS and deployed the CloudMart application.

✅ Installed Docker on EC2 Instance

✅ Created Docker Images for CloudMart Backend & Frontend

**Backend:**

+ Downloaded backend source code.
+ Created .env file with API keys & configurations.
+ Wrote a Dockerfile for building the backend container.
+ Built and tested the container.

**Frontend:**

+ Downloaded frontend source code.
+ Created a Dockerfile for building the frontend container.
+ Built and tested the container.


🛠️ **Part 2:** Kubernetes Deployment on AWS EKS
set up a Kubernetes cluster using AWS EKS and deployed the CloudMart application

+ EKS Cluster Setup : Installed eksctl and kubectl
  
+ Deployed CloudMart Backend & Frontend on Kubernetes

**Backend:**

+ Pushed Docker image to AWS ECR.
+ Created cloudmart-backend.yaml for Kubernetes deployment.
+ Applied deployment.
+ Verified pod, deployment, and service status.

**Frontend:**

+ Updated .env to point to Kubernetes backend API.
+ Pushed Docker image to AWS ECR.
+ Created cloudmart-frontend.yaml for Kubernetes deployment.
+ Applied deployment.
+ Verified service IP for frontend access.


Challenges : ⚠️ Faced issues with permissions while accessing EKS, resolved by configuring eksctl

![Screenshot 2025-03-18 194223](https://github.com/user-attachments/assets/d65adc27-ed24-4fef-afd9-29ed56fc01e8)

**DAY - 3 - CI/CD Pipelines**

1. Created and Pushed the CloudMart Application to GitHub
   
    + Initialized a new GitHub repository cloudmart-application.
    + Navigated to the frontend directory and committed the application source code.

2. Configured AWS CodePipeline for CI/CD
    + Created a new pipeline cloudmart-cicd-pipeline in AWS CodePipeline.
    + Configured the source as GitHub (cloudmart-application).
    + Set up build and deploy stages using AWS CodeBuild.

3.  Set Up AWS CodeBuild for Docker Image Build & Push
   
    + Created a build project cloudmartBuild for automated Docker image creation.

    + Configured CodeBuild with Amazon Linux 2 and Docker runtime.

    + Enabled Docker build privileges for containerized deployment.

    + Created and committed the buildspec.yml file to automate builds.

    + Successfully pushed the CloudMart Docker image to Amazon Elastic Container Registry (ECR).

4. Configured AWS CodeBuild for Kubernetes Deployment
   
    + Created a separate deployment project cloudmartDeployToProduction.

    + Installed kubectl in the build environment.

    + Updated Kubernetes cluster configuration.

    + Replaced placeholder image in cloudmart-frontend.yaml with the latest ECR image.

    + Successfully deployed the updated CloudMart application to AWS EKS.

5. Tested the CI/CD Pipeline with a Code Change
   
    + Modified MainPage/index.jsx (line 93) to update UI text.

    + Committed the changes and pushed to GitHub, triggering an automatic pipeline execution.

    + Observed pipeline execution in AWS CodePipeline.

    + Verified successful deployment using kubectl.


![Screenshot 2025-03-20 114323](https://github.com/user-attachments/assets/141c732e-5a39-456b-9e76-4139758a576e)


**Day - 4 : AI Integration**

1. Creating Resources with Terraform
   
       + Created a new IAM role and policy to allow the Lambda function to interact with DynamoDB and CloudWatch Logs. This is a prerequisite for securely running the 
         Lambda function.
   
       + Deployed a Lambda function (list_products) that lists available products from the CloudMart API. The Lambda function is now integrated with DynamoDB for product data access.

       + Configured the necessary Lambda permissions to allow Amazon Bedrock to invoke the Lambda function for product recommendations.

2. Configuring Amazon Bedrock Agent for Product Recommendations

      + Enabled access to the Claude 3 Sonnet model in Amazon Bedrock.

      + Created a Bedrock Agent called cloudmart-product-recommendation-agent to interact with users, retrieve product data, and recommend items based on their preferences.

      + Configured the IAM role for the Bedrock agent to access Lambda functions and Bedrock models, ensuring the agent can interact with the necessary services.

3. Creating and Testing OpenAI Assistant for CloudMart

     +  Created a new assistant named CloudMart Customer Support to handle general customer inquiries. The assistant is configured to assist customers with issues related to orders and platform usage.
       
     +  Environment Variables: Generated API keys for the OpenAI assistant and integrated them into the CloudMart backend configuration to enable seamless interaction with the OpenAI API.

4. Redeploying Backend with AI Assistants Integration

     + Updated the Kubernetes configuration to include environment variables for both Amazon Bedrock and OpenAI assistants.
  
     + Deployed the updated backend configuration to Kubernetes using the following command.
  
5. Testing the AI Assistant

     + Verified that the AI assistant properly engages with users, providing relevant product recommendations and handling customer support inquiries efficiently.
  
![Screenshot 2025-03-22 010845](https://github.com/user-attachments/assets/42af7f16-a049-4741-96a6-1794f735f75e)

![Screenshot 2025-03-22 010905](https://github.com/user-attachments/assets/86c31920-a75a-46c0-9bcd-8653194fe07b)










