# Configure Modmail and Logviewer

## Log Viewer

To be able to store data such as logs, you will need to use your own database.

Modmail supports MongoDB, and you are required to provide a MongoDB connection URI to the bot. You can get a **free** 500MB cluster from [MongoDB Atlas](https://www.mongodb.com/cloud/atlas). (Enough to store 3 million messages)

Upon creating an account, you will be greeted with this page:

![Free Tier](https://i.imgur.com/shZ7Sey.png)

Select one of the servers marked with "FREE TIER AVAILABLE" for the free option and click on "Create Cluster".

![](https://i.imgur.com/Hem2OKc.png) ![](https://i.imgur.com/jF3nISZ.png)

Follow the "Getting Started" tutorial on the bottom left, by creating a database user, whitelisting your IP, and connect to the cluster. When whitelisting you IP, be sure to select ALLOW ACCESS FROM ANYWHERE since Heroku does not grant a fixed IP.

Your IP should look something like this, with `0.0.0.0/0`:

![whitelisting](https://i.imgur.com/mILuQ5U.png')

The last part is to generate a MongoDB URI, navigate to "Clusters" and click on "CONNECT" (as shown in "Getting Started"). From the popup, select the middle option "Connect Your Application", and then the first option "Short SRV connection string". ![](https://i.imgur.com/OMI977u.png) ![](https://i.imgur.com/2BcVMGh.png)

This will show a URI under "Copy the SRV address:", copy that, and replace `<PASSWORD>` with the database user password (**not your account password**). The final URI should look something like this:

```
mongodb+srv://username:password@cluster0-abcde.mongodb.net/
```

If your URI is followed by `test?retryWrites=true` or anything else, don't include it.

## Deploying the Log Viewer

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/modmail-dev/logviewer)

You will also need to deploy another separate log viewer application from [this repo](https://github.com/kyb3r/logviewer). Click on the deploy button over there and fill in the configurations upon request. This is a **separate** Heroku application from the bot and is a simple website that will be used to display your thread logs.

## Modmail

Star the repository before you start 😉

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/modmail-dev/modmail)

1. Input a name of your choice for your app, the Heroku app name is not important.
2. Input your bot token into the `TOKEN` field.
3. Put the [ID of your Server](https://support.discordapp.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-) into the `GUILD_ID` field.
4. Put your own ID in the `OWNERS` field (if there are multiple owners, separate them by a comma: `123455,234567,456782`).
5. Input your MongoDB connection URI from the previous section into the `MONGO_URI` field.
6. Input the URL of your log viewer Heroku app (`https://yourlogviewerappname.herokuapp.com`) into the `LOG_URL` field.
7. Click the `deploy app` button and wait for it to finish.
8. Click `Manage App` and go into the `Resources` tab.
9. Now turn on the worker by clicking the pencil icon.
10. If you want, you can go over and check the application logs to see if everything is running smoothly.
11. Once the bot is online in your server, do `[your prefix]setup` (defaults `?`) and you are good to go!

Your bot is ready! Head over to Discord and try it out! If you have any issues, join the [Discord server](https://discord.gg/cnUpwrnpYb).

**Make sure to give the bot Manage Channels, Manage Messages and View Audit Logs permissions!**
