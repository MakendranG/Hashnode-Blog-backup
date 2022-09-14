## Learn Getting Started With Digitalocean Functions in Ten Minutes

In this blog, I am sharing the learning that is gained from the session **Getting Started with Digital Ocean Functions**.

This session is really useful for those who want to learn about serverless concepts, FaaS, Serverless architecture, and implementing a cloud function in the digital ocean. It was a great opportunity to participate in the Getting Started with Digital Ocean Functions Session hosted by **Machine Learning Hacking** in collaboration with **Digital Ocean**.

**Speaker of the session:** Amy Negrette, Developer Advocate at Digital Ocean


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663145904978/fXjegaeIG.png align="center")

During the workshop, I learned the below-mentioned topics.

# What is serverless?


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663146041828/c-zJMCV1r.png align="center")

# What is FaaS?



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663146136378/8Sz2usqG1.png align="center")

# Advantages of FaaS





There are many advantages to using a FaaS architecture. Here are some reasons to use FaaS for our application:



- Ability to focus solely on coding and application development
- Save money by only paying for what we use
- The ability to automatically scale without capacity planning or ongoing maintenance
- Reduce time to market with easy development and testing

# Serverless Architecture


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663146298692/B9VW03QD-.png align="center")

Serverless architecture allows us to deploy server-based web services on demand. We can reduce our overhead by designing our software for a serverless provider instead of maintaining our own server setup. Serverless applications are typically hosted in **Git repositories in an environment** that can scale up or down as needed.

This means that serverless functionality can **scale to zero**. This means that the function or endpoint should not consume any resources at all until it is reached. 

A serverless application can be a single function written in a language interpreted by a serverless computing provider (typically Go, Python, and JavaScript), as long as it can return a result. Each serverless computing platform essentially belongs to a runtime environment but implements similar tools and principles.

# Why use Digital Ocean Functions

Manage resources using Digital Ocean functions and automatically scale (up or down) based on demand. This solution is uniquely positioned to meet the needs of developers and businesses.

- Build applications that require both on-demand functions and long-running containers. 
- Seamless integration with managed databases.
- Take advantage of support for your preferred languages ​​and operating hours.


# Pricing

- 90,000 GB seconds per month is free, and overages are $0.0000185 per second. 
- There is no additional charge for calling the function. This means that the price is easier, cheaper and more predictable.

# Demo 

# How to complete the Functions Challenge and Add Your Shark to the Aquarium!


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663149668666/hjcMZS1yy.png align="center")

Refer to this [link](https://functionschallenge.digitalocean.com/mlh) to know more details. Let's get started.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663151154615/7xXuBeRjx.png align="center")

## Pre-requisites

[Sign up for digitalocean](https://m.do.co/c/59733a746b9a). 

## Create a DigitalOcean Function

Visit the docs and create your [DigitalOcean Function](https://docs.digitalocean.com/products/functions/). We can create a function in one of two ways. As a standalone function or a function in an App Platform app.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150025440/L0rT_6h_p.png align="center")

- Select Functions and Click Actions. On **Actions -> Create Function**.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150131012/OFPyJOA4p.png align="left")

- Select **Python:3.9** as a runtime and give a Function name and Click Create.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150291158/xpvQLeL1n.png align="center")

- Function **Shark_Challenge_Makendran** was created.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150373138/U8yLvhdfF.png align="center")

- Copy the function URL and browse it. It will give an output as **Hello stranger!**


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150523952/YIkZVHv-K.png align="center")


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150613408/-waDLcPy4.png align="center")

- To update the function input parameters, Click **Parameters**.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150715488/n2eCo_-6F.png align="left")

- Add the below function input and Click **Save**.

```
{
    "name": "Makendran G"
}
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150857358/WRWOv2No3.png align="center")

- Click **Run** and the output will show as Hello Makendran G!

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663150943272/61tvZ94r2.png align="left")



## Make an API request to create your shark



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663169364553/ZAyhqJawd.png align="center")

- To do a **POST** request to the API URL, use the below code 

```
x = requests.post('https://functionschallenge.digitalocean.com/api/sammy/mlh',params)
return {"body": x.text}
```
- To update **parameters** for name and type, use the below code

```
params = {
        "name":"Makendran Gunasekaran",
        "type":"dinosaur"
    }
```
- Your full code should look like the below

```
import requests
def main(args):
    params = {
        "name":"Makendran Gunasekaran",
        "type":"dinosaur"
    }
    x = requests.post('https://functionschallenge.digitalocean.com/api/sammy/mlh',params)
    return {"body": x.text}
```

- Click **Save**


![140920220908.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663164603435/l4o80EN6I.png align="center")

- Click **Run**


![140920220910.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663164639581/likrkMg6M.png align="center")

- Shark has been created successfully.

```
{"message":"Shark created successfully! Congrats on successfully completing the functions challenge!","see_your_shark":"http:\/\/functionschallenge.digitalocean.com\/mlh?highlight=MakendranDemo","share_your_shark":"https:\/\/twitter.com\/intent\/tweet?url=http%3A%2F%2Ffunctionschallenge.digitalocean.com%2Fmlh%3Fhighlight%3DMakendranDemo&text=I%20just%20completed%20the%20@DigitalOcean%20Functions%20challenge%21%20"}
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663164829656/_vjwI0XsJ.png align="center")





## See your Shark swimming in the Aquarium!

[Makendran Shark in Aquarium](https://functionschallenge.digitalocean.com/mlh?highlight=MakendranDemo)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663165078838/8wlezvpxX.png align="center")


# Reference URL

- [Functions Challenge](https://functionschallenge.digitalocean.com/mlh)
- [Getting Started with DigitalOcean Functions](https://www.twitch.tv/videos/1589005387?filter=all&sort=time)













