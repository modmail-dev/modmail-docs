---
description: A list of commonly asked questions or problems related to Modmail.
---

# Frequently Asked Questions

#### What is Modmail?

Modmail is a Discord bot, similar to Reddit's Modmail feature. It serves as a shared inbox for server staff to communicate with their users - and vice versa - in a seamless way.

#### Can I invite Modmail?

Unfortunately, due to the nature of the bot, there is not a global invite link. Nonetheless, you can obtain a free copy of Modmail for your server. Follow the official tutorial at [https://docs.modmail.dev/installation](https://docs.modmail.dev/installation). However, if you don’t want the hassle of installing and maintaining Modmail, we offer installation, hosting, and other cool perks for [subscribers](https://buymeacoffee.com/modmaildev).

#### How does Modmail work?

Modmail uses the Discord API to interact with the platform. When someone sends a DM to the bot, it will create a new thread. Members of the moderation team can help the user and once the conversation ended, you will have access to a beautiful log of it online.

#### Is Modmail safe?

Your Modmail bot is safe as long as you don't share your bot's token. If you share your token, a "hacker" can take control over your bot. If you shared your bot token by mistake, regenerate a new token via the Discord Developer Portal.

#### Where is my data stored?

All your data including settings, blocked users, logs, installed plugins etc. are stored in your MongoDB database. The bot files only contain the stuff needed to run the bot. This means you can move your bot to a different host and still have your data intact, as long as you use the same MongoDB URI.

#### Can I request new features?

Modmail is an open-source project, which means you can easily add or request new features. You can make an issue or submit a pull request to the development branch on the repository. [Check out the contribution guidelines.](https://github.com/modmail-dev/modmail/blob/master/CONTRIBUTING.md)

#### How do I become a support member?

To join our support team, join our [Discord server](https://discord.gg/zmdYe3ZVHG). One of the more experienced members will hold an interview to check if you fit the requirements.

#### Can I add commands to the bot?

You can add commands to the bot by using plugins. All currently approved plugins can be found in the `?plugin registry` command. If there is no plugin that fits your desired features you can develop your own plugin, read more about that in the [plugin usage guide](./usage-guide/plugins.md).

#### My bot is offline, what do I do?

Join our [Discord server](https://discord.gg/zmdYe3ZVHG) and create a post in the "help-me" forum or DM Modmail. One of our support members will assist you and help you fix the issue.
Please make sure that you provide the hosting method you use to run modmail and the console logs of your bot (if possible). If the bot appears online again automatically at the same time you can also use `?debug hastebin` (share the link) and let us check why the bot had issues.

#### How can I donate the developers?

You can support the developers on the [Buy me a coffee page](https://buymeacoffee.com/modmaildev). You will also receive various rewards for it.

### I would like to have threads in a seperate guild inbox, how can I do that?

If you want to use a separate server to the main one as the inbox server (Where threads get relayed to) add the following environment variables into your ``.env`` file:

* `MODMAIL_GUILD_ID` (the server where messages are sent to)
* `GUILD_ID` (The server where users message from)

{% hint style="info" %}
You can only use one ID for each of these two variables. It´s not supported for more multi-guild setups.
The `MODMAIL_GUILD_ID` is optional if the GUILD_ID is the inbox server.
{% endhint %}

### How do I assign permissions to my staff members to let them reply to threads?

In order to assign permissions to staff, you need to use the `?permissions add` command.
The basic permission level for replying, managing snippets (pre-defined responses) is the `Supporter` level 2. For a common setup, you can assign this level to your staff role.
An example command to add the permissions to a role would look like this:
```
?permissions add level 2 @role OR the role ID
```
(you can repeat this command for adding multiple roles).

{% hint style="info" %}
If the bot does not automatically add the permissions to the set main category
please check that your Modmail bot has enough permissions to view and edit the category.
{% endhint %}

For detailed permission setup, please take a look at the [permissions usage guide](./usage-guide/permissions.md)

#### Does anyone get any info when I create my own modmail?

There is not much information we get about your instance of modmail, The only thing what we recieve is the guild-info, For example: The guildname, The amount of members of the guild, the botname, and the bot-owner. Using this we keep track of how many Modmail-instances get created on a monthly/yearly base. ( Only modmail-developers can see this )
You can disable this by adding `DATA_COLLECTION=no` to your `.env` file.
***

### I tried installing the dependencies with another Python version and it messed up my Pipfile! How can I get the original Pipfile back?

First remove the broken `Pipfile` and `Pipfile.lock` with:

```bash
rm Pipfile && rm Pipfile.lock
```

Fetch in the changes from the remote repository:

```bash
git fetch origin
```

And then, fetch the original files with:

```bash
git checkout FETCH_HEAD -- Pipfile && git checkout FETCH_HEAD -- Pipfile.lock
```

#### Answer not found?

Feel free to join our [Discord server](https://discord.gg/zmdYe3ZVHG). People will gladly help you with any questions that you have! Just create a post in the "help-me" forum or DM our Modmail.
