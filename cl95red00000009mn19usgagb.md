# Deploy containerized workloads with Amazon Lightsail

# Introduction to Amazon Lightsail

Amazon Lightsail is an easy-to-use cloud platform that provides everything you need to build an app or website with an affordable monthly fee. 


![Arch_Amazon-Lightsail_64@5x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665583565904/xnaRBTouK.png align="center")

Lightsail Containers, announced at **re:Invent 2020**, aims to make it easy for you to build container-based apps and websites. To deploy containers in Lightsail, you create a container service that only specifies a few parameters, its performance, and its scope. 

> AWS manages the compute, network, and traffic management for you. You can deploy up to ten containers in a container service, and one of them can be chosen as the public endpoint. Lightsail provides a secure, load-balanced HTTPS endpoint to access the public endpoint.


- You can create a website or app with just a few clicks. 
- Automatically configure your network, access and security environment. 
- Easily scale as you grow or migrate resources to the broader AWS ecosystem, such as Amazon EC2.
- Enjoy the security and reliability of the world's largest cloud platform.

> Amazon Lightsail offers easy-to-use virtual private server (VPS) instances, containers, storage, databases, and more for one low monthly price.

# Use cases of Amazon Lightsail


- It uses preconfigured development stacks such as LAMP, Nginx, MEAN and Node.js. 
- Create and customize your blog, e-commerce or personal website in just a few clicks using pre-configured applications like WordPress, Magento, Prestashop and Joomla. 
- Run business software such as: File storage and sharing, backup, finance and accounting software and more.

In this article, you will see how to test Lightsail containers by deploying a web server container.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665577018583/zaz7M4Sx6.png align="center")

# Creating a Lightsail Container Service

The Lightsail console allows you to manage all the resources provided by Lightsail, including instances, containers, and databases. 

> The AWS Command Line Interface (CLI), Software Development Kit (SDK), and REST API can also be used to manage Lightsail resources, but the console provides the best integration experience.

Amazon Lightsail Container Service is a highly scalable, fully managed compute and network resource for container deployments. 

The lightsail container service architecture diagram looks like this:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665577169888/gzoNlpxxb.png align="center")

*[Image Source](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-container-services)*

When you create a container service, in addition to the target zone and availability zone, you must configure the following:

**Power**

Corresponds to the amount of CPU and memory of the container service. 

Available capacities are 

- Nano(Na)
- Micro(Mi)
- Small(Sm)
- Medium(Md)
- Large(Lg)
- Xlarge(Xl)

**Scale**

- The number of nodes on which to calculate the deployment workload. 
- Each node has a copy of the container and requests are distributed to all nodes.

> Container services can use container images available in public container registries such as Docker Hub, or images sent to the container service from your local machine.

Kindly watch the below video on how to create a Lightsail Container Service.

<iframe width="760" height="415" src="https://www.youtube.com/embed/gFSP-cZ9z7M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>




# Deploying Containers to Lightsail Container Service


The Lightsail container service can use a `public container registry` or `container image` on your local machine. 

> To deploy a container in a container service, you must define a deployment. An implementation can have up to 10 containers in its specification and a container can be designated as public via the container service scope. The selected container is called the **public deployment endpoint**.


You can also specify general container settings, including ports and environment variables. The container service may have used one implementation at a time, called the **current implementation**.

Kindly watch the below video on how to deploy Containers to Lightsail Container Service.


<iframe width="760" height="415" src="https://www.youtube.com/embed/j2kse8TGwwo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>




# Monitoring the Lightsail Container Service Deployment

The Lightsail console includes tools for viewing deployment logs and statistics. These devices help diagnose problems and measure the functionality of containers. 

Kindly watch the below video on how to deploy Containers to Lightsail Container Service.

<iframe width="760" height="415" src="https://www.youtube.com/embed/kxqJRnl1ozU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



# Conclusion

To Summarize, You can use Amazon Lightsail if you are running the test environment, creating applications for small businesses, create a custom website and running a simple web application. 

[Get started with Lightsail](https://lightsail.aws.amazon.com/ls/webapp/home?p=lgt&cp=bn&ad=c)


Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article then please share it with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)



