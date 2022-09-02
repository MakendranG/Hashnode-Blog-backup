## A Fascinating Behind-the-Scenes Look at How I Built a Harness CI Pipeline

In this blog, I am sharing my learning that are gained from the **Full Stack Testing and GitOps Workshop**.


This workshop is really useful for those who want to learn the steps required to implement an application, setup CI/CD pipelines and implement a Full Stack testing solution. It was a great opportunity to participate in the Full Stack Testing and GitOps Workshop hosted by the **Konfhub Tech** in collaboration with **Harness**.


**Speaker of the session:** Jaap Brasser, Sr. Developer Advocate at Harness


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662128749470/WwNyg3lDW.png align="center")

During the workshop, I learned the below mentioned topics.

## What is a MERN stack?


![MERN-stack-1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662127654127/x-jMtxLS6.png align="center")

*[Image Source](https://www.bocasay.com/how-does-the-mern-stack-work/)*

The MERN stack enables faster application development. The technology is used worldwide, and the MERN stack is primarily used to develop fully JavaScript-based applications. MERN stands for MongoDB, Express, React, and Node, and is based on the four core technologies that make up the stack.

- MongoDB: A document database
- Express(.js): Web Framework
- React(.js): A client-side JavaScript framework
- Node (.js): JavaScript web server

All four are included in the stack because of the four JS-based technologies. So if you're familiar with JavaScript (and JSON), you can run the frontend, backend, and database separately or together.

## CI Concepts

### What's wrong with CI today?


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662128120203/9Opbc3yaC.png align="center")

- Visibility
- Difficulties in Troubleshooting
- Length build Cycles
- Overhead in Maintaining CI
- Difficulty onboarding
- Hard to Promote Best Practices

### Harness CI Core Concepts


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662128232837/gBh4Y7H5J.png align="center")

- Agnostic
- Containerized
- Scalable
- Developer Friendly
- Fine-Grained RBAC
- Secrets Management

## Exercise - How to create a Harness CI Pipeline for the MERN Stack App

In this tutorial, we will create a CI pipeline for our stack of MERN application. The application code is in [harness-apps/MERN-Stack-Example](https://github.com/harness-apps/MERN-Stack-Example) repository.

### Pre-requisites

- Harness account -> Create an account at https://app.harness.io
- GitHub account -> Create an account at https://github.com
- Docker Hub account -> Create an account at https://hub.docker.com


### Create a CI pipeline

- Open https://app.harness.io, select and click on the **Continuous Integration module** and click **Continue**.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662130259732/N6I4J-P9n.png align="center")


- Click **Create a Pipeline**.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662129504842/X2-_Alwwz.png align="center")

- Wait for your environment to be provisioned.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662130400949/HrsLSlcZz.png align="center")

- Harness requires a [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) to access the GitHub repository. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662129740122/ByUWfl12U.png align="center")

