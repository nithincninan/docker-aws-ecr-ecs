# DOCKER >> ECR >> ECS

**Deploy and run Docker containers on AWS ECS**:



**ECS - Image from AWS**
![docker-aws-ecs-arch](https://user-images.githubusercontent.com/2525741/124363214-a09f6c00-dc57-11eb-91a6-6f1e365df8f9.png)

 
1. Prerequisites:

  * Download and install the latest version of Docker Desktop.
  
      1. Download for Mac
      2. Download for Windows
      
      * Alternatively, install the Docker Compose CLI for Linux.
        
  * Ensure you have an AWS account / AWS CLI is installed and configured
  
  

2. Create a repository using ECR(Elastic Container Repository):
    
    1. Click on Repository (Create Repository)
    
    2. Repository name: docker-nginx-welcome-image
    
    3. Click view push commands :
     
           * Push commands for docker-nginx-welcome-image
           
           
           
           Note: make sure aws cli/configure is installed in OS (mac/windows/linux). If not go below:
           
           * MAC: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-mac.html
           * Windows: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html
           
           * verify aws-clis installed: aws --version
           
           * Run command: aws configure
           
           * configure access key ID and secret access key in Identity and Access Management (IAM) > Access keys:
            
             - https://console.aws.amazon.com/iam/home?#/security_credentials
             
             eg: - aws configure
                   AWS Access Key ID [None]: XXXXXXXX
                   AWS Secret Access Key [None]: XXXXXXXXXXXXXXXXXXXX
                   Default region name [None]: ap-south-1
                   Default output format [None]: json
          
    4. Images has been pushed to the ECR repo.
          

3. Push docker image to ECR repo(from local):
  
  
  
  
  
About AWS services/tools:    
 
   **AWS ECS:**  Amazon Elastic Container Service (Amazon ECS) is a container orchestration/management service similar to Kubernetes, Docker Swarm, etc. 
 It’s a highly scalable and high-performance service that comes with Docker pre-installed. 
 It allows applications/containers to run on top of EC2 hosts.
 
   **AWS ECR:** Similar to the Docker hub, Amazon has a feature called Elastic Container Register, which allows you to deploy your Docker container to AWS. 
 
