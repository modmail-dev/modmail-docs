---
description: Deploy Modmail on a Fedora server.
---

# Fedora

{% hint style="warning" %}
For safety reasons, **DO NOT** install Modmail with a root user. A misbehaving or malicious plugin installed on your Modmail bot can easily access your entire system. If you are unsure how to create a new user on Linux, see [DigitalOcean’s tutorial: How To Create a New Sudo-enabled User](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-sudo-enabled-user-on-ubuntu-20-04-quickstart).
{% endhint %}

## Prerequisites

1. Root access (**`sudo`**).
2. Minimum 1GB of RAM
3. At least 2GB available disk space.
4. Supported releases:&#x20;
   * Fedora 38
   * Fedora 37
   * Fedora 36
   * Fedora 35

## Dependencies

* Python 3.10
* Tools: `git`, `wget`, `nano`
* Additional Modmail requirements: `g++`

{% hint style="info" %}
All code blocks should be executed in bash and line by line unless specified otherwise.
{% endhint %}

Fedora Linux 35 and above has all required packages available in official repositories. Install them with `dnf`.

```bash
sudo dnf -y install python310 git nano g++ gtk3
```

And then, make sure `pip` is installed for Python 3.10 with:

```bash
python3.10 -m ensurepip --upgrade
```

## Installing Bot

Clone and change directory into the Modmail folder with:

```bash
git clone https://github.com/modmail-dev/modmail
cd modmail
```

And then, install `pipenv` and the bot dependencies with:

<pre class="language-bash"><code class="lang-bash">python3.10 -m pip install pipenv
<strong>python3.10 -m pipenv install --python 3.10
</strong></code></pre>

Create a file named `.env` with `nano` and paste all the environmental variables (secrets) needed to run the bot via right-clicking in the nano editor. Refer to the steps in the [parent Installation page](../#preparing-your-environmental-variables) to find where to obtain these.

```bash
nano .env
```

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

After that, press `Ctrl+O` and `Enter` to save your changes. Exit the `nano` editor with `Ctrl+X`.

{% hint style="info" %}
If using the `nano` editor is a bit of a learning curve, you can always FTP into your server using software like [WinSCP](https://winscp.net/eng/index.php) to edit the `.env` file manually with your preferred GUI-based editor like Notepad.
{% endhint %}

After your `.env` file is ready, you can now go ahead and try running your bot with:

```bash
python3.10 -m pipenv run bot
```

If no error shows up, it means your bot is now running correctly. You can stop the bot from running with `Ctrl+C` to continue using your terminal.