- Kindly refer [GitHub connector documentation](https://docs.harness.io/article/jd77qvieuw-add-a-git-hub-connector#step_3_credentials) for generating token. Need to select repo, admin:repo_hook and user scope while generating token.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662130048782/AM9bA04KZ.png align="center")

- Select **GitHub**, enter your personal GitHub access token in the Access Token field.


![0827.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662130661070/_GsGtt12K.png align="center")

- Fork the [harness-apps/MERN-Stack-Example](https://github.com/harness-apps/MERN-Stack-Example) repository into your GitHub account.


![0834.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662131089832/tETxfdYoO.png align="center")

- Click **Test Connection**. Wait for the connection success message to appear, then click Next: Select Repository.


![0830.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662130866676/vMKCHz-sP.png align="center")

- Type "MERN" in the search bar and MERN-Stack-Example will appear in the list. Select the repository and click **Create Pipeline**.


![0839.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662131383509/9rYQCtT89.png align="center")

- Pipeline will be created.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662131475385/iB63UIWQF.png align="center")

- Click the Execution tab, then click **Add Step**.



![0846.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662131793055/7BgtwLePc.png align="center")

- Select the **Run** step.


![0847.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662131864170/AjT-_6Cs6.png align="center")

- Enter “Test MERN Server” in the Name field, then click in the **Container Registry** field.


![0849.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662131960433/fbw23aL_7.png align="center")

- Click New Connector.


![0850.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132024120/7IwODI14h.png align="center")

- Click **Docker Registry**.



![0851.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132077682/pxvkSEaub.png align="center")


- Enter “Docker Hub” in the Name field, then click Continue.


![0852.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132141795/rTjcdcQEs.png align="center")

- Enter "https://index.docker.io/v1/" in the Docker Registry URL field and enter your Docker Hub username in the Username field and then click **Create or choose Secret**. 


![0854.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132256008/qxR_-suh1.png align="center")

- Click **New Secret Text**.


![0855.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132317836/ge1Cg2IpE.png align="center")

- Harness needs a Docker Hub access token to pull Docker images. See Docker Hub’s [Manage 
access tokens documentation](https://docs.docker.com/docker-hub/access-tokens/) to learn how to create an access token. 


![0859.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132619085/VRJrsQcYJ.png align="center")

- The token must have Read, Write and Delete permissions.


![0901.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132679404/SB5XK-H5F.png align="center")


- Enter “Docker Hub Token” in the Secret Name field and enter your Docker Hub access token in the Secret Value field, then click Save.


![0902.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132773503/pDRY8g2D1.png align="center")

- Verify that Docker Hub Token appears in the Password field, then click **Continue**.


![0904.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132858652/EPrnyrlol.png align="center")

- Select **Connect through a Harness Delegate**, then click **Save and Continue**.


![0905.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662132930556/Z3W5dPqvY.png align="center")

- At the Delegate Setup step, click Save and Continue.


![0907.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133036598/PPhGduXoX.png align="center")

- A connection test will run, wait for it to complete, then click **Finish**.


![0908.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133095995/I95xLSrkn.png align="center")

- Select the Docker Hub connector you just created, then click **Apply Selected**.


![0909.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133162226/LIiPaSshz.png align="center")

- Verify that Docker Hub appears in the Container Registry field. Enter “node:16” in the Image field. Enter the below commands in the Command field:

```
cd server 
yarn install 
yarn test
```
- Click Apply Changes.


![09011.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133327059/7Oxako-wD.png align="center")

### Run CI Pipeline

- Back in the pipeline view, click **Save**




![0913.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133644519/9JRa0nzC4.png align="center")

- Then click **Run**.


![0916.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133653053/HkFksBLRa.png align="center")

- For Build Type select **Git Branch**. Enter “main” in the Branch Name field, then click **Run Pipeline**.


![0919.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133755050/-xyNXMFWr.png align="center")

- Your Harness CI pipeline will now execute.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133930027/skP4cB8hI.png align="center")


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133873027/PfF6DppYU.png align="center")


- Examine the Test MERN Server log output.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662133983343/IM5DqsGB1.png align="center")


> You just built your first Harness CI pipeline! Great job! With Harness CI, you can easily set up pipelines (using the graphical interface or as-code), connect them to your Git/artifact repo, and start building and testing!


## Reference Article

1. [Full Stack Testing and GitOps Workshop](https://www.youtube.com/watch?v=eM6iVTp9LV8)
2. [Building a Full Stack CI/CD Pipeline](https://www.youtube.com/watch?v=sQuIhkDJRIw&t=4467s)
3. [Official Page of Harness](https://harness.io/)
4. [CI Pipeline Basics](https://docs.harness.io/article/3amcd8hn53-ci-pipeline-basics)
5. [CI/CD Pipeline: Everything You Need to Know](https://harness.io/blog/ci-cd-pipeline)
6. [Harness Platform Solutions: Getting Started with Integrating Drone CI with Harness CD](https://university.harness.io/ci-pipeline-cd)


Gratitude for perusing my article till end. I hope you realized something unique today. If you enjoyed this article then please share to your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)










