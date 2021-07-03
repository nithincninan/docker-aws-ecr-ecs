# DOCKER > ECR > ECS

**Deploy and run Docker containers on AWS ECS**

![docker-aws-ecs-arch](https://user-images.githubusercontent.com/2525741/124363214-a09f6c00-dc57-11eb-91a6-6f1e365df8f9.png)
 ECS - Image from AWS
 
1. Prerequisites:

  * Download and install the latest version of Docker Desktop.
  
      1. Download for Mac
      2. Download for Windows
      
      * Alternatively, install the Docker Compose CLI for Linux.
        
  * Ensure you have an AWS account / AWS CLI is installed and configured
  

2. Create a repository using ECR:



3. Push docker image to ECR repo(from local)
  
  
  
  
  
About AWS services/tools:    
 
   **AWS ECS:**  Amazon Elastic Container Service (Amazon ECS) is a container orchestration/management service similar to Kubernetes, Docker Swarm, etc. 
 It’s a highly scalable and high-performance service that comes with Docker pre-installed. 
 It allows applications/containers to run on top of EC2 hosts.
 
   **AWS ECR:** Similar to the Docker hub, Amazon has a feature called Elastic Container Register, which allows you to deploy your Docker container to AWS. 
 
