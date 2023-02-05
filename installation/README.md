---
description: Modmail hosting and installation guide.
---

# Installation

Modmail is a self-hosted bot. This unfortunately means that there's **no** public bot invite. Furthermore, due to the inner workings of the bot and its highly customisable interfaces, you will need to host your own dedicated Modmail bot.&#x20;

This section provides setup instructions for Modmail on many hosting methods, both **free\* and paid**.&#x20;

\*Some free options require a credit card for verification.&#x20;

Here are the basic requirements for hosting your Modmail bot. You will find instructions on obtaining and using them in later sections.

*   A Discord account.

    You will need to create a Discord bot under your account.
*   A MongoDB database instance.

    Modmail will store its internal data to this database.
*   A hosting server.

    To keep Modmail running 24/7 in your server.
*   A Desktop Notepad, Notes, TextEdit, etc.

    Anywhere you can copy and paste to temporary store some texts while we set up the bot.

{% hint style="warning" %}
**Note:** There are two components for Modmail: the bot component and the Logviewer component. You will need **both** to take full advantage of Modmail.
{% endhint %}

## Create a Discord bot

The first step in setting up Modmail is to create a Discord bot.&#x20;

Head over to the [**Discord Developer Portal**](https://discordapp.com/developers/applications/) and create a new application.

<div>

<figure><img src="../.gitbook/assets/Image1.png" alt="Screenshot of the Discord Developer Portal homepage."><figcaption><p>Click <strong>New Application</strong> from the homepage.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image2.png" alt="Screenshot of the application creation confirmation page."><figcaption><p>Choose a name for your bot, then click <strong>Create</strong>.</p></figcaption></figure>

</div>

Once you created a new application, head over to the **Bot** tab and create a new bot.

<figure><img src="../.gitbook/assets/Image3.png" alt="Screenshot of the general information tab, arrow pointing to the bot tab."><figcaption><p>Navigate to the <strong>Bot</strong> tab on the sidebar. On this page, you can also edit the <em>About Me</em> section of your bot.</p></figcaption></figure>

<div>

<figure><img src="../.gitbook/assets/Image4.png" alt="Screenshot of the bot tab, click add bot."><figcaption><p>Click <strong>Add bot</strong> to create the bot.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image5.png" alt="Screenshot of the confirmation page, click yes do it."><figcaption><p>Click <strong>Yes, do it!</strong> to confirm your choice.</p></figcaption></figure>

</div>

After adding a bot, reset the token, then copy and store the newly generated token in your Notepad for later.

<div>

<figure><img src="../.gitbook/assets/Image6.png" alt="Screenshot with arrow pointing to reset token."><figcaption><p>Click on <strong>Reset Token</strong> then confirm with <strong>Yes, do it!</strong> Here you can also set your bot's profile picture.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image7.png" alt="Screenshot of clicking the copy button."><figcaption><p>Click <strong>Copy</strong> then store the copied token somewhere safe for later steps.</p></figcaption></figure>

</div>

{% hint style="danger" %}
**Make sure to keep this token private!** Anyone who has this token can control (or "hack") your bot and potentially cause malicious damage. If you feel that your token has been leaked, click on **Reset Token** immediately to invalidate the old token and generate a new one. Don't forget to also update your Modmail configs with your new token.
{% endhint %}

Next, we need to change some bot settings. Toggle **off** _public bot_, then toggle **on** both _server members intent_ **and** _message content intent_. Remember to click on **Save Changes**.

<figure><img src="../.gitbook/assets/Image8.png" alt="Screenshot of public bot toggled off, server members intent and message content intent toggled on. Pointing at Save Changes button."><figcaption><p>Toggle off <strong>public bot</strong>, toggle on <strong>server members intent</strong>, and toggle on <strong>message content intent</strong>. Afterwards, click <strong>Save Changes</strong> to apply the changes. Your on/off toggles should appear similar to this screenshot.</p></figcaption></figure>

<details>

<summary>Why do I need to do this?</summary>

Disabling _public bot_ prevents other users from inviting your bot. Your bot may not behave appropriately if it's present in other servers.

Enabling _server members intent_ allows Modmail to view your server's members list and efficiently populate the bot's internal cache.

Enabling _message content intent_ allows bot commands to function since Modmail doesn't use slash commands.

What about _presence intent_? It is not needed for Modmail, but it may be required for specialized plugins. We recommend keeping this toggled off to save computational resources.

</details>

### Inviting the bot

Navigate back to the **General Information** tab and copy the application ID.

<figure><img src="../.gitbook/assets/Image9.png" alt="Screenshot of copying the application ID on the general information tab."><figcaption><p>Click <strong>Copy</strong> to copy the application ID. This is also known as your "Bot ID".</p></figcaption></figure>

Using the following URL as template, replace `YOUR-ID-HERE` with the ID you just copied. Do not change anything else! Open a new browser tab and go to that URL.&#x20;

{% code overflow="wrap" %}
```
https://discord.com/oauth2/authorize?scope=bot&permissions=416075476184&client_id=YOUR-ID-HERE
```
{% endcode %}

Discord should prompt you to choose a server to invite your bot, followed by a list of permissions. Scroll to the bottom and click **Authorize**.&#x20;

<div>

<figure><img src="../.gitbook/assets/Image10.png" alt="Screenshot of the Discord bot invite prompt, click continue."><figcaption><p>Choose your server to invite, then click <strong>Continue</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image11.png" alt="Screenshot of the Discord invite prompt second page, click authorize."><figcaption><p>Scroll to the bottom and click <strong>Authorize</strong>. Don't un-check any permissions. Only Administrator is optional.</p></figcaption></figure>

</div>

{% hint style="info" %}
You **must leave on** all permissions excepted for _Administrator_ (optional). However, we recommend allowing _Administrator_ for ease of setup and to avoid complications with Discord permissions.
{% endhint %}

<details>

<summary>Do you have a separate staff server?</summary>

If you manage a large server where you have a separate server for communication among your moderation team, Modmail supports directing threads into the staff server instead of your main (public) server.

You will need to invite your Modmail bot to **both** your main (public) server and your staff server using the same invite link above.

</details>

Your bot should now be **offline** in your server. Congratulations, that's as expected! You have successfully created a Discord bot. The next step is to [create a MongoDB database](./#create-a-mongodb-database).

## Create a MongoDB database

Modmail uses MongoDB to store its internal configurations and log histories. You must create a MongoDB database in order to use Modmail.&#x20;

We will be using [MongoDB Atlas](https://www.mongodb.com/atlas), which provides us with a free 512MB storage share—more than enough for Modmail.

### Requirements

* No credit card required.
* An email account.

Head over to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register) and register for a free account:

{% embed url="https://www.mongodb.com/cloud/atlas/register" %}
MongoDB Atlas registration page.
{% endembed %}

<div>

<figure><img src="../.gitbook/assets/Image12.png" alt="Screenshot of the sign up page for MongoDB Atlas. Fill all info and click create your Atlas account."><figcaption><p>Fill in with your info, then click <strong>Create your Atlas account</strong>. Optionally, you can sign up with Google.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image13.png" alt="Screenshot of an email verification screen."><figcaption><p>You will need to confirm your email. Open your confirmation email in the same browser.</p></figcaption></figure>

</div>

Once you confirmed your email, you will be greeted by the MongoDB welcome introduction, asking you to "tell us a few things about yourself and your project". You can answer these questions honestly or however you like.

In the next step for "deploy a cloud database", choose the **Shared** option. Any recommended region (free regions) are fine. Make sure the **Cluster Tier** is set to **M0 Sandbox** and the price shows as **FREE**.

<details>

<summary>Don't see this page?</summary>

It's possible that you verified your email in a different browser session, or you manually signed in to MongoDB Atlas.

In this case, you can still follow the same steps below, but first click **Build a Database**:&#x20;

![Screenshot of homepage and click build a database.](../.gitbook/assets/Image22.png)

</details>

<figure><img src="../.gitbook/assets/Image14.png" alt="Screenshot of choosing the shared option and click create."><figcaption><p>Choose the free <strong>Shared</strong> option and click <strong>Create</strong>.</p></figcaption></figure>

<div>

<figure><img src="../.gitbook/assets/Image15.png" alt="Screenshot of making sure the shared option is selected."><figcaption><p>Make sure <strong>Shared</strong> is selected, then choose any of the <em>"recommended region"</em>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image16.png" alt="Screenshot of making sure cluster tier is set to M0 sandbox and click create cluster."><figcaption><p>Make sure Cluster Tier is set to <strong>M0 Sandbox</strong>. The Cluster Name doesn't matter. Click <strong>Create Cluster</strong>.</p></figcaption></figure>

</div>

On the following **Security Quickstart** page, do the following:&#x20;

1.  Authentication method: _Username and Password_

    Username: `modmail`

    Password: Click **Autogenerate Secure Password** - don't type your own password!
2.  Copy and **save the password** in your Notepad, you will need this for later.

    From now on, we will be referring to these credentials as the _database username_ and _database password_.
3. Click **Create User**.
4. Scroll down, we will be connecting from: _My Local Environment_
5.  Set IP address as **`0.0.0.0/0`** and anything for the description.

    **You must** set the IP address exactly to this, unless you know what you're doing. **Do not** set it to anything else or click add my current IP address. This allows Modmail to connect to your database.
6. Click **Add Entry**.

You can now click **Finish and Close** on the bottom. Your page should look similar to this:

<div>

<figure><img src="../.gitbook/assets/Image17.png" alt="Screenshot of adding a database user, then click create user."><figcaption><p>Click <strong>Autogenerate Secure Password</strong>, <strong>copy and save</strong> the database password, then click <strong>Create User</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image18.png" alt="Screenshot of setting the whitelist IP, then click add entry."><figcaption><p>Set IP Address to <strong>0.0.0.0/0</strong>, then click <strong>Add Entry</strong>.</p></figcaption></figure>

</div>

Next, we will need to generate a _MongoDB connection string_. Simply click **Connect** on the main dashboard, choose **Connect your application**, then copy the **connection string** (the default driver is fine) and paste it into your Notepad.

<div>

<figure><img src="../.gitbook/assets/Image19.png" alt=""><figcaption><p>Click <strong>Connect</strong> on the main dashboard.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image20.png" alt=""><figcaption><p>Choose <strong>Connect your application</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Image21.png" alt=""><figcaption><p>Copy the <strong>connection string</strong>.</p></figcaption></figure>

</div>

If you followed all the steps so far, your Notepad should contain three lines: the bot token, the database password, and the MongoDB connection string. For example:

{% code title="My Notepad" %}
```
My bot token: MTA3Djv3IAxNjk1NDgdKD231.G1AoUjD.5z629aKP34JKHn4v1EsdNUwdDO3MvBR9ifVES4
My database password: elAO7wF1r07pNG6u
My MongoDB connection string: mongodb+srv://modmail:<password>@cluster0.example.mongodb.net/?retryWrites=true&w=majority
```
{% endcode %}

Finally, you will need to combine the database password with the MongoDB connection string by **replacing** the `<password>` (including the `<>`) with the database password.&#x20;

You also need to **remove** everything after `.mongodb.net` at the end of the MongoDB connection string.

This is what your Notepad should look like now:

{% code title="My Notepad (revised)" %}
```
My bot token: MTA3Djv3IAxNjk1NDgdKD231.G1AoUjD.5z629aKP34JKHn4v1EsdNUwdDO3MvBR9ifVES4
My MongoDB connection string: mongodb+srv://modmail:elAO7wF1r07pNG6u@cluster0.example.mongodb.net
```
{% endcode %}

You finished the MongoDB steps! At this point, your bot should still be **offline**. You can now proceed to the [next steps](./#next-steps) and start up your Modmail bot.

## Next steps

Click on one of the links below to view further instructions for your preferred hosting method.

### [Railway](railway.md) (free)

A platform as a service (PaaS) that offers a generous free plan, which allows you to host Modmail for free without any downtime. A credit card is required for verification purposes.[ **Go to guide ►**](railway.md)****

### [Local Hosting](local-hosting-vps/) (free)

Do you have an old PC, a Raspberry Pi, or a Linux box that you're able to keep online 24/7?&#x20;

You can host Modmail on it for free (electricity fees may apply).[ **Go to guide ►**](local-hosting-vps/)****

### [Modmail Patreon](https://www.patreon.com/kyber) (paid)

We offer paid hosting solution for your Modmail bot. Hosting Modmail with us costs $4-5 USD per month.&#x20;

We will also fully manage your bot hosting for you, so you don't need to worry about upgrading or setting up your own host server. [ **Go to Patreon page ►**](https://www.patreon.com/kyber)****

### [Heroku](heroku.md) (paid)

Another popular PaaS that's used to be free. However, their recent pricing adjustments, it now costs $5-7 USD per month.&#x20;

If you are currently a higher-education student, you may be eligible for the first year free with their [student offer](https://www.heroku.com/github-students).[ **Go to guide ►**](heroku.md)****

### [Cloud Server / VPS](local-hosting-vps/) (paid)

Apart from [Patreon hosting](./#modmail-patreon-paid), hosting on a cloud server / VPS is the most reliable hosting method. Rent a virtual server from any reputable hosting provider for roughly $4-10 USD per month (price varies), and you'll be able to install Modmail onto the server.

This method is a lot more "involved" than other solutions. If you're not comfortable with configuring remote Linux environments, we recommend you to choose a different option. [ **Go to guide ►**](local-hosting-vps/)****

### [Replit](replit.md) (free/paid)

> The Modmail team does not recommend this hosting method.

An online code execution environment. You can host Modmail there for free using certain exploits. The legitimate method costs $7 USD per month. However, regardless if you pay or host for free, hosting on Replit are often unstable. [ **Go to guide ►**](replit.md)****





