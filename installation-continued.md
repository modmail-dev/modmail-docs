# Installation (continued)

## 3. Create a Database

To be able to store data such as logs, you will need to use your own database. A database is required, as the database also stores configuration data for your bot.

Modmail supports MongoDB and you are required to provide a MongoDB connection string to the bot. You can get a free 500MB cluster from [MongoDB Atlas](https://www.mongodb.com/cloud/atlas), which is enough to store around 3 million message logs.

Upon creating an account, you will be greeted with this page. Make sure you select Starter Cluster.

![Cluster selection](https://fle.soulmusic.pro/file/shxshx/Redtailedhawk1638.png)

After this, you will be taken to the below screen:

![Server selection](https://i.imgur.com/5b2Naw0.png)

Select one of the servers marked with `FREE TIER AVAILABLE` and click on `Create Cluster`. It will only take a couple of minutes to configure everything for you.

Follow the "Getting Started" tutorial on the bottom left.

## 3.1. Create a database user

Go to the `Database Access` section in the `security` tab. Click on `+ Add New User` to create a new user, whereupon a new screen will pop up. Select `Read and write to any database`, so the bot can properly store the data. Choose a username and password, but make sure they both **don't contain any special character** like `!`, `-`, `?`. Copy the password into your notepad.

Finally, click `Add User` to finish the creation.

![Create User](https://fle.soulmusic.pro/file/shxshx/Firefly1640.png)

## 3.2. Whitelist all IP's

Go to the `Network Access` section in the `security` tab. Click on `+ Add IP Address` to add an IP address, whereupon a new screen will pop up. Click the `Allow Access From Everywhere` button and `0.0.0.0/0` should appear in the `Whitelist Entry`. Otherwise, make sure to put input that manually. Finally, click `Confirm` to confirm your changes.

![Whitelisting IPs](https://fle.soulmusic.pro/file/shxshx/Topi1641.png)

## 3.3. Obtain a connection string

The last part is to generate a Mongo URI. Go to the `Clusters` section in the `Atlas` tab. Click on `Connect` on the left side of your Cluster dashboard. This will open up a new screen where you have three options. For our purposes, select the middle option `Connect Your Application`.

![Connection String](https://fle.soulmusic.pro/file/shxshx/Xuanhuaceratops1637.png)

You need to copy the connection string, which can be easily done by clicking the `Copy` button. Remove everything past `<dbname>` but keeping the `/`. Then replace `<password>` with the password for your user and `<username>` with your database-username, which you set earlier. Paste the URI in your notepad.

The final URI looks similar to this: `mongodb+srv://Username:MyPassword@modmail-kjvn21.mongodb.net/`.

![Connection String - 2](https://i.imgur.com/UIAhrZ1.png)

## 4. How to obtain your `github_token` ( Required for the update command )

Note: This is not required when you are hosting using a vps.

Start off by going to your [Github personal access tokens](https://github.com/settings/tokens) ![Personal access tokens](https://i.imgur.com/OkTue0p.png)

Generate a new token

Click on the Generate new token button in the top right of the view. ![Generate a new token](https://i.imgur.com/VZ4UaWa.png)

Give the token a name, such as: `modmail github_token`. Then check the `repo` scope. ![Name your github Token](https://i.imgur.com/1vpWTSa.png)

Click `Generate token` and GitHub will take you back to the list of tokens from before. Copy the code into your clipboard. ![Github token Copy](https://i.imgur.com/oFb2zB6.png)

If those steps are done correctly you can use the `?update` command to update your bot to the latest version!

## 5. Deploying the Log Viewer

### **Click the button below to deploy the logviewer to heroku!**

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/modmail-dev/logviewer)

**This is not the bot!**

You will need to deploy a separate log viewer application from [this repository](https://github.com/modmail-dev/logviewer). This Heroku application is separate from the bot; it's a simple website that will be used to display your thread logs.

Choose a name for your app and paste your Mongo URI (from your notepad). After you click the `Deploy App` button, it will start creating the website.

After that's done configuring, click the `View` button. It will redirect you to the logviewer home screen. Copy the link in the address bar and paste it in Notepad.

![Heroku Logviewer](https://i.imgur.com/tmiPfTL.png)

## 6. Modmail

### **Click the button below to deploy the bot to heroku.**

**This is the second application you will be deploying**

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/modmail-dev/modmail)

**6.1.** Choose any name for your app. Note: this name doesn't matter at all.

**6.2.** Put your [bot's token](https://github.com/kyb3rr/modmail/wiki/Installation#creating-a-bot-account) in the `TOKEN` field.

**6.3.** In the `DATABASE_TYPE` You may fillout: `mongodb`

**6.4.** Put the [ID of your Server](https://support.discordapp.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-) into the `GUILD_ID` field.

**6.5.** Put your own ID in the `OWNERS` field. If there are multiple owners, separate them by a comma: `180314310298304512, 355790471219511297, 325012556940836864`.

**6.6.** Put your Mongo connection URI from the previous section in the `CONNECTION_URI` field.

**6.7.** Put the `github token` you just created in the `GITHUB_TOKEN` field.

**6.8.** Put the URL of your log viewer Heroku app (`https://yourlogviewerappname.herokuapp.com`) in the `LOG_URL` field.

**6.9.** Click the `deploy app` button and wait for it to finish.

**6.10.** Click `Manage App` and go into the `Resources` tab, where you need to turn on the worker by clicking the pencil icon next to it.

**6.11.** If you want, you can go over and check the application logs to see if everything is running smoothly. If any unexpected errors pop up, join our [Discord server](https://discord.gg/etJNHCQ) and DM Modmail. The support members will help you figure out the issue and show you how to fix it.

**6.12.** Once the bot is online in your server, make sure to give it `Manage Channels`, `Manage Messages` and `View Audit Logs` permissions. If your bot is not online, recheck the previous steps above.

**6.13.** Do the `?setup` command and you are good to go!

***

Congratulations! Your bot is ready! Head over to Discord and try it out! If you have any issues or questions, join the [Discord server](https://discord.gg/etJNHCQ).

Make sure to setup permissions using this [handy guide](https://github.com/modmail-dev/modmail/wiki/Permissions)!

[Taki's Blog](https://taaku18.github.io/modmail/customization/) contains many cool customizations for the bot, so you might want to check it out!

If you like the bot, consider giving this repository a star 😉. If you want to support the developers financially, subscribe to the [Patreon](https://www.patreon.com/kyber).
