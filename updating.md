---
description: Guide on how to update the Modmail bot.
---

# Updating

You can run the `?update` command on your bot manually, replacing `?` with your bot prefix.

If for some reason your update command isn't working correctly, you can update your bot by going into your Modmail folder and pulling the latest changes from GitHub with the steps below.

First, determine whether you have the official Modmail repository cloned or a fork by observing the output of the command below:

```
cat .git/config
```

If the output shows this exact URL as shown below,

```
[remote "origin"]
        url = https://github.com/modmail-dev/modmail.git
```

you can go ahead and run the command below to pull in the latest changes:

```bash
git pull
```

Else, it means that your repository is a fork and must update (aka sync) it independently. If your repository is hosted on GitHub, click on the button on your repo's GitHub URL as highlighted below:

<figure><img src=".gitbook/assets/Screenshot 2023-04-13 224748.png" alt=""><figcaption></figcaption></figure>

Run the `git pull` command above locally after syncing your fork.

And then, be sure to restart your bot to apply the update.

## Breaking Changes and Update Compatibility

For the most part, it is not necessary to worry about updating from one version to the other. However, before updating, take a look at the most recent changelog entry to see if there is a **"Breaking"** note. If you are updating from a very old version, start at the version you are currently on, and scroll up to the current version, and check to see if there are any **Breaking** notes. If there are none, you can update without issue. (Remember to backup your files.)

If there is a **Breaking** entry in the changelog, read to see what steps are required to maintain functionality. If you need assistance, contact the Modmail Team in our official [support server *preferred*](https://discord.gg/cnUpwrnpYb) or on [GitHub](https://github.com/modmail-dev)
