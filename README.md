**GitHub Links with Explanation:**

1. [Terraform_vpc](https://github.com/venispatel453/Terraform_vpc)
   - This repository contains Terraform code for provisioning Virtual Private Cloud (VPC) resources on AWS. It includes configurations for subnets, route tables, internet gateways, and other networking components.

2. [Terraform_Instance](https://github.com/venispatel453/Terraform_Instance)
   - The Terraform code in this repository focuses on provisioning EC2 instances on AWS. It covers instance types, security groups, key pairs, and other instance-related configurations.

3. [Terraform_asg](https://github.com/venispatel453/Terraform_asg)
   - This repository contains Terraform configurations for creating Auto Scaling Groups (ASG) on AWS. It includes settings for launch configurations, scaling policies, and load balancer integration.

4. [Terraform_ecs](https://github.com/venispatel453/Terraform_ecs)
   - The Terraform code in this repository is dedicated to provisioning resources for Amazon ECS (Elastic Container Service). It covers task definitions, services, clusters, and other ECS-related configurations.

5. [Terraform_alb](https://github.com/venispatel453/Terraform_alb)
   - This repository focuses on Terraform code for provisioning Application Load Balancers (ALB) on AWS. It includes listener rules, target groups, and other configurations related to ALB setup.

These repositories contain infrastructure as code (IaC) configurations using Terraform, enabling automated provisioning and management of AWS resources. They demonstrate best practices for infrastructure automation and can serve as valuable learning resources for Terraform practitioners.



# Deploy to Amazon ECS Workflow

This GitHub Actions workflow automates the deployment process to Amazon ECS (Elastic Container Service) for a project consisting of frontend and backend services. When changes are pushed to the main branch, this workflow triggers and deploys the updated Docker container images to ECS.

## Workflow Overview

### Trigger
- **Event:** Push to Main Branch
- **Branches:** Only deploys when changes are pushed to the main branch.

### Environment Variables
- `AWS_REGION`: The AWS region where ECS is located (e.g., `ap-south-1`).
- `ECS_SERVICE_FRONTEND`: Name of the ECS service for the frontend.
- `ECS_SERVICE_BACKEND`: Name of the ECS service for the backend.
- `ECS_CLUSTER`: Name of the ECS cluster where the services will be deployed.
- `CONTAINER_NAME_FRONTEND`: Name of the frontend container.
- `CONTAINER_NAME_BACKEND`: Name of the backend container.

### Jobs
1. **Deploy:**
   - **Name:** Deploy
   - **Runs on:** Ubuntu latest
   - **Environment:** Production

### Steps
1. **Checkout:** Checks out the repository's code.
   
2. **Configure AWS Credentials:**
   - Configures AWS credentials using the AWS Actions toolkit. It uses the provided access key ID and secret access key stored in GitHub secrets.

3. **Login to Amazon ECR:**
   - Logs in to Amazon ECR (Elastic Container Registry) to authenticate Docker pushes.

4. **Build and Push Backend Image to ECR:**
   - Builds the Docker image for the backend service and pushes it to Amazon ECR.

5. **Build and Push Frontend Image to ECR:**
   - Builds the Docker image for the frontend service and pushes it to Amazon ECR.

6. **Fill in Backend Image ID in Task Definition:**
   - Updates the ECS task definition with the new backend Docker image ID.

7. **Fill in Frontend Image ID in Task Definition:**
   - Updates the ECS task definition with the new frontend Docker image ID.

8. **Deploy ECS Task Definitions for Frontend:**
   - Deploys the updated task definition for the frontend service to ECS.

9. **Deploy ECS Task Definitions for Backend:**
   - Deploys the updated task definition for the backend service to ECS.

### Outputs
- None

## How to Use
1. Ensure AWS credentials are stored securely in GitHub secrets with appropriate permissions for ECS and ECR.
2. Modify the `backend-task-definition.json` and `frontend-task-definition.json` files according to your ECS task definitions.
3. Adjust the Dockerfile paths in the workflow to match the directory structure of your project.
4. Customize environment variables and service names as per your project requirements.
5. Commit and push changes to the main branch to trigger the deployment workflow.

## Additional Notes
- This workflow assumes the presence of Dockerfiles for both frontend and backend services.
- Ensure Dockerfiles are set up correctly to build the desired Docker images.
- The ECS task definitions must be properly configured with the correct container definitions and image repositories.
- Make sure the ECS cluster specified in the workflow exists in the specified AWS region.

**Disclaimer:** Use this workflow with caution and ensure proper testing in a staging environment before deploying to production.
