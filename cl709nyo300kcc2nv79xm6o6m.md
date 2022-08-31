## A Deep Dive Into Host a Web Application With Azure App Service

## Introduction

Imagine building a website for a new business or running an existing web application on an outdated local server. Setting up a new server can be difficult. You need proper hardware, probably a server level operating system and a web hosting stack.

Once it is up and running, you will need to maintain the server. And what happens when your website traffic increases? It may be necessary to invest in extra hardware.

The hosting of your web application using the Azure -Service app makes the implementation and management of a web app than the management of a physical server much easier. 


## Create a web app in the Azure portal


### Why use the Azure portal?

- The first step when hosting the web application is to create a web app in the Azure subscription. 
- There are several ways to create a web application. 
- You can use the Azure portal, Azure Command Line Interface (CLI), script, or IDE. 
- The portal helps you discover available features, add additional resources, and customize existing resources.

### What is Azure App Service?

> Azure App Service is a fully managed web application hosting platform. This platform as a service offered by Azure allows you to focus on designing and building your application while Azure takes care of the infrastructure to run and scale your applications.

### Deployment slots

You can easily add deployment slots to an App Service web app using the Azure portal. 

For example, you can create a staging deployment slot where you can submit your code to Azure for testing. Once you are happy with your code, you can easily swap the staging deployment slot with the production slot. You can do all this with a few simple mouse clicks in the Azure portal.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660898914710/PEHXoxDoy.png align="left")

### Continuous integration / deployment support

The Azure portal offers seamless **out-of-the-box integration** and deployment with following service

- Azure DevOps
- GitHub
- Bitbucket
- FTP or a local Git repository on your development machine.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660899186711/PWsG48MJZ8.png align="left")


Connect your web app to one of the previous sources and App Service will do the rest for you by automatically syncing your code and any future code changes with the web app. 

> *Additionally, Azure DevOps allows you to define your build process and release that compiles the source code, runs the tests, creates a version, and finally deploys the version to the web app each time you commit the code. All this implicitly happens without having to intervene.*

### Integrated Visual Studio -Publication and Publication FTP

In addition to setting up the continuous integration/implementation for your web app, you can always benefit from rigid integration with Visual Studio to publish your web app on Azure through web implementation technology. The app service also supports publication based on FTP for more traditional work flows.

### Support for built -in auto scale

Depending on the use of the web app, it is possible to resize the up/down app increasing/lowering the sources of the machine below that your web app hosts. Resources can be the number of cores or the amount of RAM available.

Scale-out, on the other hand, is the ability to increase the number of machine instances that the web app runs on.

## Create a web app

When you're ready to run a web app on Azure, go to the Azure portal and create a web app resource. Creating a web app assigns a set of hosting resources in App Service, which you can use to host any Azure-supported web application, be it ASP.NET Core, Node.js, Java, Python and so on.



## Operating systems

If you deploy your app as code, many of the runtime stacks available are limited to one operating system or the other. After selecting a runtime stack, the toggle will indicate whether or not you have a choice of operating systems. If your target runtime stack is available on both operating systems, choose the one you will use to develop and test your application.

If your application is packaged as a **Docker image**, select the operating system on which you want to run your image.

Selecting Windows activates the Monitoring tab, which gives you the option to enable **Application Insights**. 

### Application Insights

- Enabling this feature configures your application to automatically send detailed performance telemetry data to the Application Insights monitoring service without requiring any changes to your code. 
- You can also use Application Insights from apps hosted on Linux, but this no-code turnkey option is only available on Windows.

## App Service Plans

- An App Service plan is a collection of virtual server resources that run App Service apps. 
- App service plan's size determines the capabilities of the virtual servers running the apps assigned to the plan and the App Service features those apps have access to. 
- Each App Service web app you create must be associated with a single App Service plan that runs it.

***A single App Service plan can host multiple App Service web apps. In most cases, the number of apps you can run on a single plan is limited by the apps' capabilities and the plan's resource limitations.***

## Demo - Create a web app


- In the Azure portal menu or from the home page, select **Create a resource**. Everything you create on Azure is a resource. The box is displayed creates a resource box.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660900274082/ZRYhWDRkC.png align="left")

Here, you can look for the resource you want to create or select one of the popular resources that people create in the Azure portal. 

- From the Create an resource menu, select **Web**.


![19080246.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660900614921/9OjYyP7VA.png align="left")

- Select **Web App**. If you don't see it, search for and select **Web App** in the search box. The **Create Web App** Resource pane appears.


![19080247.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660900685496/eeFkFVsc1.png align="left")

- On the Basic tab, enter the following values ​​for each setting.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660896933000/Xv_O7kMJO.png align="left")

- Select **Review + Create** to access the review panel, then select **Create**. The portal displays the deployment area, where you can view the status of your deployment.

## Preview your web application

When the deployment is complete, select **Go to resource**. The portal displays the App Service Overview panel for your web application.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660897275230/a0NE_CDfx.png align="left")

To preview your web app's default content, select the URL at the top right. The loaded placeholder page indicates that your web application is running and ready to deploy your application code.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660897341280/CmNCrMbdw.png align="left")

## Conclusion

App Service makes web app management and control easier than traditional hosting options. Your App Service Plan can help you reduce the time and effort spent running and managing your web app and provide advanced cloud features such as autoscaling and integration with Git.


Gratitude for perusing my article till end. I hope you realized something unique today. If you enjoyed this article then please share to your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)
