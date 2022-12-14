# Getting Started with Amazon Elastic Container Service with Fargate

# Introduction

## What is Docker?


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665817168535/nJV_kVYee.png align="center")
*[Image Source](https://umbrella.cisco.com/blog/considering-docker-consider-security-first)*

- **Docker** is a tool that makes it easy to build, deploy, and run applications using containers. 
- Containers allow developers to package and *deploy applications as a single package*, along with all necessary components such as libraries and other dependencies.
- This ensures that the program will run on any other Linux machine, regardless of your custom settings on the machine, which may be different from the machine you use to write and test the code.


## What is Amazon ECS?


![Arch_Amazon-Elastic-Container-Service_64@5x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665817256433/n6Bo2qF8e.png align="center")


- Amazon ECS manages containers and allows developers to run applications in the cloud without configuring the environment to run their code. 
- It allows developers with AWS accounts to deploy and **manage scalable applications** running on groups of servers called *clusters* through application program interface calls and task definitions.
- Amazon ECS makes it easy for developers to use Docker containers for a variety of tasks. 
- These range from hosting *simple websites to running complex distributed microservices* that require thousands of containers.


# Running Amazon ECS with Fargate


![Arch_AWS-Fargate_64@5x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665817280792/xRYi6KHwl.png align="center")

You can run services or tasks on *AWS Fargate* to deploy containers on serverless infrastructure managed by Amazon ECS.

Let's launch Amazon ECS on AWS Fargate using the Fargate launch type for our task. In regions where Amazon ECS supports AWS Fargate, the Amazon ECS First Startup wizard guides you through the Amazon ECS launch process using the Fargate launch type.

The wizard creates a cluster and gives you the option to run a sample web application.

Kindly watch the below video on how to create a task definition, a service, and a cluster using Fargate.

<iframe width="760" height="415" src="https://www.youtube.com/embed/UY9ishwjFYQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Conclusion

You have successfully created a task definition, a service, and a cluster using Fargate.


Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article then please share it with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)




