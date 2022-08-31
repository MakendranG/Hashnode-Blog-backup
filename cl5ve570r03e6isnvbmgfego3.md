## Improve application scalability and resiliency with Azure Load Balancer

Load balancing is the even distribution of load across a group of back-end resources or servers. The Azure Load Balancer works with `Layer 4` of the Open Systems Interconnection (OSI) model. The load balancer distributes the inbound flow arriving at the load balancer's front end to the back end pool instances. 

These flows comply with the configured load balancing rules and health probes. The backend pool instance can be an Azure virtual machine or an instance in a virtual machine scale set. 

A `public load balancer` can provide outbound connectivity to virtual machines (VMs) in a virtual network. These connections are made by translating  private IP addresses to public IP addresses. Public load balancers are used to  balance internet traffic to  VMs. 

If a private IP is only needed on the front end, an internal load balancer is used. `Internal load balancers` are used to  balance the traffic in the virtual network. In hybrid scenarios, you can access the load balancer front end over your on-premises network. 

## Use of an Azure load balancer

You can use Azure Load Balancer to scale your application to create highly available services. The load balancer supports both input and output scenarios. Load balancers provide **low latency and high throughput** that can be scaled to millions of flows in all TCP and UDP applications. 

The main scenarios  you can run with the Azure Standard Load Balancer are: 

- Load balancing internal and external traffic to Azure virtual machines. 
- Improve availability by balancing resources within and across zones. 
- Configure outbound connections for Azure virtual machines. 
- Use the **Health Probe** to monitor load-balanced resources. 
- Use **port forwarding** to access virtual machines in your virtual network using public IP addresses and ports. 
- Enables IPv6 load balancing support. 
- Standard Load Balancer provides multidimensional metrics via Azure Monitor. 
- Load balancing service on multiple ports, multiple IP addresses, or both. 
- Move internal and external load balancer resources between Azure regions. 
- Use the HA port to load balance TCP and UDP flows simultaneously on all  ports. 

## Secure by default 

- The default load balancer is based on the `zero trust network security model`. 
- The standard load balancer is `secure` by default and is part of the virtual network.  
- The default load balancer and default public IP address are closed for incoming connections unless opened by a network security group. 
- The Basic Load Balancer is published on the Internet by default. 
- The load balancer does not store customer data.

## Azure Load Balancer Components 

### Front-end IP configuration 

IP address of the Azure load balancer. These IP addresses are: 

1. Public IP address 
2. Private IP address 

The type of  IP address determines the type of load balancer created. Choosing a private IP address  creates an `internal load balancer`. Select a public IP address to create a `public load balancer`. 

#### Public load balancer

The public load balancer maps the public IP and port of incoming traffic to the private IP and port of the VM. The load balancer back maps the response traffic from the VM. You can distribute a particular type of traffic to multiple VMs or services by applying **load balancing rules**.

#### Internal load balancer
 
The internal load balancer distributes traffic to resources in the virtual network. Azure limits access to the front-end IP addresses of load-balanced virtual networks. Front-end IP addresses and virtual networks are `never exposed` directly  to Internet endpoints. That is, the internal load balancer cannot accept inbound traffic from the Internet. Internal line-of-business applications run in Azure and are accessed  within Azure or from on-premises resources. 

### Back end pool 

Adding or removing VMs from the backend pool reconfigures the load balancer without any additional action. The backend pool supports the addition of instances over a network interface or IP address. 

### Health probe 

Health probes are used to determine the `health status` of  instances in the backend pool. While creating the load balancer, configure the health probe used by the load balancer. This health probe determines if the instance is healthy and can receive traffic.

### Load balancer rules 

Load balancer rules are used to define how incoming traffic is distributed to all  instances in the backend pool. Load balancing rules map a particular front-end IP configuration and port to multiple back-end IP addresses and ports. Load balancer rules apply only to inbound traffic. 





### Highly available port 

This rule allows a single rule to balance all TCP and UDP flows arriving on all ports of the internal default load balancer. 

HA port load balancing rules are useful in critical scenarios such as network virtual appliance high availability and scaling for  virtual networks. This feature is useful when load balancing is required on a **large number of ports**. 


### Inbound NAT rules 

Inbound NAT rules direct inbound  traffic  to the front-end IP address and port combination. Traffic is sent to a specific virtual machine or instance in the backend pool. Port forwarding is done through the same hash-based distribution as load balancing. 

### Outbound rules 

Outbound rules configure outbound network address translation (NAT) for all virtual machines or instances identified by the backend pool. This rule allows backend instances  to communicate (outbound) with the Internet or other endpoints. 


## Load balancing algorithm 

You can distribute the incoming traffic stream from the load balancer front end to the back end pool by creating a load balancer rule. Azure Load Balancer uses a `5-tuple hash algorithm' to distribute incoming flows. 

The load balancer rewrites the headers of the TCP / UDP header flow when  traffic is routed to the backend pool instance. If the load balancer's health probe points to a healthy backend endpoint, you can use the backend instance to receive new traffic flows. 

By default, Azure Load Balancer uses a hash of 5 tuples. 

-  Source IP address 
-  Source port 
-  Destination IP address 
-  Destination port 
-  IP protocol number used to map the flow to available servers
 




The load balancer works at **layer 4** and does not provide application layer gateway functionality. Protocol handshakes are always done directly between the client and the backend pool instance. The load balancer does not interact with the TCP payload or provide TLS offload, allowing you to create rich cryptographic scenarios. 

Load balancers allow `large scale-out of TLS applications` by terminating TLS connections on the VM itself. The response to the 
inbound flow is always the response from the virtual machine. When the flow arrives at the virtual machine, it also retains the original source IP address. Each endpoint is responsive by the VM.  The response to the request to the front end is the response generated by the back end VM. After successfully verifying the connection to the front end, it verifies the connection to at least one back end virtual machine end-to-end.



Gratitude for perusing my article till end. I hope you realized something unique today. If you enjoyed this article then please share to your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)





