# Configuring an Azure function behind a NAT gateway to restrict outgoing IP addresses

# Introduction

**Azure Virtual Network Address Translation** is a fully managed and resilient PaaS offering from Azure that simplifies outbound connectivity to virtual networks. You can define a virtual network egress connection to one or more subnets of a virtual network using a single public IP or a public IP prefix resource, or a combination of both. Once configured, traffic is routed through the NAT gateway without a custom route table.

# Use of Azure NAT

If your application requires a static IP address or range of IP addresses when sending traffic over the Internet or to a remote endpoint, `Azure NAT` is an easy solution to meet these requirements. Similar functionality can be achieved using a load balancer but using a NAT gateway makes it easy to configure and manage traffic flows without much effort. NAT uses Port NAT and is the recommended solution when deploying solutions in Azure. 

In this article, you'll understand how to configure an Azure function behind a NAT gateway to restrict outgoing IP addresses.

# Create an Azure virtual network using function subnets

An Azure virtual network is the building block for secure communication between Azure resources, the Internet, and an on-premises network. It provides features such as network traffic filtering, routing, DDoS protection, and integration with other Azure services. 


- In the Azure portal, enter `virtual networks` in the top search box and click Virtual Networks under Services.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669534801133/aw54Anj7j.png align="center")


- To create a new virtual network resource, click the `Create Virtual Network` button in the middle of the window.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669534841064/pU2ENu_ZK.png align="center")

- In the Create virtual network box that appears, enter the following values in the Default tab.


![imageonline-co-censored-image.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1669535102617/eOOQqNfLz.jpg align="center")

- Click Next: View the network IP addresses and IPv4 address space.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669535183608/UnBdepPMF.png align="center")

- On the same page, click `+ Add Subnet`, click Add Subnet in the pop-up window, enter the following information, and then click `Add`.

**Subnet Name:** function-subnet
**Subnet address range:** 10.0.1.0/24


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669535232568/gk-XYWXks.png align="center")


> You will use this private subnet to configure a NAT gateway to control traffic flow to the Azure Function.

- Click Next: Security and review the configuration.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669535262159/SN8S6V4_E.png align="center")

- Click `Review + Create` to review the settings, then click `Create` to begin creating your virtual network resource. 

# Create a premium Azure Function app

> Azure Functions is a serverless computing service in Microsoft Azure. You can deploy your code using Azure Functions without worrying about the servers your code will run on. Azure features three basic hosting services, including consumer plans, premium plans, and dedicated plans. All three plans come with unique offerings and limitations, including scalability, security, network connectivity, and support for custom images.

- In the Azure portal, enter `Function App` in the top search box and select `Function App` under Services.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669535416508/WXqy1h2eA.png align="center")


- Click `Create a function app` in the center of the screen and enter the following values in the Basics tab of the Create Function App window.


![imageonline-co-censored-image (1).jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1669535670750/BXRxd3tdj.jpg align="center")



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669535890305/ogXgjp9RK.png align="center")

- Click on the `Monitoring` tab and make sure it is set to No.

- Click the `Review + Create` tab and click the `Create`. 



# Create an HTTP trigger function to display the outgoing IP

There are several ways to create and deploy Azure Functions. In production, you can set up a deployment mechanism that allows Azure Functions to pull the latest version of your code from your version control system. Function apps provide different types of functions, including HTTP triggers, Timer triggers, Cosmos DB triggers, Blob storage triggers and Queued storage triggers.


- In the top search bar of the Azure portal, search for the function app which was created earlier.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536030248/3PRNaV7WM.png align="center")


- To see your `Outbound IP addresses` and `Additional Outbound IP Addresses`, click the `Properties` button under Settings in the left panel menu.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536107444/i42DcaTZK.png align="center")

> The IP addresses listed here are used by the platform as the source IP address when sending HTTP requests or feature-generated traffic. 

- Select Functions from the left panel menu and click `+ Create`.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536136717/TY_xSt-c7.png align="center")

- Select the `HTTP trigger` from the Template to use.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536195357/E-we3_XRl.png align="center")

- Enter `OutboundIP` in the New function name field. When you're done, click `Create`.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536261406/GJcjHdT7M.png align="center")

- Click `Code + Test` from the left menu options and replace the editor code with the following code snippet.

