# Overview of Pulumi Deployments and Its Challenge Tutorial 101: The Essential Guide

# Introduction


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668875334862/dLf9syWpP.png align="center")

*[Image Source](https://www.pulumi.com/product/pulumi-deployments/)*

Pulumi Deployments is a new **deployment-as-a-service** technology that allows Pulumi to fully manage the infrastructure running as a code program for platform users. 

> One of the features of Pulumi Deployments is "Git Push to Deploy", which allows you to run a deployment whenever you add and push a Git repository.

Pulumi deployments help you provision infrastructure quickly and manage 10x scale.


# Pulumi Deployments Preview

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668868851854/zknF1dBM7.png align="center")

*[Image Source](https://www.pulumi.com/product/pulumi-deployments/)*

Pulumi Deployments is a new feature that automates the running of Pulumi applications in a secure hosting environment. 

> Deploy any stack with a click of a button, git push, or API call. Available as a preview today.


# What are the benefits of Pulumi Deployments?

- Pulumi Deployments accelerate infrastructure deployments by remotely executing the `pulumi up` command when you click a button, push into a GitHub branch, or call the Deployments REST API. 
- Instead of using a CLI, you can use a managed service to run Pulumi applications and automate large-scale cloud deployments. 
- Pulumi deployments are based on the same technology as the Pulumi Automation API, enabling organizations to manage up to 10x more cloud infrastructure resources per engineer compared to other infrastructures such as code tools.

Click on this **[link](https://www.pulumi.com/product/pulumi-deployments/)** and Join Preview.

# Challenge 

In this challenge, you will learn how to 

- Create a project in the Pulumi service console to select an architecture model.
- Create a Pulumi application.
- Connect GitHub to your Pulumi deployment.
- Start updating your Pulumi service stack. 

## Prerequisites

Few things you need in advance to do this Pulumi deployment.

1. [Pulumi account](https://app.pulumi.com/)
2. [Pulumi CLI](https://www.pulumi.com/docs/get-started/install/)
3. Pulumi Deployment preview added
4. Python 3.9 or higher
5. AWS, Azure, or Google Cloud account
6. AWS, Azure, or Google Cloud CLI
7. GitHub account


## Create a project

- First, create a project in the Pulumi service console. Go to [app.pulumi.com](app.pulumi.com) and log in. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668869758801/uaIq44pw5.png align="center")

- Select **Stacks** in the left navigation and click **Create Project**. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668869867511/-6MeRZCRX.png align="center")

- Then choose the cloud you want to use, the language, and the template you want to use. Choose one of the other models from Starter. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668869984340/kcZ44VTt9.png align="center")

 - Select **Next** and specify in the project details: project name, stack name, and configuration values ​​for the model. 


![1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668870209467/5zGVsUJ6B.png align="center")

- Selecting **Create Project** takes you to the New Stack Overview page.


![2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668870312575/M0wsJF0xD.png align="center")

## Pull Your Project Locally

- Follow the getting started instructions on the new stack overview page.


![3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668871427798/A7R15pUop.png align="center")

- Create a new folder for your project in the CLI, then pull the github project. Don't run `pulumi up`. 

```
mkdir deployment && cd deployment
pulumi new aws-python -s MakendranG/deployment/dev
```
**NOTE**

*MakendranG/deployment/dev - You need to update with your project details.*


- Then create a git repository in your project directory and push it to GitHub. Execute the below command one by one.

```
ls
code __main__.py
git init
git add .
git commit -m "First commit"
git branch -M main
git remote add origin https://github.com/MakendranG/Pulumi_Challenge.git
git push -u origin main
```

**NOTE**

*git remote add origin **https://github.com/MakendranG/Pulumi_Challenge.git** - Update your github repository*


## Deploy by installing Pulumi Push

- Return to the Pulumi service console, select the **Settings** tab, then select **Deploy**. To enable the Pulumi deployments, first install the Pulumi GitHub. 


![4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668873399219/2m-ZrAPSt.png align="center")


- After installation, you will be prompted for deployment options. Select the organization/GitHub repository, branch, and directory you want to join. Scroll down to Environment Variables and provide your cloud credentials (e.g., AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_SESSION_TOKEN for AWS).


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668873723513/UhNawjg4F.png align="center")

## Deploying the stack using Pulumi Deployments

- To start the deployment, select the **Actions** button, then select **Update** and **Deploy**. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668874026517/F4BuZ853R.png align="center")


- Go to the **Actions** tab. Selecting a new deployment will display the deployment log with details about the deployment.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668874110884/gPFK5_3zp.png align="center")

## Endpoint verification

Finally, verify that the deployed infrastructure endpoints are working. You can copy the endpoint URL from the output section of the deployment log.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668874165020/JAwvnJtvq.png align="center")


# Conclusion

You have completed the Pulumi Challenge. Run `pulumi destroy -y` to remove all these resources. Otherwise, you can play with your own infrastructure! Just add what you want and change the git repo to Pulumi Deployments and a new deployment will start. 


Gratitude for perusing my article till the end. I hope you realized something unique today. If you enjoyed this article, then please share with your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)









