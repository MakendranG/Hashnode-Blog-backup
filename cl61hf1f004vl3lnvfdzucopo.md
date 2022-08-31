## AWS DevOps Tools


These tools automate manual tasks, help teams manage complex, large-scale environments, and empower engineers with high-speed control  enabled by DevOps. 

## 1. Continuous Integration and Continuous Delivery 

AWS developer tools help you securely host and version your application source code, and automatically build, test, and deploy your applications to AWS or your on-premises environment. 
 
  

### 1.1. Software release process 


**AWS CodePipeline**


- It is a `CI & CD` service for fast and reliable application and infrastructure updates. 
- CodePipeline builds, tests, and deploys your code whenever code changes, based on  release flow patterns you define. 
- This allows you to  deliver features and updates quickly and reliably. Build and test the code.

**AWS CodeBuild** 

- AWS CodeBuild is a `fully managed build service` for compiling source code, running tests, and producing deployment-ready software packages. 
- With CodeBuild, you don't need to provision, manage, and extend your own build servers. 
- CodeBuild is constantly evolving and handles multiple concurrent builds, so your builds don't have to wait in queues. 

### 1.2. Deployment Automation 

**AWS CodeDeploy**
 

- AWS CodeDeploy automatically deploys code  to any instance, including Amazon EC2 instances and on-premises servers. 
- AWS CodeDeploy makes it easy to  release new features quickly, helping you avoid downtime when deploying your application, and managing the complexity of updating your application. 

### 1.3. Unified CI/CD project 

**AWS CodeStar**
 

- AWS CodeStar lets you rapidly develop, build, and deploy applications on AWS. 
- AWS CodeStar provides a unified user interface that allows you to easily manage your software development activities in one place. 
- With AWS CodeStar, you can set up your entire continuous delivery toolchain in minutes, so you can release your code faster. 
 

## 2.  Microservices
 
Build and deploy  microservices architecture using containers or serverless computing.  

### 2.1. Production Docker Platform 

**Amazon Elastic Container Service**

Amazon Elastic Container Service (ECS) is a  high performance and `highly scalable container` management service that supports Docker containers and allows you to easily run applications on a cluster managed  Amazon EC2 replica. 

### 2.2. Computer without server 

**AWS Lambda** 

- AWS Lambda allows you to run your code without provisioning or managing your server.  
- With Lambda, you can run code for virtually any type of backend application or service, all with no need for administration. 
- Simply upload your code and Lambda will handle everything needed to run and scale your code with high availability.  

## 3. Infrastructure as code 

- Use code and templates to provision, configure, and manage  AWS infrastructure resources.
- Monitor and enforce infrastructure compliance. Provide template-based infrastructure
 
### 3.1 Configuration Manager 
  

**AWS Systems Manager**
 

- AWS Systems Manager is a management service that helps you automatically collect software repositories, apply operating system patches, create system images, and configure Windows and Linux operating systems. 
- These features help you identify and track system configurations, prevent drift, and maintain software compliance for your EC2 and on-premises configurations.

### 3.2. Deploying template-based infrastructure

**AWS CloudFormation**

AWS CloudFormation provides developers and system administrators with an easy way to create and manage collections of related AWS resources,  and provision and update them in an orderly and predictable way. 


### 3.3. Chef configuration management 

**AWS OpsWorks**

- AWS OpsWorks is a configuration management service that uses Chef, an automated platform that treats server configurations as code. 
- OpsWorks uses Chef to automate how servers are configured, provisioned, and managed in Amazon Elastic Compute Cloud (Amazon EC2) instances or on-premises computing environments. 



### 3.4. Policy as code 

**AWS Config**

- AWS Config is a managed service that provides  AWS resource inventory, configuration history, and configuration change notifications to enable security and governance. 
- You can use Config Rules  to create rules that automatically inspect the settings of AWS resources recorded by AWS Config. 
- You can provision your infrastructure from an AWS CloudFormation template and call AWS Systems Manager to track your software inventory, or  configure your instance and use AWS Config to automatically fix configuration inconsistencies. 

## 4. Monitoring and logging 

Log and monitor application and infrastructure performance in near real time. 

### 4.1. Cloud and network monitoring 

**Amazon CloudWatch**

- Amazon CloudWatch is a monitoring service for AWS cloud resources and  applications running on AWS. 
- You can use Amazon CloudWatch to collect and track metrics, collect and monitor log files, set alarms, and automatically respond to changes in  AWS resources.  

### 4.2. Distributed trace 

**AWS X-ray**

 

- AWS X-Ray helps developers analyze and debug  distributed production applications such as B. 
- Built with a microservices architecture. With X-Ray, you can understand the performance of your applications and  underlying services  to identify and troubleshoot performance issues and the root cause of  errors. 
 
### 4.3. Activity and API usage tracking 

**AWS CloudTrail**

- AWS CloudTrail is a web service that records AWS API calls for your account and provides log files. 
- The information recorded  includes the  API caller's ID, the time of the API call, the source IP address of the API caller, the request parameters, and the response elements returned by the AWS service. 
 

## 5. Platform as a service 

Deploy web applications without provisioning and managing the infrastructure and application stack. 

### 5.1. Running and managing web apps 

**AWS Elastic Beanstalk** 

- AWS Elastic Beanstalk is  for deploying and scaling web applications and services developed using Java, .NET, PHP, Node.js, Python, Ruby, Go and Docker on well-known servers such as Apache and Nginx. 
- It is an easy-to-use service. Simply upload the code and Elastic Beanstalk will handle the provisioning for you, from capacity provisioning to load balancing, autoscaling, and application health monitoring. 
- At the same time, you have full control over  AWS resources that support your application and always have access to the underlying resources.

## 6. Version control 

Host a secure and scalable Git repository in the cloud. 

### 6.1. Private Git Hosting 

**AWS CodeCommit**
 

- AWS CodeCommit is a fully managed source control service that makes it easy for your organization to host secure and  scalable private Git repositories. 
- With CodeCommit, you can  securely store everything from source code to binaries and work seamlessly with your existing Git tools.



Gratitude for perusing my article till end. I hope you realized something unique today. If you enjoyed this article then please share to your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.

