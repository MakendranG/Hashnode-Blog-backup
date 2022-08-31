## Nhost: The Perfect Backend 101: The Essential Guide

## Introduction to Nhost


Nhost is the GraphQL open source development and backend platform. Nhost does for the backend, what Netlify and Vercel do for the frontend. Nhost provide a modern backend with the common building blocks needed to create great digital products.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661160260372/Pc7-xqQSc.png align="left")

It simplify the creation and deployment of the backend by using nhost platform that takes care of configuration, security and performance. Things work and automatically scale so you can focus on your product and business. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661160312157/6kFU0kvZZ.png align="left")

## Architecture

Nhost is a backend service built with open source tools to provide developers with the common building blocks needed to create great apps and digital products.

Here is a high-level diagram of the Nhost stack:

[![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661152883288/w_O08UHEl.png align="left")](https://docs.nhost.io/platform/overview/architecture)


As you can see in the image above, Nhost provides endpoints for:

- GraphQL (/ graphql)
- Authentication (/ auth)
- Archiving (/ archiving)
- Functions (/ functions)

The data is stored in Postgres and the files are stored in S3.

## Open source

The open source tools used for the entire Nhost stack are:

- Database: Postgres
- GraphQL: Hasura
- Authentication: Hasura Auth
- Storage: Hasura storage
- Features: Node.js


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661160342840/m18-7EyaN.png align="left")

## Introduction to the Nhost command line interface

The Nhost command line interface (CLI) allows you to locally run a complete Nhost development environment with the following services: 

- PostgreSQL database
- Hasura
- authentication
- Archiving
- Serverless functions
- e-mail

### Installation

- Install the binary globally. To install Nhost CLI, run this command from any directory in your terminal:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661154560447/KZ90iuUvf.png align="left")





![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661155081790/HdcqemoaW.png align="left")

On MacOS and Linux, this installs the Nhost CLI in / usr / local / bin. If you prefer to install in a location other than / usr / local / bin, set the INSTALL_PATH variable accordingly:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661154640689/1U4RrCvJC.png align="left")


On Windows, this downloads and extracts the nhost.exe binary available in Assets from the latest version from the GitHub release page: https://github.com/nhost/cli/releases. 

You can move the executable to another location and add the path to the PATH environment variable to make nhost globally accessible.

Finally, you can verify that everything installed successfully by typing:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661154676744/lweSyCqg8.png align="left")


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661155135534/wz5bTDpRf.png align="left")






## Requirements

Before using the Nhost CLI, make sure the following dependencies are installed on your local computer:

1. Git
2. Docker

### Access to the Nhost CLI

- After installing Nhost CLI, you can log into your Nhost account by running the following command:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661155735704/6DPei0YPh.png align="left")


This will ask you to enter your Nhost account information (email / password). After successfully logging in, you are authorized to manage your Nhost projects using the Nhost CLI.

- You can also logout at any time by doing the following:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661155758569/AjrC5-I-K.png align="left")

## Configure your project

### Create a new Nhost project
First of all, we need to create a new Nhost project.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661155533069/qDau5YWhr.png align="left")

Then log into the Nhost dashboard and click the Create your first project button. Then, name your new Nhost project, select a geographic region for your Nhost services, and click **Create Project**.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661155877219/y5vpG62Yc.png align="left")

After a few seconds you should get a PostgreSQL database, GraphQL API with Hasura, file storage and authentication.

### Create a new GitHub repository

A typical workflow also involves creating a Github repository for your Nhost project. It will simplify your development workflow as Nhost can integrate with Github to enable continuous deployment. 

Then go to your Github account and create a new repository. You can make your repository public or private.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661156040412/dJtQcGhsK.png align="left")

### Connect the Nhost project to Github

- Finally, connect your GitHub repository to your Nhost project. This will allow Nhost to deploy new versions of your project when you push new commits to your connected Git repository. From your project workspace, click Connect to GitHub.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661156112870/ugNpsmFxA.png align="left")

- Install the Nhost app on your GitHub account.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661156170862/PI47nIBeN.png align="left")

- Connect your GitHub repository.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661156258522/J-8zjTKPb.png align="left")

## Local development

### Initialize your Nhost project

Nhost CLI brings the functionality of your Nhost production environment directly to your local computer. It deploys Docker containers to run backend services that match your production environment in an on-premises environment. This allows you to make changes and test your code locally before deploying those changes to production.

Initialize your Nhost project locally with the following command:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661156493470/pY8fQFF5u.png align="left")


Finally, be sure to link your current working directory to your GitHub repository:

```
echo "# my-nhost-app" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/makendrang/my-nhost-app.git
git push -u origin main
```


### Start a local development environment

Run the following command to start a local development environment for your Nhost project:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661156935462/V-cNlCqvV.png align="left")

Running this command will start all core services provided by Nhost. It also runs a web server to serve the Hasura console for the GraphQL engine, allowing you to manage the database and test the GraphQL API.

Hasura console will automatically open at http: // localhost: 1337.

### Make changes

There are three things that the Nhost CLI and GitHub integration follow and apply to production:

- Database migrations
- Hasura metadata
- Serverless functionality

## Demo 

Below are the steps required to create a simple Nhost-based React app for the backend. 
It Contains:

- Database: PostgreSQL
- Snapshot GraphQL API: Hasura
- Authentication: Hasura Auth
- Storage: Hasura storage

At the end of this demo, you will have a full-stack app that allows users to log in to access a secure dashboard and update their profile information.

### Requirements

Before we begin, we make sure your development environment is ready.

You need Node.js version 14 or later

### Project configuration

