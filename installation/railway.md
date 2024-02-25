---
description: Deploy Modmail on Railway PaaS.
---

# Railway

## What is Railway?

Railway is a deployment platform where you can provision infrastructure, develop with that infrastructure locally, and then deploy to the cloud.

## Requirements

* A credit card.
* An email account.
* A [GitHub](https://github.com/signup) account.
* You have completed the initial steps: [invited your bot](./#create-a-discord-bot) and [created a MongoDB database](./#create-a-mongodb-database).

## Costs

Railway is no longer free. Their lowest plan starts at $5 per month.
Visit the [pricing](https://railway.app/pricing) page for the up-to-date pricing info.

## Fork our GitHub repositories

You will need to fork our repositories to deploy onto Railway.

Make sure you're logged in to [GitHub](https://github.com/). You will need to fork **two** repositories.

First we fork the Modmail repository. Head over to [https://github.com/modmail-dev/modmail/fork](https://github.com/modmail-dev/modmail/fork), leave all the settings as default, and click **Create fork**.

<figure><img src="../.gitbook/assets/RW1.png" alt="Screenshot of creating a Modmail fork."><figcaption><p>Create a GitHub fork for the Modmail Repository.</p></figcaption></figure>

Next do the same for the Logviewer repository by heading over to [https://github.com/modmail-dev/logviewer/fork](https://github.com/modmail-dev/logviewer/fork), leave all the settings as default, and click **Create fork**.

<figure><img src="../.gitbook/assets/RW2.png" alt="Screenshot of creating a Logviewer fork."><figcaption><p>Create a GitHub fork for the Logviewer Repository.</p></figcaption></figure>

Next, to keep your Modmail and Logviewer up to date, you will need to install the [Pull app](https://github.com/apps/pull). Simply head over to [https://github.com/apps/pull](https://github.com/apps/pull), click **Install**, choose **Only select repositories**, then select **both** the Modmail and Logviewer repositories that you forked in the previous step.

<div>

<figure><img src="../.gitbook/assets/RW3.png" alt="Screenshot of installing the pull app."><figcaption><p>Click <strong>Install</strong> to install the <a href="https://github.com/apps/pull">Pull app</a>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW4.png" alt="Screenshot of selecting both repositories."><figcaption><p>Select <strong>both</strong> the Modmail and Logviewer forks, then click <strong>Install</strong>.</p></figcaption></figure>

</div>

Your GitHub should now be all set. Next step, [create a Railway account](railway.md#create-a-railway-account) to deploy your bot.

## Create a Railway account

Head over to [Railway's website](https://railway.app/new) and create an account. It will ask you to create a new project, choose **Deploy from GitHub repo**. Then, you will be asked to connect your GitHub account.

{% embed url="https://railway.app/new" %}
Sign up for a new Railway account.
{% endembed %}

<figure><img src="../.gitbook/assets/RW5.png" alt="Screenshot of selecting the deploy from GitHub repo option."><figcaption><p>Choose <strong>Deploy from GitHub repo</strong> when creating a new project.</p></figcaption></figure>

<details>

<summary>Why does it says "Your Account is Unverified"?</summary>

If your GitHub account is new or not reputable, you may be asked to verify your identify.

This unfortunately means that you will have to provide a credit card for verification. Click **Verify Account**, read and accept Railway's **Terms of Service**, then enter your credit card details. You may be temporary charged $1 USD to confirm the legitimacy of the card.

<img src="../.gitbook/assets/RW6.png" alt="Screenshot of clicking verify account." data-size="original"><img src="../.gitbook/assets/RW7.png" alt="Screenshot of clicking terms of service." data-size="original"><img src="../.gitbook/assets/RW7B.png" alt="Screenshot of clicking I agree with terms of service." data-size="original"><img src="../.gitbook/assets/RW8.png" alt="Screenshot of entering your credit card details." data-size="original">

</details>

Next, you will be asked to **Configure a GitHub App**. You will be directed to the GitHub authentication page. Choose **Only select repositories**, then select **both** the Modmail and Logviewer repositories, as you have done before. Finally, click **Install & Authorize**.

<div>

<figure><img src="../.gitbook/assets/RW9.png" alt="Screenshot of choosing configure GitHub app."><figcaption><p>Click <strong>Configure a GitHub App</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW10.png" alt="Screenshot of selecting both repositories."><figcaption><p>Select <strong>both</strong> the Modmail and Logviewer forks, then click <strong>Install &#x26; Authorize</strong>.</p></figcaption></figure>

</div>

The next step is to deploy Modmail onto Railway. This is split into two parts. You will need to complete **both parts** to fully Modmail.

## Part 1: Deploying the Logviewer

From the [**New Project**](https://railway.app/new) page, create the project by selecting your **Logviewer** repository, then select **Add variables**.

<div>

<figure><img src="../.gitbook/assets/RW11B.png" alt="Screenshot of selecting the Logviewer repository."><figcaption><p>Choose your <strong>Logviewer</strong> repository fork.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW12B.png" alt="Screenshot of choosing Add Variables."><figcaption><p>Click on <strong>Add variables</strong>. Alternatively, the following page can also be found within the project -> variables menu.</p></figcaption></figure>

</div>

Click **New Variable**, set left to be **`CONNECTION_URI`**, then on the right, paste your revised MongoDB connection string from your Notepad (if this is new to you, [go back and read the initial steps](./)).

Don't add any other variables, nor use the suggested variables section. You should see a new variable named **`CONNECTION_URI`** added under variables once you're done.

<div>

<figure><img src="../.gitbook/assets/RW13 (1).png" alt="Screenshot of clicking new variable."><figcaption><p>Click on <strong>New Variable</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW14 (1).png" alt="Screenshot of filling left and right boxes then click add."><figcaption><p>Left side: <strong><code>CONNECTION_URI</code></strong>. Right side: your <strong>MongoDB connection string</strong>. Then click <strong>+ Add</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW15.png" alt="Screenshot of the completed variables page."><figcaption><p>Once you've added the variable, you should see a single variable named <strong><code>CONNECTION_URI</code></strong>.</p></figcaption></figure>

</div>

Next, go to the **Deployments** tab, look at the latest deployment, is it successful? You may need to wait up to 10 minutes. If you click the URL, you should be taken to your Logviewer homepage (see screenshot below). **Save this URL** into your Notepad as we will need it for the next step, we will be referring to this as your Logviewer URL.

<div>

<figure><img src="../.gitbook/assets/RW16.png" alt="Screenshot of the deployments tab, and clicking the URL."><figcaption><p>Navigate to the <strong>Deployments</strong> tab, save and open this URL.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/LVHOME.png" alt="Screenshot of the Logviewer homepage."><figcaption><p>This URL should show the Logviewer homepage.</p></figcaption></figure>

</div>

## Part 2: Deploying the Modmail bot

From the [**New Project**](https://railway.app/new) page, create the project by selecting your **Modmail** repository, then select **Add variables**.

<div>

<figure><img src="../.gitbook/assets/RW11.png" alt="Screenshot of selecting the Modmail repository."><figcaption><p>Choose your <strong>Modmail</strong> repository fork.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW12.png" alt="Screenshot of choosing Add Variables."><figcaption><p>Click on <strong>Add variables</strong>. Alternatively, the following page can also be found within the project -> variables menu.</p></figcaption></figure>

</div>

Click **New Variable.** We will be adding 5 variables in total, so repeat this step until you've added all 5 variables.

| Variable Name (left) | Variable Value (right)                                                        | Example                                                                                                               |
| -------------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **`CONNECTION_URI`** | The MongoDB Connection string from your Notepad.                              | <pre data-overflow="wrap"><code>mongodb+srv://modmail:elAO7wF1r07pNG6u@cluster0.example.mongodb.net
</code></pre>     |
|                      |                                                                               |                                                                                                                       |
| **`TOKEN`**          | The Discord bot token from your Notepad.                                      | <pre data-overflow="wrap"><code>MTA3Djv3IAxNjk1NDgdKD231.G1AoUjD.5z629aKP34JKHn4v1EsdNUwdDO3MvBR9ifVES4
</code></pre> |
|                      |                                                                               |                                                                                                                       |
| **`LOG_URL`**        | The Logviewer URL from your Notepad. Remember to add `https://` in front!     | <pre data-overflow="wrap"><code><strong>https://web-production-1234.up.railway.app
</strong></code></pre>             |
|                      |                                                                               |                                                                                                                       |
| **`OWNERS`**         | Your Discord ID. If you have multiple owners, separate your IDs with a comma. | <pre><code>718827787302791100
</code></pre>                                                                           |
|                      |                                                                               |                                                                                                                       |
| **`GUILD_ID`**       | The ID of the Discord server for your Modmail bot.                            | <pre><code>109483701365508619
</code></pre>                                                                           |
|                      |                                                                               |                                                                                                                       |

<details>

<summary>Do you have a separate staff server?</summary>

If you manage a large server where you have a separate server for communication among your moderation team, Modmail supports directing threads into the staff server instead of your main (public) server.

Simply add an additional variable named **`MODMAIL_GUILD_ID`** and set the value to your staff server's ID.

Note: the **`GUILD_ID`** should always be your main server's ID (not staff server's).

If you haven't yet invited your Modmail bot to your staff server, see the [invite section](./#do-you-have-a-separate-staff-server).

</details>

<div>

<figure><img src="../.gitbook/assets/RW17.png" alt="Screenshot of clicking new variable."><figcaption><p>Click on <strong>New Variable</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW18.png" alt="Screenshot of the completed variables page."><figcaption><p>Once you've added the variable as per the table above, you should see 5 variables here.</p></figcaption></figure>

</div>

## Complete the setup

Within 10 minutes of saving the Modmail bot variables, your Modmail bot should come online in your server. The default prefix for Modmail is **`?`**. You need to run **`?setup`** within your server to complete the setup. If you configured Modmail to use a separate staff server, you must run this command **in your staff server**. This will create a category for your Modmail threads and a Logs channel for an archive of all past threads.

<details>

<summary>Help! My bot hasn't started after 10 minutes.</summary>

This probably means you've failed to follow one or more steps. \[more info TODO]

</details>

## How to keep your bot running 24/7

You have 10 days to test Modmail without upgrading to the "Developer" plan. As mentioned in the [costs](railway.md#costs) section, Railway's Developer plan provides enough free monthly credits to run Modmail for **free** 24/7 everyday. However, you will need to provide your credit card details to upgrade your plan. More details can be found [here](https://docs.railway.app/reference/plans).

#### Usage-based subscription

Head over to the \*\*\*\* [**Billing Details**](https://railway.app/account/billing) page, click the **Unlock** button to unlock Developer plan. Then input your credit card details and hit **Subscribe to Developer Plan**.

{% hint style="warning" %}
Subscribing to the Developer plan under _usage based subscription_ **may incur you unexpected charges**. This because Railway does not provide any safe-guards or monthly spending limits. Average Modmail and Logviewer usage should be well below the free threshold. However, if you run resource-intensive code via plugins or due to other means, you credit card may be billed.

If you want to guarantee that your credit card won't get charged for whatever reason, check out the [credit-based subscription model](railway.md#credit-based-subscription-alternative-subscription-model) instead. Alternatively, you can use a virtual credit card, such as [privacy.com](https://privacy.com/virtual-card), to verify for the Developer plan.
{% endhint %}

<div>

<figure><img src="../.gitbook/assets/RW20.png" alt="Screenshot of clicking the unlock button."><figcaption><p>Click the <strong>Unlock</strong> button next to <strong>Unlock Developer Plan</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW21.png" alt="Screenshot of filling in credit card details and clicking subscribe."><figcaption><p>Fill in your credit card details then click <strong>Subscribe to Developer Plan</strong>.</p></figcaption></figure>

</div>

<details>

<summary>Why was I charged $1.00 USD?</summary>

This should be a temporary charge to verify that your credit card works as expected. Railway explains this with:

A temporary hold of $1.00 USD will be placed on the card and then refunded immediately.

</details>

#### Credit-based subscription (alternative subscription model)

If you rather pay a one-time $5.00 USD non-refundable credit purchase instead of permanently linking your credit card, you can choose to use the credit-based subscription model. As long as you have a non-zero credit balance (which should be forever since the monthly operating cost for Modmail is $0.00), you will be continuously subscribed to the Developer plan.

<div>

<figure><img src="../.gitbook/assets/RW20.png" alt="Screenshot of clicking the unlock button."><figcaption><p>Click the <strong>Unlock</strong> button next to <strong>Unlock Developer Plan</strong>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW23.png" alt="Screenshot of clicking credit-based subscription."><figcaption><p>Click <strong>Credit-based subscription</strong> at the bottom.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW24.png" alt="Screenshot of entering credit card info, $5 amount, and click purchase credits."><figcaption><p>Fill in your credit card details, enter <strong>$5.00</strong> as the amount (it's the minimum), then click <strong>Purchase Credits</strong>.</p></figcaption></figure>

</div>

There you go! Your bot should now be able to run 24/7 without interruptions. Head over to the [**Usage**](https://railway.app/account/usage) page to make sure you won't be charged. Add up the estimated price for both your projects and verify that they're well below $5.00 USD.

<figure><img src="../.gitbook/assets/RW22.png" alt="Screenshot of the usage page."><figcaption><p><strong>Estimated Bill</strong> should be $0.00 and the sum of the <strong>Estimated</strong> should be well below $5.00.</p></figcaption></figure>

<details>

<summary>How do I cancel my Developer plan subscription?</summary>

If you're subscribed under the [usage-based subscription](railway.md#usage-based-subscription) model, you can cancel your subscription by heading to the \*\*\*\* [**Billing Details**](https://railway.app/account/billing) page, click **Manage Subscription**, then click **Cancel plan**.

<img src="../.gitbook/assets/RW25.png" alt="Screenshot of clicking manage subscription." data-size="original"><img src="../.gitbook/assets/RW26.png" alt="Screenshot of clicking cancel plan." data-size="original">

</details>

## Updating

Railway is configured to automatically update your Modmail bot and Logviewer whenever new updates become available.

<details>

<summary>How do I disable auto-updates?</summary>

You can disable auto-updates by heading to the settings page for **both** your Modmail and Logviewer projects. Under **Automatic Deployments**, click **Disable trigger**. ![Screenshot of disabling auto updates for Logviewer.](../.gitbook/assets/RW19b.png)![Screenshot of disabling auto updates for Modmail.](../.gitbook/assets/RW19a.png)

</details>

## Next steps

Now that you've successfully set up Modmail, visit the [Getting Started](../getting-started.md) page to find information on using Modmail.

You can also join our [**Discord Server**](https://discord.gg/cnUpwrnpYb) to interact with our community or get support for Modmail.
