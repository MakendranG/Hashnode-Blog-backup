# Understanding Azure Kubernetes Service

# Introduction

In this article, You will understand the Azure Kubernetes service. You will create an AKS and deploy a container on it.

# What is Kubernetes?


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667230184586/B8LaoqXdX.png align="center")

*[Image Source](https://concisesoftware.com/blog/what-is-kubernetes/)*

- Container-based applications and their associated networking and storage components are managed by the Kubernetes platform. 
- The underlying infrastructure components are not the focus of Kubernetes. 
- There is a robust set of APIs for management operations.
- You can build and run modern, portable, microservices-based applications using Kubernetes. 
- As teams progress through the adoption of microservices-based applications, Kubernetes supports both stateless and stateful applications.

> You can build applications with your preferred programming language, OS, libraries, or messaging bus on the open platform. CI/CD tools can be used to schedule and deploy releases.



# Kubernetes cluster architecture


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667230280271/kNxzSGgiD.png align="center")

*[Image Source](https://learn.microsoft.com/en-us/azure/aks/concepts-clusters-workloads)*

A cluster is made up of two parts.

- The control plane provides the core services.
- Run your application workload with the help of the Nodes.

## Control plane

A control plane is created when you create an AKS cluster. The control plane is free of charge and can be accessed by the user. You only pay for the AKS cluster. The control plane and resources are located in the region where you created them.

The control plane has core components. They are

- kube-apiserver
- etcd
- kube-scheduler	
- kube-controller-manager


## Nodes

To run your applications and support services, you need a container. An AKS cluster has at least one virtual machine that runs the Kubernetes components and container runtime.

The Kubernetes node components re

- kubelet
- kube-proxy
- container runtime




# What is AKS?


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667229937228/LEOdbC9IW.png align="center")

[Image Source](https://rafay.co/the-kubernetes-current/getting-started-with-azure-kubernetes-service-aks/)

The AKS simplifies the deployment of a managed Kubernetes cluster in Azure. Critical tasks, like health monitoring and maintenance, are handled by Azure. You only manage and maintain the agent nodes if you manage the masters. 

> AKS provides a managed service that reduces the complexity of deployment and core management tasks. You only pay for the AKS nodes that run your applications if you use the Azure platform.


# Demo

Kindly watch the below video to understand the Azure Kubernetes service. 

<iframe width="760" height="415" src="https://www.youtube.com/embed/X7Ilt3ihoRA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Conclusion

You created an Azure Kubernetes service. Deployed a container on Azure Kubernetes Service and created a service for the container.


Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article then please share it with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.

Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)