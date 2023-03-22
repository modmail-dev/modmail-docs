---
description: Deploy Modmail on a Windows machine.
---

# Windows

## Prerequisites

* Somewhat recent hardware / software.
* Stable internet connection from hosting server.
* The hosting server remains online 24/7.
* You have completed the initial steps: [invited your bot](../#create-a-discord-bot) and [created a MongoDB database](../#create-a-mongodb-database).
* Windows 10 or 11 (any varient)

## Filling Enviornment Variables
Once you have finished the prerequsite steps, gather your:
* BotToken
* Logviewer URL (or what you plan on using if you haven't set it up yet.)
* Primary Guild (Server) ID
* Inbox Guild (Server) ID (if applicable)
* Bot Owner's ID (usually just your ID)
* Completed MongoURI

Once you have done so, open the file `.env.example` included in your download in your preferred raw text editor of choice (Usually Notepad or Notepad++, however others exist. *Do not use Word, WordPad, or similar*)


Begin to fill in the information required:
``TOKEN=`` your bot’s token.


``LOG_URL=`` the URL of your log viewer.


``GUILD_ID=`` the ID of the server your bot operates in.


``OWNERS=`` your user ID (ie. OWNERS=9821302031291298, or if multiple owners, OWNERS=9821302031291298,9781239213813229,924822913921391).


``MONGO_URI=`` your Mongo connection URI from the MongoDB setup.


Together, they should resemble something similar to the original ``.env.example`` file.


Save the file as ``.env`` when done.

It should look something like this:
{% code title=".env" %}
```py
TOKEN=yourbottokengoeshere
LOG_URL=https://example.logs.vodka/
GUILD_ID=1079074933008781362
OWNERS=188363246695219201,231595246213922828
MONGO_URI=mongodb+srv://username:password@cluster0-abcde.mongodb.net/
```
{% endcode %}

## Installing Python

Download Python and set up Python from official Python download page: https://www.python.org/downloads/. The pre-installed Python on your local machine is usually out of date, you need the version of Python 3.09 for Modmail.

> The version of Python required may change overtime. Use the version that is recommended in this guide, and then reach out to us in the Support Server if that gives you problems. We will attempt to keep these guides as up to date as possible, however, this is the one place where a potiental version mismatch could occur.

## Running Modmail

Open Command Prompt, or "cmd". You can do this in one of two ways.

1. Press the Windows Key, then type "cmd" and press enter.
2. Hold down the Windows Key + R, a Run Dialog will appear, type in "cmd" and press enter.

### Navigate to where you stored Modmail

Find the path of where you located your modmail in File Explorer, right click the folder name `modmail` or `modmail-master` and click "Copy Path".

Then go back to your Command Prompt, and type ``cd `` then right click and press paste. This will paste in the path of the folder you just found in File Explorer. Press enter to change to that directory.

### Install the requirements

Run this command:
```py -3.9 -m pip install pipenv && py -3.9 -m pipenv install```

This will install the pipenv package, and then use it to install the most up-to-date list of dependencies from our dependency list.

### Start your Modmail

To start the Modmail bot itself, run this command:
```py -3.9 -m pipenv run python bot.py```

Your Modmail should now be working properly. If you are still having issues, let us know in our [support server](https://discord.gg/zmdYe3ZVHG).

## Updating
