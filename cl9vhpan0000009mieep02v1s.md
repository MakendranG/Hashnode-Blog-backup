# Deploying Custom App Image to Container Apps using Azure Container Registry

# Introduction

In this article, you will learn how to use the Azure portal to deploy custom container images to container apps.

# Azure Container Registry

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667141577527/lQu47Br_0.png align="center")

- Container images and related artifacts can be stored and managed through the ACR service. 
- ACR can be used with your existing deployment process. 
- Trigger-based build on source code commits and base image updates can be used to build automated deployment tasks.




# Azure Container Apps


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667141541220/iIClLSZEU.png align="center")

- You can run container-based web applications using the azure container app. 
- You can run multiple container revisions. 
- Container applications are useful for organizations that want to take care of the hosting and security of the container application. 
- It's easier to cross-communicate between container applications with the system fully supporting the Distributed Application Runtime.

> The container app lets you manage and publish a new release to the environment using CI/CD mechanism that enables the team to achieve their goals for continuous release. The apps can scale based on demand. The integration with the container registry allows the environment to be fully automated where new releases to the registry automatically update the container app accordingly.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667140670004/zTs1Uv1yz.png align="center")
*[Image Source](https://learn.microsoft.com/en-us/azure/container-apps/overview)*

Container apps allow you to enjoy the benefits of running containers while leaving behind the concerns of managing cloud infrastructure and complex container orchestrators.

# Azure Container Apps Features 

- Manage the container app's application lifecycle by running multiple container revisions.

- You can scale your apps based on any scale trigger. 

- It is possible to enable HTTPS without having to manage other infrastructure.

- Traffic can be split across multiple versions of an application.

- For secure internal-only endpoints, use internal and service discovery.

- You can access the rich set of APIs with the help of Dapr.

- You can run containers from any registry, public or private.

- You can use the azure CLI extension, azure portal, or arm templates to manage your applications.

- You can securely manage secrets in your application.

- Logs can be monitored using azure log analytics.




> The container app versioning is done by the azure container apps. Revisions are snapshots of the container app. Revisions are created on first-time deployment and on subsequent updates to the container app image.

# Demo

Kindly watch the below video on how to deploy Custom App Images to Container Apps using Azure Container Registry.

<iframe width="760" height="415" src="https://www.youtube.com/embed/Qu_o3Xupsj8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Conclusion

You added a custom image to the container registry using the Azure CLI and code environment. You used the container registry to create a revision for a custom image.

Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article then please share it with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.

Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)



