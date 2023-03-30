---
description: Hosting the patreon logviewer on the cloud or on your own computer.
---

# Patreon logviewer

Before starting, please ensure that you have first followed the regular logviewer hosting setup [here](./logviewer)

## Setting up OAuth2

To set up OAuth2, you need to set a few settings in your Discord Developer Portal. First, head to the [Discord Developer Portal](https://discord.com/developers/applications) and select your modmail bot application. Then go to "OAuth2" and "General"
<figure><img src="https://i.imgur.com/ZqteRCn.png" alt=""></figure>

First, copy the Client ID and Client Secret. You will need these later when filling in the .env.
Then, set a redirect URL to `https://yourlogviewer.com/callback`, with the url being changed to the url of your logviewer.
Finally, click save.
<figure><img src="https://i.imgur.com/xTBUnSA.png" alt=""></figure>

## Downloading the files

* You must have git installed on your system. If you do not, run `sudo apt install git` to install it.

You can download the logviewer files by running the following command:

```bash
git clone https://github.com/modmail-dev/logviewer-premium logviewer
```
<figure><img src="https://i.imgur.com/8um24fa.png" alt=""></figure>
Once done, you can use `cd logviewer` to enter the directory.

## Installing the dependencies

* Pipenv must be installed. Since this is also used for the bot, you can skip this step if you have already installed it.

Installing the dependencies is done by running the following command:

```bash
pipenv install
```
<figure><img src="https://i.imgur.com/833DVry.png" alt=""><figcaption></figure>

## Configuring the .env

To configure the .env file, you can use the following command:

```bash
cp .env.example .env
nano .env
```
This will copy the example .env file and open it in nano. You can then edit the file with your info. Besides the normal logviewer config, you will also need to add your bot's token and the client ID and secret you copied earlier.

You will need to enter the same mongo URI as your bot uses. The rest of the configs can be left to the default values, unless you have a specific reason to change them.

Then save the file and exit nano by pressing `ctrl + x`, then `y` and `enter`.

## Running the logviewer

Now you can start the logviewer with the following command

```bash
sudo pipenv run logviewer
```

## Whitelisting users

To allow people to view the logviewer, you will have to whitelist them. To do this, you can use the following command in discord where your modmail bot is:
`oauth whitelist roleID` or `oauth whitelist userID`.

## (Optional) Keep logviewer running in the background with pm2

Pm2 can keep your logviewer automatically online in the background even if you close your terminal. To install pm2, run the following command:

```bash
sudo apt install npm -y && sudo npm i pm2 -g
```

Once installed, you can start the logviewer with pm2 by running the following command:

```bash
sudo pm2 start logviewer.sh --name "logviewer" && sudo pm2 save
```

More info on how to use pm2 can be found [on pm2's website](https://pm2.keymetrics.io/docs/usage/quick-start/).
