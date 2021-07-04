# DOCKER --> ECR --> ECS

**Deploy and run Docker containers on AWS ECS**:

![docker-aws-ecs-arch](https://user-images.githubusercontent.com/2525741/124363214-a09f6c00-dc57-11eb-91a6-6f1e365df8f9.png)

**Prerequisites:**

  * Download and install the latest version of Docker Desktop.
  
      1. Download for Mac
      2. Download for Windows
      
      * Alternatively, install the Docker Compose CLI for Linux.
        
  * Ensure you have an AWS account / AWS CLI is installed and configured

**Step 1. Create a repository using ECR(Elastic Container Repository):**
    
    1.1 Click on Repository (Create Repository)
    
    1.2 Repository name: docker-nginx-welcome-image
    
    Note: make sure aws cli/configure is installed in OS (mac/windows/linux). If not go below:
                   
       * MAC: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-mac.html
       * Windows: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html
       
       * verify aws-cli installed: aws --version
       
       * Run command: aws configure
       
       * configure access key ID and secret access key in Identity and Access Management (IAM) > Access keys:
        
         - https://console.aws.amazon.com/iam/home?#/security_credentials
         
         eg: - aws configure
               AWS Access Key ID [None]: XXXXXXXX
               AWS Secret Access Key [None]: XXXXXXXXXXXXXXXXXXXX
               Default region name [None]: ap-south-1
               Default output format [None]: json
                  
    
**Step 2. Push docker image to ECR repo(from local):**
  
   2.1 Click ( view push commands ) :
        
   * Push commands for docker-nginx-welcome-image
   
       ![aws-push](https://user-images.githubusercontent.com/2525741/124391731-a0fb3e00-dd0f-11eb-9719-9f7eba7d8f6e.png)
         
               
   2.2 Images has been pushed to the ECR repo.
              
   <img width="1076" alt="pushed-image" src="https://user-images.githubusercontent.com/2525741/124391746-b1abb400-dd0f-11eb-90af-d9a1917e2dd8.png">


**Step 3. Create a ACS Elastic Cluster Service**

    


  
**About AWS services/tools:**    
 
   **AWS ECS:**  Amazon Elastic Container Service (Amazon ECS) is a container orchestration/management service similar to Kubernetes, Docker Swarm, etc. 
 It’s a highly scalable and high-performance service that comes with Docker pre-installed. 
 It allows applications/containers to run on top of EC2 hosts.
 
   **AWS ECR:** Similar to the Docker hub, Amazon has a feature called Elastic Container Register, which allows you to deploy your Docker container to AWS. 
 
