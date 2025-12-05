---
description: Hosting the logviewer on the cloud or on your own computer.
---

# Logviewer

## Prerequisites

This logviewer hosting tutorial is written assuming you have already set up your bot on one of the supported operating systems.

{% hint style="warning" %}
The logviewer can be set up using your local pc or homeserver. However it is higly recommended to run the logviewer on a vps or different cloud based service to avoid security issues. To let staff members access the logviewer (which is a popular usecase) you need to expose ports to the public internet which can be risky for your router and it´s local network.
There are also several other issues that can occur.
Please only set up your logviewer on your local network **if you can take full responsibility and 100% know what you are doing**.
{% endhint %}

## Dependencies
- Python 3.11
- Tools: `git`, `wget`, `nano`

## Downloading the files

* You must have git installed on your system. If you do not, run `sudo apt install git` to install it.

You can download the logviewer files by running the following command:

```bash
git clone https://github.com/modmail-dev/logviewer logviewer
```
<figure><img src="https://i.imgur.com/8um24fa.png" alt=""></figure>
Once done, you can use `cd logviewer` to enter the directory.

## Installing the dependencies

First, install pipenv by running the following command:

* Pipenv must be installed. Since this is also used for the bot, you can skip this step if you have already installed it. You may neeed to use a different command to access your python installation depending on your operating system and python configuration.

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
This will open the example `.env` file in nano. You can then edit the file with your info.
You will need to enter the same mongo URI as your bot uses. The rest of the configs can be left to the default values, unless you have a specific reason to change them.

Then save the file and exit nano by pressing `ctrl + x`, then `y`, change the name from `.env.example` to `.env` and then `enter`.

## Running the logviewer

Now you can start the logviewer with the following command

```bash
sudo pipenv run logviewer
```

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
