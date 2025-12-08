**🚀 AWS ECS + ECR DevOps Pipeline — Infrastructure Automation Project**

**📌 Project Description**

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
  

**🏗 Architecture Overview:**

<img width="591" height="436" alt="image" src="https://github.com/user-attachments/assets/941b25ad-0a71-4574-b597-314b84c917f9" />


**⭐ Key Contributions:**

 🔹 Containerized application using Docker.

 🔹 Created & managed ECR repository.

 🔹 Designed ECS infrastructure (Cluster, Task Definition, Service).

 🔹 Built automated CI/CD pipeline using CodeBuild + CodePipeline.

 🔹 Managed artifact storage via S3.

 🔹 Integrated GitHub triggers for continuous deployment.

 🔹 Verified live deployment on ECS and monitored logs.

**🧰 Tech Stack:**

 🔹 Source Control- GitHub

 🔹 CI/CD-	AWS CodePipeline, CodeBuild

 🔹 Compute- Amazon ECS (EC2 launch type)

 🔹 Container Registry-	 Amazon ECR

 🔹 Storage- S3

 🔹 Other Services- IAM Roles, CloudWatch Logs

**Part A — Manual Deployment Workflow (Summary):**

1. Create ECR Repository:

- Created a new ECR repo to store Docker images.

2. Create Docker Image and Push to ECR:

- Downloaded sample code to EC2

- Built image

- Tagged and pushed to ECR using push commands

- Verified image in repository

3. Create ECS Cluster:

Created ECS cluster with default settings.

4. Create Task Definition:

- Provided container name

- Added image URI from ECR

- Exposed required port

5. Create ECS Service:

- Connected task definition to ECS cluster

- Service launched 1 running task

- Verified application working from the external link

**🔹 Part B — Automated CI/CD Pipeline (GitHub → ECS): **

1. S3 Bucket for Artifacts

- Created an S3 bucket to store build artifacts from CodeBuild.

2. CodeBuild Project

Configured with:

- Source: GitHub

- Privileged mode enabled (to build Docker images)

- Environment variables:

      - IMAGE_REPO_NAME

      - AWS_ACCOUNT_ID

      - CONTAINER_IMAGE

- Artifacts output to S3

3. Update CodeBuild Role

- Added permissions for ECR push/pull actions.

4. CodePipeline Setup

- Pipeline stages:

      - Source: GitHub
      
      - Build: CodeBuild builds Docker image → pushes to ECR
      
      - Deploy: ECS deploys updated task definition and service

5. End-to-End Verification

- Modified the application code in GitHub

- Pushed changes

- Pipeline triggered automatically

- New Docker image built → pushed → deployed

- Application updated in ECS


**🟩 How to Run the Project:**

1️⃣ Prepare the Repository

- Download or clone the GitHub repository to your machine and review the application code and Dockerfile.

2️⃣ Make a Small Application Change

- Modify the application file (ex: app.py) so the pipeline can detect an update.

3️⃣ Commit & Push the Changes

- Push your updated code to the same GitHub branch linked to CodePipeline.

4️⃣ Pipeline Automatically Starts

Go to AWS CodePipeline and observe:

- Source stage fetches new code

- Build stage creates Docker image and pushes to ECR

- Deploy stage updates the ECS service

All stages should turn green.

5️⃣ Verify the ECS Deployment

- Open ECS console → Cluster → Service → Tasks → Public IP/External Link.

- Confirm the new version of your application is running.

6️⃣ Validate the Pipeline Flow

Ensure the following:

- ECR has a new image with a new tag

- ECS service deployed a new task revision

- Application updates appear in browser

- CodeBuild logs show successful build

- S3 bucket contains build artifacts

**🖼 Screenshots :**


📸 Manual Mode:

 🔹 ECR repo showing the pushed image ⬇️

 <img width="940" height="209" alt="image" src="https://github.com/user-attachments/assets/45ef5602-c3c4-40f4-9f89-ebbc33b8ee23" />
 

 <img width="940" height="294" alt="image" src="https://github.com/user-attachments/assets/6437271a-68d5-4c98-977b-2f1059923518" />


 🔹 ECS cluster ⬇️
 
 <img width="940" height="303" alt="image" src="https://github.com/user-attachments/assets/021b5228-dac2-41b4-9b19-8f66e4041529" />

 
 🔹 ECS task definition ⬇️

 <img width="940" height="459" alt="image" src="https://github.com/user-attachments/assets/53f0b6ed-973a-410e-bbe3-8445ca76cea7" />

 
 🔹 ECS service running ⬇️
 
 <img width="940" height="455" alt="image" src="https://github.com/user-attachments/assets/93f3248a-3d6a-4c49-b4e3-36278619608a" />


 🔹 Application web output ⬇️

 <img width="940" height="390" alt="image" src="https://github.com/user-attachments/assets/8aadbc19-73a9-419f-9f6c-c4b32748e1be" />


**📸 Automated Mode:**

🔹 CodeBuild successful build logs ⬇️

<img width="940" height="450" alt="image" src="https://github.com/user-attachments/assets/74911639-884b-4307-9190-f01b2ea687f1" />

🔹 CodePipeline showing all green stages ⬇️

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/5ca5c5db-655e-40ea-bc0a-b7fb9527be45" />

🔹 ECR image pushed by pipeline ⬇️

<img width="940" height="453" alt="image" src="https://github.com/user-attachments/assets/6daa1193-9129-4679-b77c-05064f5176ca" />


🔹 ECS service ⬇️

<img width="940" height="453" alt="image" src="https://github.com/user-attachments/assets/cc6e51be-eed1-4b44-b382-3a160838904c" />

🔹 Browser output of updated application 3rd change pushed ⬇️

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/ae8ed13b-faf1-494d-9aa8-1f8a94e7cacc" />


**📌 Closing Notes:**

This project demonstrates both manual and automated deployment pipelines on AWS ECS, covering real industry practices like containerization, ECR storage, ECS orchestration, and CI/CD automation.

