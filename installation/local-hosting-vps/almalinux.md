---
description: Deploy Modmail on RHEL / Alma Linux / CentOS server.
---

# Alma Linux

{% hint style="warning" %}
For safety reasons, **DO NOT** install Modmail with a root user. A misbehaving or malicious plugin installed on your Modmail bot can easily access your entire system. If you are unsure how to create a new user on Linux, see [DigitalOcean’s tutorial: How To Create a New Sudo-enabled User](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-sudo-enabled-user-on-ubuntu-20-04-quickstart).
{% endhint %}

Alma Linux 8, 9 and CentOS Stream 8, 9 are based on Red Hat Enterprise Linux (RHEL) 8 and 9 respectively so you can essentially follow this guide if you're running any of the OS mentioned above.

## Prerequisites

1. Root access (**`sudo`**).
2. Minimum 1GB of RAM
3. At least 2GB available disk space.
4. Supported releases:&#x20;
   * Alma Linux 9
   * Alma Linux 8
   * CentOS Stream 9
   * CentOS Stream 8
   * Red Hat Enterprise Linux (RHEL) 9
   * Red Hat Enterprise Linux (RHEL) 8

## Dependencies

* Python 3.9
* Tools: `git`, `nano`

{% hint style="info" %}
All code blocks should be executed in bash and line by line unless specified otherwise.
{% endhint %}

### RHEL 9 / Alma Linux 9 / CentOS Stream 9

RHEL 9 and its derivatives have all required packages available in official repositories. Install them with `dnf`:

```bash
sudo dnf -y install python39 git @development nano
```

### RHEL 8 / Alma Linux 8 / CentOS Stream 8.4-8.x

RHEL 8 and its derivatives have all required packages available in official repositories. Install them with `dnf`:

```bash
sudo dnf -y update
sudo dnf -y group install development
sudo dnf -y install python39 python39-pip python39-devel nano git
```

## Installing Bot

Clone and change directory into the Modmail folder with:

```bash
git clone https://github.com/modmail-dev/modmail
cd modmail
```

Inside the Modmail folder, ensure `pip` is installed correctly and is defaulting to Python 3.9 with:

```bash
python3.9 -m ensurepip --upgrade --default-pip
```

And then, install `pipenv` and the bot dependencies with:

```bash
pip3.9 install pipenv
pipenv install --python 3.9
```

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
pipenv run bot
```

If no error shows up, it means your bot is now running correctly. You can stop the bot from running with `Ctrl+C` to continue using your terminal.