```
#r "Newtonsoft.Json"

using System.Net;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Primitives;
using Newtonsoft.Json;

public static async Task<IActionResult> Run(HttpRequest req, ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    var client = new HttpClient();
    var response = await client.GetAsync(@"https://ifconfig.me");
    var responseMessage = await response.Content.ReadAsStringAsync();

    return new OkObjectResult(responseMessage);
}
```

> The function above makes an HTTP request to get the public IP address of the network it uses to connect to the Internet. The response is then captured and displayed as part of the result.


- After changing the code, click `Save`. Click `Test/Run` and then click `Run` to trigger the function app and leave the `body` content as default.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536368625/j7bfHFm0r.png align="center")


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536439751/GyiNQZDMo.png align="center")

**OUTPUT WINDOW**


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536505855/DP0oU4_Tu.png align="center")

You should see an output that shows the outgoing IP address that the function application is using to communicate with the remote endpoint. 


# Using Vnet Integration in Azure Functions

You connect your function app to a virtual network subnet and test the function to ensure that the egress IP address of your function application is the same as the public IP address associated with your NAT gateway. 


- Return to the Azure Function App resource. Under `Settings` in the left menu options, select `Networking` and click `Virtual Network Integration`.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536642697/E_ILdWznS.png align="center")

- Click the `+ Add virtual network` button and select the `demo-vnet` virtual network from the `Function-Subnet` drop-down list.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536698435/gjmd_slXC.png align="center")

- Click `OK` and wait for the deployment to complete. 


- Once the connection is established, you will see the virtual network configuration listed on the Virtual Network Integration page.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536771753/xMBPIYfhK.png align="center")





- Return to the Function app, select `Configuration` under `Settings` from the left menu, and click `+ New Application Setting`.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536819549/VtJWJkMvp.png align="center")

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669536858492/9aw7cdzvU.png align="center")

- Enter the following information for Name and Value and click OK.

**Name:** WEBSITE_VNET_ROUTE_ALL
**Value:** 1



> By default, this feature directs RFC1918 traffic to the virtual network only if the application is configured with virtual network integration. This means that by default it only points to the private IP address space and not to public IP addresses. The application settings configured above are required to redirect all outgoing traffic to the virtual network from the application.

- On the Setup page, click `Save` to finish configuring the app settings.





# Create a NAT gateway and associate it with an Azure virtual network subnet


- Enter the `Public IP` in the upper search window of the Azure portal and select the public IP address for the service.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669537551494/W-owal8Cx.png align="center")



- In the middle of the screen, click on the Create Public IP address, use the following information from the Pop-Up window and click `Create`.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669537636562/cNAvcHNVu.png align="center")


![imageonline-co-censored-image (2).jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1669537728588/G-hnS6q5a.jpg align="center")

- In the Azure portal search box, find `NAT Gateway` and select `NAT Gateway` under the service.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669537811320/IjLKKKu4O.png align="center")

- Click the `Create NAT Gateway` button and enter the following information.

![imageonline-co-censored-image (3).jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1669537921610/_wHRg67sE.jpg align="center")

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669538118987/68w2gMqIh.png align="center")


- For now, click `Review + Create` and `Create` to finish creating the resource. 

- Under Settings on the left menu, click Subnets and select the following options for subnet settings:

**Virtual Network:** demo-vnet
**Subnet Name:** function-subnet


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669538219217/flAqskL7G.png align="center")

- When you're done, click `Save`.



# Check the Azure Function NAT configuration

- Go to the Azure Function resource under Function Options and click on the `OutboundIP` function you created earlier.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669538420423/U0Il6PkM_.png align="center")

- Click `Code + Test` -> `Test/Run` and `Run` to trigger the function.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669538692124/6-iAiAVo6.png align="center")

- Check the output of the function.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669538740643/tSPddGYez.png align="center")


- The IP addresses listed here correspond to public IP addresses configured as NAT gateways. 

- Navigate to the NAT Gateway resource under your account and click the Outbound IP.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669538763959/tbYxBxOLw.png align="center")

# Conclusion

The IP addresses listed here match the output of the function, confirming that your Azure function has been configured with a NAT gateway and that all traffic now flows through the NAT gateway using the assigned public IP address and egress IP address.


Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article then please share it with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)

























