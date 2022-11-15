# Continuous integration and deployment with AWS code services

# Introduction

All of the tools you need to deliver software are provided by Amazon Web Services. 

In this article, you will work with the below mentioned Amazon Web Services.


- **CodeCommit** is a source control service. 
- **CodePipeline** is a service for continuous integration and continuous delivery. 
- **CodeBuild** is a service to build, test, and package source code. 
- **CodeDeploy** is a service to automate code deployment.



# Creating an AWS CodeCommit Repository


![Arch_AWS-CodeCommit_64@5x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668006093966/aBvNnW-Sj.png align="center")


Private Git repositories can be hosted by CodeCommit, a secure source control service. You can use CodeCommit to store code. It works with your existing Git-based tools because it supports the standard Git function. 

Kindly watch the below video to set up a repository for source control of your application and also to establish a secure connection to the repository because Code Commit is secure. 

<iframe width="760" height="415" src="https://www.youtube.com/embed/VFYQJlW7Hdw?start=10" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



# Committing Code to Your AWS CodeCommit Repository


Kindly watch the below video to commit code and use an EC2 instance for your development environment.  You will commit the code to your repository using Git with the command and credentials you copied to a text file in the previous Step. 

<iframe width="760" height="415" src="https://www.youtube.com/embed/OPAzTBPwtRQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Building and Testing with AWS CodeBuild


![Arch_AWS-CodeBuild_64@5x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668007189766/n3ue6f66K.png align="center")

The service supports continuous integration. You are charged for the number of minutes it takes the service to complete your build. You can modify the build environment of your choice with the help of CodeBuild. 

> CodeBuild has two ways to specify the build commands: entering a single shell command or defining a buildspec.

Kindly watch the below video to create a building project and built your app. 

<iframe width="760" height="415" src="https://www.youtube.com/embed/iJGCxBJ3ZIg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


# Deploying with AWS CodeDeploy



![Arch_AWS-CodeDeploy_64@5x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668007514567/C4Tf5U-zL.png align="center")

CodeDeploy is a platform-agnostic service. You can run CodeDeploy anywhere, not just on EC2 instances. The CodeDeploy Agent is installed on the server to respond to deployment tasks. 

> In-place and blue/green deployment types are supported by CodeDeploy.

A group of instances is targeted to deploy the application. Tags can be used to specify instances. The Elastic Load Balancer is used to balance requests between deployment group instances.

Kindly watch the below video to set up deployment groups for both in-place and blue/green deployment. 

<iframe width="760" height="415" src="https://www.youtube.com/embed/kDoiV9zmV4o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Automating Your Deployment with AWS CodePipeline


![Arch_AWS-CodePipeline_64@5x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668009116956/aL_oykhMd.png align="center")

CodePipeline is available in the cloud. You can describe your software release process with the help of the CodePipeline. Each stage is comprised of one or more actions. The action stages are connected. 

> Actions can include building or deploy, publishing to an SNS Topic for manual approval, or executing an Amazon function. Transitions are represented by arrows from one stage to the next.

An output artifact is created when a stage succeeds. The artifacts are kept in an S3 bucket. The following stage uses the artifact to perform actions. Subsequent stages are not executed if a stage fails. Assume you have a build stage and a deploy stage. CodePipeline will not attempt to deploy if the build stage fails. When a new source code revision is detected, the entire pipeline is executed.

Kindly watch the below video to create an end-to-end deployment that uses the services you have set up. 

<iframe width="760" height="415" src="https://www.youtube.com/embed/EvGvuSymxic" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Following the Continuous Deployment Pipeline


Kindly watch the below video to see continuous deployment in action under various scenarios.

<iframe width="760" height="415" src="https://www.youtube.com/embed/Wtyk3dPv-KU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Recovering Automatically from a Failed Deployment

Kindly watch the below video to see how the automatic rollback capabilities of CodeDeploy work. 

<iframe width="760" height="415" src="https://www.youtube.com/embed/xVKv3ghDFhc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Using AWS CodeDeploy Blue/Green Deployments in Your Pipeline


Up to this point, you have been using in-place deployment for your code. One disadvantage of in-place deployment is that an instance is out of service during an update. Your deployment group has fewer instances than you want to serve traffic. The one at a time deployment configuration can be used to minimize this impact. The time it takes to upgrade the deployment is longer. 



> The drawbacks of in-place deployment are overcome by blue/green deployment. The original blue environment and a second green environment are used to overcome in-place deployment issues. A green environment is created during deployment.

**How blue/green deployment works**

- There is no risk of configuration drift if you don't reuse instances. 
- The green environment has instances that install and run the new version of the application. 
- All of the instances in the blue environment are still serving traffic. 
- It is safe to switch traffic to the green environment once the green environment instances are ready. 
- The switch can be achieved using an Elastic Load Balancer. 
- The traffic becomes blue when it switches to a green environment. 
- If you anticipate needing to roll back, you can keep or destroy the original blue environment. 
- The blue and green environments are referred to as original and replacement in some areas.

Kindly watch the below video to see how CodeDeploy manages a deployment.

<iframe width="760" height="415" src="https://www.youtube.com/embed/kqlbrmMH4Tw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Conclusion

From this article, you will be able to do the below mentioned tasks successfully.

- You can create and use CodeCommit to control source control. 
- Test your code with CodeBuild. It's possible to automate your CI/CD process. 
- Use CodeDeploy to automate your deployment. 
- Roll back using a blue/green deployment strategy.



Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article then please share it with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.

Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)







