## Learn How to Deploy Website Using Hugo on AWS Amplify in Ten Minutes



In this post, you'll learn how to set up and deploy a website using **Hugo** (AWS Cloud9's Integrated Development Environment (IDE) for content management), **AWS CodeCommit** for source code management, and **AWS Amplify** for serving source-based websites, automated deployment process.




# Configuring the AWS Cloud9 IDE

Start by provisioning the AWS Cloud9 IDE. 

> The **AWS Cloud9** environment is based on Amazon Elastic Compute Cloud. You must provision an AWS Cloud9 environment in a public subnet in an Amazon Virtual Private Cloud in your AWS account.

This can be done with the following steps:

- Sign in to your AWS account with credentials that have administrator privileges. If you don't have an AWS account, you can create one.

- Open the Cloud9 console and Click **Create Environment**.


![19090126.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663568835621/5LnIHVWkI.png align="left")

- Use the wizard in the AWS Cloud9 console to create a new AWS Cloud9 environment.

- Enter a name for your desktop and an additional description.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663569095003/bkcmtbMZ2.png align="center")

- Choose **Next Step**.

- In the Environment Settings section, under Environment type, choose **Create a new environment EC2 instance (direct access)**. 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663569447695/hKvHjOjHb.png align="center")


- For Instance Type, choose the desired instance type.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663569468444/bnOe9NbW1.png align="center")

- For Network, under Network Settings (VPC), choose the VPC that will host your AWS Cloud9 instance. 

- Choose the public subnet of this VPC to deploy. 

- Leave all other settings unchanged and select **Next Step**. 

- Review the selections and choose **Create Environment**. It takes a few minutes to set up the environment. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663569600664/KOL3Ar7mp.png align="center")

- When your environment is ready, you can access the AWS Cloud9 IDE from your browser. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663569776888/QolaiMgq3.png align="center")

# Configure the source code repository to track content changes

> Use AWS CodeCommit, a fully managed resource management service that hosts secure Git-based repositories.

- Open the CodeCommit console in a new browser and create a new repository.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663569909534/QKjfr8Fxz.png align="center")


- In Repository Name, enter **amplify-website**. 

- Enter an appropriate description.

- Choose **Create**. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663570096006/h8gH8mdWk.png align="center")


It takes a few minutes to create the repository.



# Set up and deploy a sample website


- In the AWS Cloud9 IDE, return to your browser and place your cursor in the lower terminal window of the IDE.

- Enter the following code to download and unzip the existing example website saved as a .zip file.

```
cd ~/environment
aws s3 cp s3://ee-assets-prod-us-east-1/modules/3c5ba9cb6ff44465b96993d210f67147/v1/example-website.zip ~/environment/example-website.zip
unzip example-website.zip
rm example-website.zip
```
The following screenshot shows the result.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663574702884/3VTY8iphS.png align="center")

- Then run the command to create a directory to host and start the website by copying the files from the example website. 

```
mkdir ~/environment/amplify-website/
cd ~/environment/amplify-website/
```

- Next, create a new default branch on your AWS Cloud9 instance called local master. Then copy the files from the example website. 

