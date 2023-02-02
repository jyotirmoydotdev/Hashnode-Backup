# NAPPTIVE made Cloud-Native Easy 🤯

# Introduction

First, let me talk about why we need to run the application on the cloud, let's take an example of a static website, which contains `index.html` we can run this file on our computer or we can say local host, but this website only can be accessed by you, and other people on the internet cannot access it. You can run a server on your computer which will expose your local host to the internet but you need to run your computer 24X7 so other people access your website, which is not practical for most of us, but what we can do? we can use a cloud provider or you can say a person who is giving their computer to run the program 24X7. Now people can access your `index.html` file at any time and from any computer.

Now we understood why we need a cloud, but one more problem arises the pain of configuring and handling the traffic and learning docker, Kubernetes, etc., But if you are a developer who just wants to focus on your work, like improving the application. So, we can use Napptive to help us with all these 👍.

Did You ask What is Napptive?🤔 I am here to explain.

NAPPTIVE is a cloud-native application platform. It is a platform that provides an integrated solution that can be used by developers and non-technical users. Enough of the description, let us try this platform.

# Deploy Static Website

To deploy a static website first, we need to upload the code to GitHub, for now, we will use the repository [github.com/napptive/static-example-launcher-app](https://github.com/napptive/static-example-launcher-app) or you can use yours. Make sure to login into your Napptive account, you can use an Email, Google, or GitHub account, and after that choose a username \[user name should be in lowercase and without space\] for your login. Now login to your account with your chosen login method. After you have logged in you can see something just like this :

![Napptive dashboard](https://cdn.hashnode.com/res/hashnode/image/upload/v1675292476863/5e137e73-3c8b-4d6a-9f07-316535c8a81b.png align="center")

You can see a tutorial pop up, you can read it. As you can see, this is the dashboard where you can maintain your apps. NAPPTIVE provides a catalog where can you simply set up your project, and click on the top left corner second option **Catalog**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675293018036/fd5072a2-5700-4bd0-a208-8519d62a2a9c.png align="center")

Click the **deploy-static-app** after that click on ► **Deploy :**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675293244740/54aa0f07-5eaa-4166-9f55-8df24b0d2210.png align="center")

After you have clicked it, you can see a YAML code inside the **Components configuration,** here we need to configure the code if you want to deploy your own code but as I have said I will deploy the default code.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675293463511/c650eb7f-8b59-41de-85cd-8b3fadc182d0.png align="center")

```yaml
components:
    - name: deploy-static-comp
      type: webservice
      properties:
        image: napptive/playground-launcher-static-nginx:1.22-v1.0.0
        cpu: "100m"
        memory: 128Mi
        ports:
            - port: 80
              expose: true
#-------------------------------------------------------------------
        env:
            - name: LAUNCHER_TARGET_REPO # target_repo
              value: https://github.com/napptive/static-example-launcher-app.git
#-------------------------------------------------------------------
            - name: LAUNCHER_REPOSITORY_USER
              value: ""
            
            - name: LAUNCHER_REPOSITORY_ACCESS_TOKEN
              value: ""
      traits: # Trait section
        - type: napptive-ingress
          properties:
            port: 80
            path: /
```

Here you can see the lien I have hilited, you need to change the **value:** link with your GitHub repo link, and you can give any **name:** to your app. After you have done you can see the ► **Deploy** button in the bottom right corner, click it. Conformation is asked just click **► Yes. deploy.** After you have clicked you can see a new app in your dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675294304097/03fa7922-b0a9-4ca8-aa99-edf6fef1fcc7.png align="center")

First, the CPU was using 0% but now you can see we are using 10% of the CPU and 3% of ram, remember different projects can use a different amount of resources. Free users have **1 CPU, 4000 MB RAM,** and **1000 MB RAM.** If you need more ram you can upgrade to the **PRO** plan.

Now, Check the deployment, you can access the deployment with the link which is in the section **endpoints** for me the link is [deploy-static-comp-80-cfdakufl20br8thb27s0.apps.playground.napptive.dev](http://deploy-static-comp-80-cfdakufl20br8thb27s0.apps.playground.napptive.dev), you can also go to this link and check this website.

To study more read the doc :  
[https://docs.napptive.com/tutorials/Deploying\_Drawio.html](https://docs.napptive.com/tutorials/Deploying_Drawio.html)

Just Like this, you can deploy **Python Apps,** **NodeJs Apps,** **WordPress,** and many more.