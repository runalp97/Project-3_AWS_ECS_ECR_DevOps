🚀 AWS ECS + ECR DevOps Pipeline — Infrastructure Automation Project

📌 Project Description

This project demonstrates a complete DevOps workflow for containerizing an application, pushing the Docker image to Amazon ECR, and deploying it to Amazon ECS using an automated CI/CD pipeline built with CodeBuild and CodePipeline.

The project was built in two phases:

🔘 Manual Mode

- Create ECR repository

- Build and push Docker image

- Create ECS Cluster, Task Definition, and Service

- Run the container manually on ECS

🔘 Automated Mode

- GitHub used as source repo

- CI/CD using CodeBuild + CodePipeline

- Artifacts stored in S3

- ECR used as container registry

- ECS Service auto-deploys new versions

🏗 Architecture Overview (Text-Based)
GitHub (Source Code)
      ↓
AWS CodePipeline
      ↓
AWS CodeBuild (Build Docker Image)
      ↓
Amazon ECR (Push Image)
      ↓
Amazon S3 (Store Artifacts)
      ↓
Amazon ECS (Cluster + Service + Task Definition)
      ↓
EC2 Launch Type Task (Runs Container)
      ↓
Application Accessible via Public IP

⭐ Key Contributions

Containerized application using Docker

Created & managed ECR repository

Designed ECS infrastructure (Cluster, Task Definition, Service)

Built automated CI/CD pipeline using CodeBuild + CodePipeline

Managed artifact storage via S3

Integrated GitHub triggers for continuous deployment

Verified live deployment on ECS and monitored logs

🧰 Tech Stack
Category	Tools
Source Control	GitHub
CI/CD	AWS CodePipeline, CodeBuild
Compute	Amazon ECS (EC2 launch type)
Container Registry	Amazon ECR
Storage	S3
Other Services	IAM Roles, CloudWatch Logs
🔹 Part A — Manual Deployment Workflow (Summary)
1. Create ECR Repository

Created a new ECR repo to store Docker images.

2. Create Docker Image and Push to ECR

Downloaded sample code to EC2

Built image

Tagged and pushed to ECR using push commands

Verified image in repository

3. Create ECS Cluster

Created ECS cluster with default settings.

4. Create Task Definition

Provided container name

Added image URI from ECR

Exposed required port

5. Create ECS Service

Connected task definition to ECS cluster

Service launched 1 running task

Verified application working from the external link

🔹 Part B — Automated CI/CD Pipeline (GitHub → ECS)
1. S3 Bucket for Artifacts

Created an S3 bucket to store build artifacts from CodeBuild.

2. CodeBuild Project

Configured with:

Source: GitHub

Privileged mode enabled (to build Docker images)

Environment variables:

IMAGE_REPO_NAME

AWS_ACCOUNT_ID

CONTAINER_IMAGE

Artifacts output to S3

3. Update CodeBuild Role

Added permissions for ECR push/pull actions.

4. CodePipeline Setup

Pipeline stages:

Source: GitHub

Build: CodeBuild builds Docker image → pushes to ECR

Deploy: ECS deploys updated task definition and service

5. End-to-End Verification

Modified the application code in GitHub

Pushed changes

Pipeline triggered automatically

New Docker image built → pushed → deployed

Application updated in ECS

🟩 How to Run the Project (No Commands — Only Instructions)
1️⃣ Prepare the Repository

Download or clone the GitHub repository to your machine and review the application code and Dockerfile.

2️⃣ Make a Small Application Change

Modify the application file (ex: app.py) so the pipeline can detect an update.

3️⃣ Commit & Push the Changes

Push your updated code to the same GitHub branch linked to CodePipeline.

4️⃣ Pipeline Automatically Starts

Go to AWS CodePipeline and observe:

Source stage fetches new code

Build stage creates Docker image and pushes to ECR

Deploy stage updates the ECS service

All stages should turn green.

5️⃣ Verify the ECS Deployment

Open ECS console → Cluster → Service → Tasks → Public IP/External Link.

Confirm the new version of your application is running.

6️⃣ Validate the Pipeline Flow

Ensure the following:

ECR has a new image with a new tag

ECS service deployed a new task revision

Application updates appear in browser

CodeBuild logs show successful build

S3 bucket contains build artifacts

🖼 Screenshots You Should Add

Add these screenshots inside /screenshots folder or inline in the README using GitHub image markdown.

Recommended:

📸 Manual Mode

ECR repo showing the pushed image

ECS cluster

ECS task definition

ECS service running

Application web output

📸 Automated Mode

CodeBuild successful build logs

CodePipeline showing all green stages

ECR image pushed by pipeline

ECS service showing deployment event

Browser output of updated application

📌 Closing Notes

This project demonstrates both manual and automated deployment pipelines on AWS ECS, covering real industry practices like containerization, ECR storage, ECS orchestration, and CI/CD automation.

If you want, I can also create:

✅ A short LinkedIn post
✅ Portfolio description
✅ Resume bullet points for this project
✅ Architecture diagram (image)

Just tell me!