- [Create a new Nhost project](https://makendran.hashnode.dev/nhost-the-perfect-backend-101-the-essential-guide#heading-create-a-new-nhost-project)




### Initialize the application

#### Create a React app

The easiest way to create a new react app is to use the tool called **create-react-app** which will start a react app for you without you having to configure everything yourself.

Then open your terminal and run the following command:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661162664931/lfp6Lgecg.png align="left")

You can now switch to your project directory:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661162681502/8_UAXLwOH.png align="left")

Run the development server with the following command:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661162694928/C5um2ML_l.png align="left")

If everything is working fine, your React dev server should be running on port 3000. Open http://localhost:3000 in your browser to check this. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661160465958/AMDjrjjGf.png align="left")


#### Configure Nhost with React

To work with Nhost from within our React app, we will use the React SDK provided by Nhost. It's a wrapper around the Nhost JavaScript SDK that gives us a way to interact with our Nhost backend using react hooks.

You can install the Nhost React SDK with:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661162758691/sX4jAN2e5.png align="left")

Next, open your App.js file as we will now configure Nhost in our app.

The Nhost React SDK includes a React provider called **NhostReactProvider** that exposes the authentication state and any provided React hooks in our application.

Use the following code to instantiate a new nhost client and link it to your nhost backend:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661162833549/W-MSVpVmk.png align="left")


Finally, make sure you create an environment variable called **REACT_APP_NHOST_SUBDOMAIN** and **REACT_APP_NHOST_REGION** to store your nhost domain details:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661162864304/ractr8akd.png align="left")

You can find the subdomain and region of your Nhost project in the project overview:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661162905818/UxqURaFFo.png align="left")

### Build the application

#### Add authentication

##### **Sign-up**

The next step is to allow our users to authenticate with our application. Let's start implementing the login process.

To do this, we use the **useSignUpEmailPassword** hook provided by the Nhost React SDK in our SignUp component.

So open the corresponding file of your project and use the following code:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661162987064/1aV8cj7_6.png align="left")



By default, the user must verify their email address before fully signing up. You can change this setting in your Nhost dashboard. 

##### **Sign-in**

Now that new users can register for our application, let's see how to authorize existing users to log in with an email address and password.

To do this, we use the nhost hook called **useSignInEmailPassword** in our SignIn component the same way we did in our SignUp component. This is what your component should look like after applying the login logic changes:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163053683/1LITmCIfJ.png align="left")

##### **Sign-out**

Finally, to allow users to sign out of the application, we can use the Nhost **useSignOut** hook:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163101776/LcLjRDTrU.png align="left")

#### Protect routes

Now that we've implemented authentication, we can easily decide who can access certain parts of our application. In our case, we only allow authenticated users to access the `/` and `/ profile` paths. All other users should be redirected to the `/ sign-in page` if they attempt to access such locations.

To do this, we can create a wrapper component (`ProtectedRoute`) to check the authentication status of the current user using Nhost SDK:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163162401/-NnJWzUn-.png align="left")

Then we can use a layout path in our App.js file to wrap the ProtectedRoute component around the paths we want to protect:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163183149/1hog_V6YJ.png align="left")

#### Retrieve user data

Finally, we show the information of the verified user on their dashboard to make the app more personal.

Getting the current verified user data is quite simple. In fact, we can use the useUserData hook provided by Nhost to do this. So open the **component / layout.js** file and use this socket like:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163229702/4mHQiVsEA.png align="left")

That's it! The JSX code for rendering user data (E -Mail, advertising name, etc.) is already included in your components as part of the model you designed at the start of this manual.

#### User data update

Nhost offers a graphql -Api via Hasura so that we can immediately query and mutate our data.

We use the Apollo Graphql client for interaction with this graphql -Api.

So start to install the following dependencies:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163304470/1ozTeakg4.png align="left")

Then add the nhostapollophovider of @ nhost / react-Apollo to your app.js.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163337286/XPGIma3Sj.png align="left")



From there, we can create our graphql request and use the Apollo Usemutation hook to make this request if the user submits the form on the profile page:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163356449/rEnUPrm39.png align="left")

Finally, since Hasura authorizes a standard directive and we have not yet defined any authorization, our Graphql changes would fail. So, open the Hasura console from your project's "Data" tab in your Nhost dashboard. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661161878474/HXz9Y-vtg.png align="left")

Next, go to the Permissions tab of the users table, enter the user in the role cell and click the edit icon on the select operation:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661161866776/Go-Bi1nGU.png align="left")

To restrict the user to reading their own data only, specify a condition with the user ID and session variable X-Hasura-User-ID passed with each request.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661161918370/hh8_V9Cs7.png align="left")



Next, select the columns you want users to have access to and click Save Permissions.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661161963790/riFcPn5il.png align="left")


Repeat the same steps for the user role update process to allow users to update only their display name and metadata.




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661161988831/NMW__8k3U.png align="left")





Finally, to add caching, synchronization, and server state updating into your React application, let's instead refactor user data retrieval using the Apollo client and our GraphQL API. 

Then first add the following GraphQL query to get the current user data from the layout component:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163418415/6eTr0YvGg.png align="left")

Then replace the useUserData hook with the useUserId hook to get the current user ID.




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163437024/HDF3B8UGD.png align="left")
Finally, we can execute our GraphQL query using the useQuery hook and the current user ID.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661163459197/1NJJ_4wj-.png align="left")

You now have a fully functional React application. Congratulations!


Gratitude for perusing my article till end. I hope you realized something unique today. If you enjoyed this article then please share to your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.


Follow me and share your thoughts,
[GitHub](https://github.com/MakendranG)
[LinkedIn](https://www.linkedin.com/in/makendran/)
[Twitter](https://twitter.com/MakendranG)















