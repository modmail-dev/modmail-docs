---
description: https://github.com/kyb3r/modmail
---

# Introduction

Modmail is a self-hosted Discord bot for your server. It works similar to [Reddit](https://reddit.zendesk.com/hc/en-us/articles/210896606-What-is-Modmail-)'s Modmail—both in functionality and purpose. It serves as a shared inbox for server staff to communicate with their users in a seamless way.

This bot is free for everyone and always will be. If you like this project and would like to show your appreciation, you can support us on [**Patreon**](https://www.patreon.com/kyber), cool benefits included!

## What is Modmail used for?

When a member sends a direct message to Modmail, the bot will create a channel (we call it a "thread") into a designated category. All further DM messages will automatically relay to that channel, then any available staff can respond within the channel. Compared to ticketing bots, Modmail allows easier and more organised discussions among staff. &#x20;

<figure><img src="https://i.imgur.com/fru5Q07.png" alt=""><figcaption><p>An example of a Modmail thread.</p></figcaption></figure>

Our Logviewer will save the threads so your staff can view previous threads through their corresponding log link. ~~Here is an~~ [~~**example**~~](https://logs.modmail.dev/example).

## Features

#### **Highly customisable**

* Changeable bot status, prefix, category, log channel, etc.
* Versatile command permission system.
* Interface elements (color, responses, reactions, etc.).
* Snippets and command aliases.
* Minimum duration for accounts to be created before allowed to contact Modmail (`account_age`).
* Minimum length for members to be in the guild before allowed to contact Modmail (`guild_age`).

**Advanced logging functionality**

* When you close a thread, Modmail will generate a log link and post it to your log channel.
* Native Discord dark-mode feel.
* Markdown/formatting support.
* Discord authentication-protected logs ([Patreon-only feature](https://patreon.com/kyber)).
* See past logs of a user with `?logs`.
* Searchable by text queries using `?logs search`.

#### **Robust implementation**

* Ease of installation: you can get your Modmail bot running in under 10 minutes!
* Schedule tasks in human time, e.g. `?close in 2 hours silently`.
* Editing and deleting messages are synced.
* Support for the diverse range of message contents (multiple images, files).
* Paginated commands interfaces via reactions.

This list is ever-growing thanks to active development by our exceptional contributors. See a full list of available commands by using the `?help` command.

## Installation

Visit our [installation page](installation/) for detailed instructions on setting up Modmail for your server.

## Supporting the project

You have various options to help the project. Giving this repository a star is greatly appreciated. You can also help people that have trouble setting up Modmail at our [Discord server](https://discord.gg/etJNHCQ).&#x20;

If you like to show your appreciation, consider supporting us on [**Patreon**](https://www.patreon.com/kyber)!

### Contributing

Support Modmail with your contributions! Whether it be improvements to the documentation or new functionality, please feel free to make the change. Check out our [contributing guidelines](https://github.com/kyb3r/modmail/blob/master/.github/CONTRIBUTING.md) before you get started.

## Next steps

* Read about [installing Modmail](installation/).
* Become familiar with [Modmail commands and functionalities](getting-started.md).

{% hint style="info" %} In this guide when we refer to **bot commands**, we will assume the prefix to be ``?`` and will display them like in this example. ``?help``. Optional arguments will be in [brackets], for example ``?close [time] [reason] [silently].`` Required arguments will be put in <andled brackets>, for example ``?permissions add <command/level> <name> <user/role>` {% endhint %}
