---
description: Hosting the patreon logviewer on the cloud or on your own computer.
---

# Patreon logviewer

This logviewer hosting tutorial is written assuming you have already set up your bot and are running Ubuntu 20.04-22.04.

## Setting up OAuth2

To set up OAuth2, you need to set a few settings in your Discord Developer Portal. First, head to the [Discord Developer Portal](https://discord.com/developers/applications) and select your modmail bot application. Then go to "OAuth2" and "General"
<figure><img src="https://i.imgur.com/ZqteRCn.png" alt=""></figure>

First, copy the Client ID and Client Secret. You will need these later when filling in the `.env`.
Then, set a redirect URL to `https://yourlogviewer.com/callback`, with the url being changed to the url of your logviewer.
Finally, click save.
<figure><img src="https://i.imgur.com/xTBUnSA.png" alt=""></figure>

## Downloading the files

* You must have git installed on your system. If you do not, run `sudo apt install git` to install it.

Due to the logviewer premium repo being private, you will first need to set up a personal access token to clone the repo. To do this, follow the steps below.

* Open github in your browser
* When logged in, click your name in the top right and go to 'settings'
* On the left, click 'Developer settings'
* On the left, click 'Personal access tokens' and then 'Tokens (classic)'
* Click 'Generate new token'
* Give the token a name and select the 'repo' scope
* Copy the token and save it somewhere safe

<figure><img src="https://i.imgur.com/rpDGDaJ.png" alt=""></figure>
<figure><img src="https://i.imgur.com/6lHiDM6.png" alt=""></figure>
<figure><img src="https://i.imgur.com/BIVl3E5.png" alt=""></figure>
<figure><img src="https://i.imgur.com/DVZysE6.png" alt=""></figure>
<figure><img src="https://i.imgur.com/xZd2m4R.png" alt=""></figure>

You can download the logviewer files by running the following command:

```bash
git clone https://github.com/modmail-dev/logviewer-premium logviewer
```

You will be prompted for your username and password. Enter your github username and the personal access token you just created.
<figure><img src="https://i.imgur.com/qe0wWIg.png" alt=""></figure>
Once done, you can use `cd logviewer` to enter the directory.

## Installing the dependencies

First, install pipenv by running the following command:

* Pipenv must be installed. Since this is also used for the bot, you can skip this step if you have already installed it.

```bash
python -m pip install pipenv
```

Installing the dependencies is done by running the following command:

```bash
pipenv install
```
<figure><img src="https://i.imgur.com/833DVry.png" alt=""><figcaption></figure>

## Configuring the .env

To configure the `.env` file, you can use the following command:

```bash
nano .env.example
```
This will open the example `.env` file in nano. You can then edit the file with your info. Besides the normal logviewer config, you will also need to add your bot's token and the client ID and secret you copied earlier.

You will need to enter the same mongo URI as your bot uses. The rest of the configs can be left to the default values, unless you have a specific reason to change them.

Then save the file and exit nano by pressing `ctrl + x`, then `y`, change the name from `.env.example` to `.env` and then `enter`.

## Running the logviewer

Now you can start the logviewer with the following command

```bash
sudo pipenv run logviewer
```

## Whitelisting users

To allow people to view the logviewer, you will have to whitelist them. To do this, you can use the following command in discord where your modmail bot is:
`?oauth whitelist roleID` or `?oauth whitelist userID`.

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
