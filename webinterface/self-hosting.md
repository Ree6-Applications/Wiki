---
description: A Guide about how to self host Ree6's Webinterface!
---

# Self hosting

## Requirements

* Java 17
* NodeJS 18

## Recommendation

* MariaDB/MySQL

### Frontend

For the Frontend you will need to host the Svelte application either locally or on a hoster.\
We recommend to use Netlify for this, because it allows a quick and easy setup without installing anything!

### Backend

For the Backend we recommend to hide it behind a reverse proxy.\
Our recommendation is Cloudflare Tunnels!

## Setup

#### Disclaimer

We will be using [Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/) and Netlify for this setup example.

### Preperation

Before we can start we will need to either download the Frontend part of the Webinterface or just fork the Repo! In our example we will be forking the [official Repository](https://github.com/Ree6-Applications/Webinterface).



### Frontend

First we will need to visit the [Netlify page](https://app.netlify.com/).\
After creating a new account or login into your already existing account, we will be creating a new site!\
Instead of creating a new one and uploading the files we will be setting it up using Github!

For this example, I created a new Github account called RealRoseDev, please do not fork any repository of that account.\


For that we will need to go into the dashboard of Netlify and Press on `Import from Git`.

![image](https://github.com/Ree6-Applications/Webinterface/assets/53257574/1478f946-2547-4d1c-86fe-4e16ee5b9a52)

We will then be asked to connect to a Git Provider, we will be using Github for this.\
When selecting Github and, if required, authorized, we will see all our repos.\
And we will need to select our fork of the Webinterface repo!

![image](https://github.com/Ree6-Applications/Webinterface/assets/53257574/07031345-347b-41b9-8e42-2fd302a626ef)

Once selected you will see this page.

![image](https://github.com/Ree6-Applications/Webinterface/assets/53257574/6e085c8a-0a65-443f-97ec-f48f4c7ffbd8)

We will need to set `Frontend/` as base directory to allow netlify to know where our Frontend is located.

![image](https://github.com/Ree6-Applications/Webinterface/assets/53257574/53a25f4d-332f-4e0e-882e-c1c3e35ea1de)

After entering the right base directory Netlify should automaticly fill the build command.\
Now that we finished up the setting up we can deploy it easily!

Once we deployed our application we have the ability to use a custom subdomain!\
Please visit [this page](https://www.netlify.com/blog/how-to-bring-a-subdomain-to-netlify-dns/) for more information about this.

### Backend

After downloading the latest release file we just run it on our server/host machine!\
Once the config has been created we stop the Backend again and configurate the config.\
We will first need to enter our Discord credentials:

![image](https://github.com/Ree6-Applications/Webinterface/assets/53257574/5ced49fc-aef9-406c-b034-664ff5f073fe)

Once we set our Discord credentials we should continue to set our SQL entries and setup the Webinterface specific configuration.\
We will need to set the `discordRedirect` to the url of our Frontend + `/login`.\
for me this would be `https://backend-setup.netlify.app/login`.\
The same value should be set for `loginRedirect`.\
At last we need to set the `allowedDomains`, we recommend to use `*.DOMAIN` if using a custom subdomain.\


For our example we are are going to use `https://backend-setup.netlify.app/`, because we have not setuped a custom subdomain.\
Your config should look like this:

![image](https://github.com/Ree6-Applications/Webinterface/assets/53257574/c412a807-1175-44e0-af66-373dea0ea2e6)

Once the config is done, we can just start the backend!\
After starting we will need to setup our reverse proxy, as said we are using Cloudflare Tunnels in this case.\
If you want to use Cloudflare Tunnels and have not yet installed it we recommend reading the official guide [here](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/tunnel-guide/remote/#1-create-a-tunnel)\


Once the Tunnel has been created, we make a new subdomain pointing to our application.\
We can check if it worked by just sending a get request to the domain.\
You should get a responds like in the image from the server:

![image](https://github.com/Ree6-Applications/Webinterface/assets/53257574/4280a2e4-2b90-4d07-bb0e-18afdc16c1c4)

Now that we have a working subdomain we will need to set it in the Frontend.

### Connecting the Frontend with the Backend

To connect the Frontend with the Backend we will need to go into the code of the Frontend.\
There is a file in `src/lib/scripts/` called `constants.ts`.\


In there we change this part:

![image](https://github.com/Ree6-Applications/Webinterface/assets/53257574/b342c498-cdd1-4ff3-92c6-70d8f0dcafd0)

To the domain of our backend!\
For me this would be `https://api.heav.lol`.\
Once Netlify has deployed the change you should be all good to use the new Frontend!

## Troubleshooting

### Invalid OAuth2 redirect\_uri

This means you have not entered the login redirect in the OAuth2 settings on Discord.

1. Go to the [Discord Developer Portal](https://discord.com/developers/applications) and sign in to your account.
2. Once you're signed in, click on the "New Application" button in the top right corner of the screen.
3. Select your Application
4. In the left-hand menu, click on the "OAuth2" tab.
5. Under the "OAuth2 Redirects" section, click the "Add Redirect" button.
6. Copy & paste the Redirect Login URL into the text field.
7. Click "Save changes" button.

### How do I get my Client code and secret?

1. Go to the [Discord Developer Portal](https://discord.com/developers/applications) and sign in to your account.
2. Once you're signed in, click on the "New Application" button in the top right corner of the screen.
3. Enter a name for your application and click the "Create" button.
4. In the left-hand menu, click on the "OAuth2" tab.
5. Copy the "Client ID" and "Client secret" and put them into the config file of the Backend.