```
git init
git remote add origin codecommit::us-east-1://amplify-website
git remote -v
git checkout -b main
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575127447/HHRxmH0fM.png align="center")

- Adding and committing locally commits all changes to the remote Amazon Codecommit repository. 


```
cp -rp ~/environment/example-website/* ~/environment/amplify-website/
git add *
git commit -am "first commit"
git push -u origin main
```


- In the Amplify console, Choose **Get Started**. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575371651/OfTkNBa1n.png align="center")

- Choose **Amplify Hosting** and Click Get Started.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575426834/3So7_4kG5.png align="center")

- On the Getting Started with Amplify Console page, choose *AWS CodeCommit* as your source code repository. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575485228/Wq2xxmykC.png align="center")

- Select Continue. 

- On the Add Repository Branch page, select the repository for the recently updated repository. 
- For Branch, select Main. 
- Choose Next. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575546059/8s7Fqzqec.png align="left")


- Choose Next.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575634748/Nnctp1Z6u.png align="left")

- On the review page, choose **Save and Deploy**.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575655692/cZ0KBwzu2.png align="left")

Amplify builds and deploys your Amplify site in minutes and shows you the progress.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575736601/I5eSDhRwX.png align="left")

After the implementation is complete, you can visit our website to see sample content.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575847254/myRrg37_s.png align="left")

The following screenshot shows an example website. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575864100/FU1k0-2bQ.png align="left")


# Performing Changes to the website

You can now update the text string on the home page and commit and publish this change.

- In the AWS Cloud9 IDE, return to your browser and place your cursor in the lower terminal window of the IDE.

- In the navigation pane, choose `~/environment/amplify-website/workshop/content/_index.en.md`.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663575959586/o1MLtwFcP.png align="left")

The contents of the file will open in a new tab in the top panel. 

- Change the **LARGE TITLE** to **Makendran Docs**.

- Save the changes to `_index.en.md` by choosing **Save** from the File menu. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663576185341/_6lkurdPo.png align="left")

- In AWS Cloud9, run the following command in the lower terminal window to commit the changes.

```
git add *; git commit -am "homepage update"; git push origin main
```

- Return to the Amplify console to see how automatically detects changes. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663576280241/ug2-VegJ3.png align="left")

Amplify walks you through the steps to make changes to your website.


- After this update is complete, visit the website URL to see if the LARGE TITLE on the home page has changed.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663576506429/51TcWT95W.png align="left")

You can repeat this process to make automatic, source-based changes to your website.


# Add a custom domain

By adding custom domains to your Amplify setup, your customers can easily access your content. You can register new domains through **Amazon Route 53**, or if you have domains registered outside of AWS, you can integrate with Route 53 and Amplify. 

For our use, the domain *www.makendran.study* is a domain name registered by a third party registrar. Route 53 allows you to manage DNS configuration for domains registered outside of AWS.

## Start by setting up a public zone on Route 53. 

- In the Route 53 console, choose hosted zone. 

- Choose **Create Hosted Zone**. 

- Enter `makendran.study` as the domain name. 

- Enter an appropriate description.

- Under Type, select **Public Hosted zone**. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663576942438/zxubBqu7K.png align="left")

- Choose **Create Hosted Zone**.

- Save the addresses of name servers that respond to clients DNS lookups for your domain. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663577456287/EWEbgi1ms.png align="left")

- In a separate browser, access the DNS registrar console. 

- Configure custom DNS name server settings in the remote domain name registration console. This configuration points to the Route 53 destination name servers as the authoritative DNS for your custom domain. For this purpose, this change notice may take up to 48 hours. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663577526489/CDEpIS6Wn.png align="left")

- Use https://who.is to verify that your AWS nameservers are listed correctly for your custom Internet client domain. 


You can now set up custom domains in Amplify. 

> Amplify allows you to configure DNS and configure SSL for any custom domain you want.




- In the Amplify console, under **App Settings**, select **Domain Management**. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663577695040/I0cakdQuv.png align="left")


- Choose **Add domain**. 


- Enter a custom domain name for your domain (*makendran.study*). 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663577744158/XpzNNBhcn.png align="left")

- Choose **Configure Domain**. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663577849742/vVQJ54ms4.png align="left")


- For subdomain, set www and choose to exclude custom domain root. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663577951834/GNou5--Xz.png align="left")


- Choose Save. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663577964200/bMx7nSbc8.png align="left")


Amplify starts the SSL certificate creation process. After a while, you'll be taken to your SSL configuration and see a domain verification in progress.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663578128796/WS_0C4hUM.png align="left")


Amplify verifies domain ownership by creating an example CNAME record in the host zone file. Once ownership is verified, your domain is deployed to Amazon CloudFront distributions managed by Amplify and domain activation is complete.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663580384406/ZKe53cMpr.png align="left")

Customers can now access the website with a custom domain name *www.makendran.study*. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663580437684/hm5UcxggB.png align="left")

# Setting up a subdomain for development

To align with CodeCommit's development code branch, Amplify creates a development website so you can test changes before they go into production.

- Go to the AWS Cloud9 IDE and type the following command to create a **development branch** using the terminal.

```
git checkout -b development
git branch
git remote -v
```

- Modify a content to push the changes to CodeCommit using the current content from the master branch.


```
git add *; git commit -am "first development commit";
git push -u origin development
```

- Open and edit the file `~/environment/amplify-website/workshop/content/_index.en.md` and change the update path for the website to something else. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663578492982/kyzzCLDe9.png align="left")

- Capture and push the changes with the following code.

```
git add *; git commit -am "second development commit"; git push -u origin development
```

- Go back to the amplify-website app. 

- Select **Connect Branch**. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663578622194/PhlZJBD30.png align="left")

- For Branch, select the development branch you created. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663578641811/gB_Rj0r9o.png align="left")

- Choose Next and Click **Save and Deploy**.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663578685351/xd7NfyhlT.png align="left")

Amplify will create a second website based on the content of the development branch. In the Amplify console, you can view instances of your website that correspond to the development code tree. 


![19090412.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663578749261/upRsLNU3I.png align="left")


- In Amplify, access the **Domain Management** menu item to add a custom subdomain. 

- Edit the domain and add a subdomain entry with the desired name. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663579008152/-TkkvYyTo.png align="left")

- Commit to the development branch with committed code and content changes. 

- Choose **Update**.


![19090442.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663580556852/gH0o1vQ1C.png align="left")




# Control access to development

New content is hosted on the development site, so you can restrict access. 

1. In the Amplify console, select **Applications**. 

2. Select **Access Control**. 


![19090444.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663580696423/rz5wxTX_e.png align="left")


3. Under Access control settings, select the desired settings. You have the option to restrict access globally or per site. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663580802419/5dxyZumGQ.png align="left")


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663580866835/AuE_rp85V.png align="left")

# Cleaning Up

1. Select the application you created in the Amplify console and Select **Delete App** from the Actions drop-down menu.

2. In the CodeCommit dashboard, choose the repository you created and Choose **Delete**.

3. Select the IDE you created in the AWS Cloud9 dashboard and Choose **Delete**.


# Conclusion

Hugo is a powerful tool for quickly delivering content in a variety of formats, including image portfolios, online resume presentations, blogs, and technical articles. Amplify Console offers a convenient, easy-to-use static web hosting service that dramatically speeds up the delivery of static content. Hugo and Amplify Console work together to quickly deploy a website in minutes with features like easy-to-use URLs, code-level experiences, and encryption (SSL). 

# Reference Article

1. [Welcome to AWS Amplify Hosting](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)
2. [Hugo](https://gohugo.io/)
3. [How do I create and activate a new AWS account?](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/)
5. [Amazon Route 53](https://aws.amazon.com/route53/)
6. [Hosting a static website using Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
7. [NGINX Plus on AWS](https://aws.amazon.com/quickstart/architecture/nginx-plus/)
8. [AWS CloudFormation](https://aws.amazon.com/cloudformation/)
9. [MkDocs](https://www.mkdocs.org/)
10. [AWS Cloud9](https://aws.amazon.com/cloud9/)
11. [AWS CodeCommit](https://aws.amazon.com/codecommit/)
12. [Amazon S3](https://aws.amazon.com/s3/)
13. [Agile website delivery with Hugo and AWS Amplify](https://aws.amazon.com/blogs/devops/agile-website-delivery-with-hugo-and-aws-amplify/)









