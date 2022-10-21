# Centralized Operations Management on AWS by using AWS System Manager

# Introduction


![Arch_AWS-Systems-Manager_64@5x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666380789241/V6V7p6Mi7.png align="center")

You can manage your applications and infrastructure in the cloud with the help of the `Systems Manager`. Systems Manager simplifies application and resource management, shortens the time to detect and resolve operational problems, and helps you manage your resources securely at scale.

# How Systems Manager works


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666380716959/Vg2yJPAdA.png align="center")

*[Image Source](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)*


- The Systems Manager will verify that your user, group, or role has permission to perform the action you specified. 
- If the target of your action is a managed node, the Systems Manager Agent will perform the action. 
- The systems Manager, SSM Agent, and other services performed an action on behalf of the Systems Manager report status. If configured, the Systems Manager can send status details to other services.
- If enabled, Systems Manager operations management capabilities such as Explorer, OpsCenter, and Incident Manager aggregate operations data or create artifacts in response to events or errors with your resources. 
- The artifacts include operational work items. Systems Manager operations management capabilities give operational insight into your applications and resources.



# Features of AWS System Manager

There are four core feature groups that make up the operations hub for your AWS applications and resources.


## Operations Management

### Explorer

- Explorer is a dashboard that shows information about your resources. 
- There is an aggregated view of operations data for your accounts in explorer.

### OpsCenter

- Operations engineers and IT professionals can view, investigate, and resolve operational work items in a central location. It is designed to reduce the mean time to resolve issues. 
- Systems Manager Automation runbooks can be used to resolve issues. 
- You can specify the data you want for each item. 
- You can see the reports by status and source.


### Incident Manager


- Users can mitigate and recover from incidents affecting their applications with the help of the Incident Manager. 
- Incident Manager increases incident resolution by notifying responders of impact, highlighting relevant data, and providing collaboration tools to get services back up and running. 
- The incident manager can automate response plans.


## Application Management

### Application Manager

Application Manager helps engineers investigate and fix issues with their resources in the context of their applications and clusters.


### AppConfig

AppConfig can help you create, manage, and deploy application configurations. AppConfig can be used to deploy applications of any size.


### Parameter Store

Parameter Store has storage for configuration data and secrets.



## Change Management

### Automation

Common maintenance and deployment tasks can be automated.


### Change Manager

Change Manager is an enterprise change management framework for requesting, approving, implementing, and reporting on operational changes to your application configuration and infrastructure.


### Maintenance Windows

The maintenance Window can be used to set up recurring schedules for managed instances to run administrative tasks.


## Node Management

### Fleet Manager

Fleet Manager is a UI experience that allows you to remotely manage your nodes.

 
### Session Manager

Session Manager can be used to manage edge devices and Amazon EC2 instances.

 
### Patch Manager

Patch Manager can be used to automate the patching process of your managed nodes.

# Use cases

1. Aggregate data in a single console and gain actionable insights across services.

2. It's possible to resolve application issues automatically.

3. Use operational data to easily manage applications and identify issues.

4. Proactive processes such as patching and resource changes can be automated to diagnose and fix operational issues before they affect users.

In this article, you'll get started with `Centralized Operations Management` by using the capabilities of the system manager, such as 

- Fleet Manager
- Patch Manager
- State Manager
- Automation runbooks.

The article focuses on managing EC2 instances at scale, patching operations on the managed fleet, and using Automation runbooks to simplify maintenance tasks.

# Set up AWS Systems Manager using Quick Setup

## Quick Setup

`Quick setup` is a feature of the Systems Manager that can be used to quickly set up security roles on your Amazon EC2 instances. Quick setup can be used in an individual account or across multiple accounts. The minimum required permission to get started is provided by these capabilities, which help you manage and monitor the health of your instances.

To get started with Quick Setup, you need to choose a home region and onboard with it. Quick Setup creates the resources that are used to deploy your configurations in the home region.

## IAM roles and permissions

Permissions and roles are part of the IAM. Quick setup creates the following IAM roles on your behalf.

- AWS-QuickSetup-StackSet-Local-ExecutionRole
- AWS-QuickSetup-StackSet-Local-AdministrationRole

If you're setting up a management account, Quick Setup creates the following roles on your behalf.

- AWS-QuickSetup-SSM-RoleForEnablingExplorer
- AWSServiceRoleForAmazonSSM
- AWSServiceRoleForAmazonSSM_AccountDiscoverey
- Launch Amazon EC2 Instances to manage with AWS Systems Manager


Kindly watch the below video to launch Amazon EC2 Instances to manage with AWS Systems Manager.

<iframe width="760" height="415" src="https://www.youtube.com/embed/d6N5Sk-5-jg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


We used the Quick Setup feature of the Systems Manager to get started. We now have the necessary roles and permissions set up so that we can leverage the power of the Systems Manager.

# Patch Nodes Managed By AWS Systems Manager

The process of patching managed nodes with both security-related and other types of updates can be done with the help of Patch Manager.

## Patch Manager

- **Patch Manager** can be used to apply patches. 
- Patch Manager uses patch baselines, which include rules for auto-approving patches within days of their release, as well as a list of approved and rejected patches. 
- Scheduling patching to run as a Systems Manager `State Manager association` will allow you to install patches on a regular basis.


We will use a patch baseline to quickly learn how to use Patch Manager.

Kindly watch the below video to Patch your managed nodes using Patch Manager.

<iframe width="760" height="415" src="https://www.youtube.com/embed/qwT4wKGcM4c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


We ran a simple patching operation on our managed instances after establishing a default patch baseline. We can schedule patching operations by creating a patching configuration that will allow us to perform patching during a defined window.

# Resize an EC2 instance using Systems Manager Automation

Common maintenance, deployment, and remediation tasks can be simplified with the help of **automation**.

Kindly watch the below video on how to use an automation runbook to resize EC2 instances.

<iframe width="760" height="415" src="https://www.youtube.com/embed/iILI5Fa2s6c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


We explored the power of Systems Manager Automation runbooks by resizing our instances to the desired instance type. The Systems Manager Automation runbook reference can be used to get started working with runbooks. 



Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article then please share it with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.

Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)