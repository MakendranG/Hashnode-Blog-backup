## Everything You Need to Know About Insights From the AZ-104 Bootcamp Session - Week 3

In this blog, I am sharing my learning that are gained from the Week-3 of AZ-104: Microsoft `Azure Administrator Bootcamp`.


This boot camp is really useful for those who want to pass the AZ-104 exam.  It was a great opportunity  to participate in the Microsoft Azure AZ-104 Bootcamp hosted by the `Azure Developer Community` in collaboration with `Whizlabs` and `Reskill`.


The Microsoft Azure AZ-104 certification is an administrator-level certification that measures our ability to perform the following technical tasks: 

- Manage Azure IDs and governance. 
- Implement and manage storage. 
- Deploy and manage Azure compute resources. 
- Configure and manage virtual networks. 
- Monitor and protect Azure resources. 

**Speaker of the session**: Samik Roy ( Lead Cloud Developer in Open Systems| Community Speaker & Contributor| Helping Customer to use Microsoft Sentinel At Scale| Love to tell stories with data)



![az1041](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vq65tbdqcbk2tdmtrv7j.png)
 
 

During the third bootcamp session, I learned the below mentioned topics.

## Configure storage accounts



![badge1](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y4kn1e3bx3x53rxfyvfe.png)
 

I have learnt: 

1. Identifying the capabilities and use cases of Azure storage account. 
2. Choosing from different types of storage and storage accounts. 
3. Selecting a storage replication strategy. 
4. Configuring network access to storage account. 
5. Protecting the storage endpoint.
6. Demo








## Configure blob storage


![badge 2](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qo69sqwxf3x08mbu6ymo.png)
 

I have learnt: 

1. Identify the features and use cases of Azure Blob Storage. 
2. Configuring blob storage and blob access levels. 
3. Configuring blob lifecycle management rules. 
4. Configuring blob object replication. 
5. Blob storage upload and pricing.
6. Demo







## Configure storage security


![badge 3](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4phnvdm75n2l2albwvvj.png)
 


I have learnt: 

1. Configuring a shared access signature that includes URI and SAS parameters. 
2. Configuring storage service encryption. 
3. Implement customer management keys. 
4. Ways to improve storage security.
5. Demo









## Configure Azure files and Azure File Sync

![badge 4](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jtld2kjmq2850muax6z9.png)
 

I have learnt: 

1. Identifying when to use Azure files and Azure Blobs.  
2. Configuring Azure file shares and file share snapshots.  
3. Identifying the features and use cases of Azure FileSync. 
4. Identifying the file synchronization component and configuration steps. 
5. Demo






## Configure storage with tools

![badge 5](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o0okl2srfvvf9jplx079.png)
 


I have learnt: 


1. Configuring and using Storage Explorer.  
2. Configuring the Import and Export Service.  
3. Configuring and use AZCopy.
4. Demo



At the end of the session, We have Q & A where I have cleared doubts. Speaker also recommended to take microsoft learn courses to gain more knowledge.

![youtube image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/86o7vkh1leoebt648083.png)
 
 

To learn more about the topics, I have taken the [Microsoft Learning modules](https://docs.microsoft.com/en-us/learn/paths/az-104-manage-storage/) and successfully completed as well. Every module is having a knowledge check where we can validate our learning as well.

![total image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vp200gq0qo9qduno0cxy.png)
 


In Microsoft Learn courses, they are giving sandbox account where we can do azure exercises to get more familiar with the services. PFB are the sandbox modules.

![Sandbox](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o1ff1v8diww5k3yhfb4u.png)




       



## Exercise: Hosting a static website with blob storage 

This tutorial shows you how to create and deploy a static website in Azure Storage. When complete, it creates a static website that users can access to the public. 

In this tutorial, you will learn how to: 

1. Configure static website hosting 
2. Deploy the sample website 

## Requirements 

1. You need an Azure subscription to access Azure Storage. If you don't  have a subscription yet, create a free account before you start. 
2. Storage Account

## Configure static website hosting 

1. The first step is to configure your storage account to host your static website in the Azure portal. 
2. When you configure your account to host a static website, Azure Storage automatically creates a container named **$web**. 
3. The $web container contains files for  static websites. 
4. Open the Azure portal in your web browser. 
5. Find the storage account and view the account summary. 
6. Select **Static Website** to display the static website configuration page. 
7. Select **Enabled** to enable static website hosting for your storage account. 
8. In the **Index Document Name** field, specify the default index page for `index.html`. When a user navigates to the root of a static website, the default index page is displayed. 
9. In the **Error Document Path** field, specify the default error page  `404.html`. When a user tries to navigate to a page that does not exist on a static website, a standard error page is displayed. 
10. Click **Save**. You should now see your static website endpoint in the Azure portal.

![static site](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bvq437xgfgk2zjqsagqj.png)

## Deploy the file to the container

- Create a default index file and name it index.html.  
- Open index.html in Notepad, paste the following text into a file and save. 

```
<!DOCTYPE html>
<html>
  <body>
    <h1>Welcome to AZ-104 BootCamp session - Day 3!</h1>
  </body>
</html>
```
- Create a standard error file and name it 404.html. 
- Open 404.html in Notepad, paste the following text into a file and save.

```
<!DOCTYPE html>
<html>
  <body>
    <h1>404</h1>
  </body>
</html>
```
- Upload both the files to the $ web container.

![upload](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/v0irgdguhpdb1i6keqam.png)
 
- Launch the website and view it in Azure. 

![Site](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j14s89pgvzg0uaykxjst.png)
 

The tutorial completed successfully and the  static website was deployed to Azure.
 

Link to Register for the bootcamp: https://azdev.reskilll.com/event/Az104~doon

Gratitude for perusing my article till end. I hope you realized something unique today. If you enjoyed this article then please share to your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)
