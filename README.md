# DOCKER ( Nginx ) -> ECR -> ECS

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

   3.1 Create cluster:
   ```
        * select cluster template > EC2 linux + networking
   ```
   <img width="1149" alt="create-cluster" src="https://user-images.githubusercontent.com/2525741/124395869-343e6e80-dd24-11eb-9857-c6f1f3cd72f0.png">

   ```      
        * configure cluster 
            1. configure name: docker-nginx-welcome-image
            2. Provisioning Model : On-Demand Instance
            3. ec2 Intance type: t2.micro
            4. No: of instance: 1
            5. Key pair: Create new (docker-nginx-welcome-ecs)
            6. EBS Volme size: 30
        * networking: 
            1. Security group inbound rules: 0.0.0.0/0
                 (determines the trafic that can reach your instance)
            2. Port range : 80
         * click "Create cluster" button.
  ```         
   ![cluster-configure](https://user-images.githubusercontent.com/2525741/124395888-4ae4c580-dd24-11eb-8e55-2799a1c88a7c.png)
                     
   3.2 View Cluster:
   
   <img width="693" alt="Task-done" src="https://user-images.githubusercontent.com/2525741/124395951-a020d700-dd24-11eb-9245-05641966d87a.png">


**Step 4. Task Definition**
    
   4.1 click on “Task Definition”.
   
   4.2 Create new Task Definition 
   
   ```
      > Choose EC2
   ```
   
   ![create-new-task](https://user-images.githubusercontent.com/2525741/124397125-a6ff1800-dd2b-11eb-9035-2447fcb383d5.png)
   
   ```
      * Configure Task:
            1. Task Definition Name: docker-nginx-welcome-image-task
            2. Task size: 
                * Task memory (MiB) : 512
                * Task CPU (unit) : 512
            3. Add Container
   ```
   ![configure-task-and-container-image](https://user-images.githubusercontent.com/2525741/124397170-f9403900-dd2b-11eb-925b-23e3f58ce592.png)
   
   <img width="1091" alt="add-container" src="https://user-images.githubusercontent.com/2525741/124397135-bd0cd880-dd2b-11eb-80e6-7e625811d0ce.png">
   
   4.3 Task: create service
   
   <img width="630" alt="create-service" src="https://user-images.githubusercontent.com/2525741/124397147-d0b83f00-dd2b-11eb-9dbe-bcaa946841b7.png">
   
   ```
      * Launch Type: EC2
      * Number of tasks: 1  
      
      * Review > Create Service
   ``` 
   
   <img width="869" alt="configure-service" src="https://user-images.githubusercontent.com/2525741/124397155-d57cf300-dd2b-11eb-92d9-bbb6f1438f10.png">

  
**About AWS services/tools:**    
 
   **AWS ECS:**  Amazon Elastic Container Service (Amazon ECS) is a container orchestration/management service similar to Kubernetes, Docker Swarm, etc. 
 It’s a highly scalable and high-performance service that comes with Docker pre-installed. 
 It allows applications/containers to run on top of EC2 hosts.
 
   **AWS ECR:** Similar to the Docker hub, Amazon has a feature called Elastic Container Register, which allows you to deploy your Docker container to AWS. 
   
   **Refer:** 
        
        * https://aws.amazon.com/getting-started/hands-on/deploy-docker-containers/
 
