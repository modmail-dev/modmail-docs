---
description: Deploy Modmail on Heroku PaaS.
---

# Heroku

## What is Heroku? <a href="#what-is-railway" id="what-is-railway"></a>

Heroku is a container-based cloud Platform as a Service (PaaS). Developers use Heroku to deploy, manage, and scale modern apps.

## Requirements <a href="#requirements" id="requirements"></a>

* A credit card (for payment and verification).
* An email account.
* A [GitHub](https://github.com/signup) account.
* You have completed the initial steps: [invited your bot](./#create-a-discord-bot) and [created a MongoDB database](./#create-a-mongodb-database).

## Costs

Unfortunately, Heroku is no longer free-of-charge. You will need at least their Eco plan, which currently costs $5 USD per month. See their [pricing page ](https://www.heroku.com/pricing)for more info and up-to-date prices.

If you are a higher-education student, you may be eligible for their [student offer](https://www.heroku.com/github-students), which grants you $13 USD of credits per month for 12 months—enough to host Modmail free for one year.

## Fork our GitHub repositories

You will need to fork our repositories to deploy onto Heroku.

Make sure you're logged in to [GitHub](https://github.com/). You will need to fork **two** repositories.&#x20;

First we fork the Modmail repository. Head over to [https://github.com/kyb3rr/modmail/fork](https://github.com/modmail-dev/modmail/fork), leave all the settings as default, and click **Create fork**.

<figure><img src="../.gitbook/assets/RW1.png" alt="Screenshot of creating a Modmail fork."><figcaption><p>Create a GitHub fork for the Modmail Repository.</p></figcaption></figure>

Next do the same for the Logviewer repository by heading over to [https://github.com/kyb3r/logviewer/fork](https://github.com/modmail-dev/logviewer/fork), leave all the settings as default, and click **Create fork**.

<figure><img src="../.gitbook/assets/RW2.png" alt="Screenshot of creating a Logviewer fork."><figcaption><p>Create a GitHub fork for the Logviewer Repository.</p></figcaption></figure>

Next, to keep your Modmail and Logviewer up to date, you will need to install the [Pull app](https://github.com/apps/pull). Simply head over to [https://github.com/apps/pull](https://github.com/apps/pull), click **Install**, choose **Only select repositories**, then select **both** the Modmail and Logviewer repositories that you forked in the previous step.&#x20;

<div>

<figure><img src="../.gitbook/assets/RW3.png" alt="Screenshot of installing the pull app."><figcaption><p>Click <strong>Install</strong> to install the <a href="https://github.com/apps/pull">Pull app</a>.</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/RW4.png" alt="Screenshot of selecting both repositories."><figcaption><p>Select <strong>both</strong> the Modmail and Logviewer forks, then click <strong>Install</strong>.</p></figcaption></figure>

</div>

Your GitHub should now be all set. Next step, [create a Heroku account](heroku.md#create-a-heroku-account) to deploy your bot.

## Create a Heroku account





## Updating

You can update Modmail on your Heroku account whenever changes are made to the repository. If you want to update while hosting locally (not Heroku), simply type `git pull` in your terminal and install the requirements again with `pipenv install`.

## Forking the repo

Before you get started, you must [fork](https://github.com/modmail-dev/modmail/fork) the repo first if you are using Heroku and want to update the bot.

### Syncing a fork branch from the web UI

1. On GitHub, navigate to the main page of the forked repository that you want to sync with the upstream repository.
2.  Select the Sync fork dropdown.

    ![sync-fork-dropdown](https://user-images.githubusercontent.com/70805800/194696934-5333af5d-165e-4873-b5b7-bd01f0461185.png)
3.  Then click Update branch.

    ![update-branch-button](https://user-images.githubusercontent.com/70805800/194696947-68891d50-a624-4901-a03d-e49564852a23.png)

If the changes from the upstream repository cause conflicts, GitHub will prompt you to create a pull request to resolve the conflicts.

### I want to enable automatic updates

1. Create a GitHub account
2. [Fork](https://github.com/modmail-dev/modmail/fork) the repository
3. Add GITHUB\_TOKEN into your configuration variables from https://github.com/settings/tokens with the repo scope ([Guide](https://github.com/modmail-dev/modmail/wiki/Installation-\(cont.\)#4-how-to-obtain-your-github\_token---required-for-the-update-command-)).
4. Link your GitHub account to heroku ![](https://i.imgur.com/qjWraS0.png)
5. Turn on automatic deploys ![](https://i.imgur.com/jgUVl7f.png)
6. Restart the bot

### I want to update the bot once

[Click here to create a new pull request to your fork](https://github.com/modmail-dev/modmail/pull/new/master). Select `compare across forks`, make the base repository `yourusername/modmail` and ensure the branch is set to master. Put any title you want and create the pull request. On the page that comes after this, merge the pull request.

You then want to go to your modmail application in Heroku, connect your modmail fork via the `Deploy` tab and deploy the `master` branch.

You can turn on auto-deploy for the master branch if you don't want to go through the process of logging into Heroku and deploying the branch every time changes to the repo are made in the future. However, you will have to make a pull request to update your fork every time.
