# Node.js ECR Deployment Demo

## Prerequisites

- GitHub Account
- AWS Account
- AWS CLI configured
- Docker installed

## Setup Instructions

1. **Create ECR Repository**

   - Go to Amazon ECR in AWS Console
   - Create a new repository named `your-fullname-nodejs-app`

2. **GitHub Secrets Configuration**
   In your GitHub repository settings:

   - Go to Settings > Secrets and Variables > Actions
   - Add two secrets:
     - `AWS_ACCESS_KEY_ID`: Your AWS IAM user access key
     - `AWS_SECRET_ACCESS_KEY`: Your AWS IAM user secret key

3. **IAM Permissions**
   Ensure your AWS IAM user has the following ECR permissions:
   - `ecr:GetDownloadUrlForLayer`
   - `ecr:BatchGetImage`
   - `ecr:BatchCheckLayerAvailability`
   - `ecr:PutImage`
   - `ecr:InitiateLayerUpload`
   - `ecr:UploadLayerPart`
   - `ecr:CompleteLayerUpload`

## Workflow Explanation

The GitHub Actions workflow does the following:

1. Triggers on push to main branch
2. Checks out the code
3. Configures AWS credentials
4. Logs in to Amazon ECR
5. Builds Docker image
6. Tags image with commit SHA
7. Pushes image to ECR repository

## Docker Build

To build docker image, run the following command:

````bash
docker build -t mydocker .

To run the docker image, run the following command:

```bash
docker run -p 5000:5000 mydocker

## Local Development

```bash
# Install dependencies
npm install

# Run the application
npm start
````
