## The Essential Guide to Overview and Benefits of Gateway Load Balancer

# Introduction

Gateway Load Balancer is an Azure Portfolio SKU load balancer suitable for high-performance and high-availability scenarios using third-party Network Virtual Appliances. 

> The gateway load balancing feature simplifies the deployment, scaling, and management of NVAs. You can bind your gateway load balancer to a public endpoint with a single click.


The appliances can be used transparently for a variety of scenarios, including:

- Firewall
- Advanced packet analysis
- Intrusion detection and prevention system
- Mirror Traffic
- DDoS protection
- Custom appliances


> Gateway load balancers allow you to easily add or remove advanced network features without additional administrative costs. It provides the "bump-in-the-wire" technique needed to ensure that all traffic to the public endpoint is routed to the device before the application is deployed.

In NVA scenarios, it is especially important that the flow be symmetrical. Gateway Load Balancer maintains flow stickiness for specific instances in a server group along with flow symmetry.

This application provides continuous routing to virtual machines on the network without manual configuration. As a result, packets travel the same network path in both directions, and devices that require this basic functionality can continue to function. The health probe listens on all ports and uses HA port rules to direct traffic to the server instance. Traffic to and from the Gateway Load Balancer uses the VXLAN protocol. 

# Benefits


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663876241678/2qtwqRDRq.png align="center")

*[Image Source](https://www.hylton.ca/group-benefits-5-main-advantages)*


Gateway load balancers have the following advantages:

- Integrate virtual appliances transparently into network paths.
- Easily add or remove network virtual appliances from the network path. 
- Scale easily while keeping costs under control.
- Improves the availability of virtual network devices. 
- Connect apps across regions and subscriptions

You can associate a standard public load balancer or a standard virtual machine IP configuration with a gateway load balancer. After connecting to the standard public load balancer front-end or standard virtual machine IP configuration, no additional configuration is required to ensure that traffic to and from the application endpoint is routed to the gateway load balancer. 

Traffic flows from the customer's virtual network to the provider's virtual network. The traffic is then routed back to the customer's virtual network. The customer's virtual network and the provider's virtual network can exist in different subscriptions, tenants, or regions, so there are no administrative costs involved.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663875067495/HsBimgL2J.png align="center")

*[Image Source](https://learn.microsoft.com/en-us/azure/load-balancer/gateway-overview)*





# Components

A gateway load balancer consists of the following components:

## Front-end IP Configuration

- Gateway load balancer IP address. 
- This IP address is for private use only.

## Load balancing rules

- Load balancing rules are used to determine how incoming traffic is distributed across all instances in a server pool. 
- Load balancing rules assign specific configurations and forward IP ports to different server IP addresses and ports.

> A gateway load balancing rule can only be an HA port rule. A gateway load balancing rule can be associated with up to two server pools.

## Backend pool

- A group of virtual machines or instances from a scaled set of virtual machines that serve incoming requests. 
- For cost-effective scaling to accommodate large amounts of inbound traffic, compute guidelines generally recommend adding multiple instances to a server pool. 
- The load balancer reconfigures itself instantly with automatic reconfiguration when instances are scaled up or down. 
- Adding or removing virtual machines from the server pool reconfigures the load balancer without any additional action. 
- A server pool is covered for all virtual machines in a single virtual network.


## Tunnel Interfaces

- Gateway Load Balancing Server Pools have another component, Tunnel Interfaces. 
- A tunnel interface allows devices on the server to ensure that network flows are handled as expected. Each backend pool can have up to two tunnel interfaces. 
- Tunnel interfaces can be internal or external.

## Chain

- A gateway load balancer can refer to a standard public load balancer front end or a standard public IP configuration for a VM. 
- Connecting advanced network functions in a specific order is called service chaining. So these links are called chains.


# Limitations 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663875930599/d07U-qiPt.png align="center")

*[Image Source](https://www.macrorecruitment.com.au/coaching/possible-limitations-of-the-high-i/)*

- Gateway load balancers do not operate on the global load balancing tier 
- Cross-tenant connections through the Azure portal are not supported.
- Gateway load balancers do not currently support IPv6.
- Gateway load balancers currently do not support redundant front-ends for zones due to a known issue. 
- All frontends configured with zone redundancy are assigned an IP address with or without zones. 
- Frontends configured in the portal are automatically created without zones.


Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article then please share it with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)
