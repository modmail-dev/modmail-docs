---
description: Deploy Modmail on a Fedora server.
---

# Fedora

## Prerequisites

* Root access (**`sudo`**).
* Minimum 1GB of RAM
* At least 2GB available disk space.
* Supported releases: Fedora 37, Fedora 36, Fedora 35.

## Dependencies

* Python 3.9
* Tools: `git`, `wget`, `nano`
* Additional Modmail requirements: `g++`

{% hint style="info" %}
All code blocks should be executed in bash and line by line unless specified otherwise.
{% endhint %}

Fedora Linux 35 and above has all required packages available in official repositories. Install them with `dnf`.

```bash
sudo dnf -y install python39 git nano g++ gtk3
```

## Installing Bot

In your home directory, clone and cd into the official Modmail repository with:

```bash
cd ~
git clone https://github.com/modmail-dev/modmail
cd modmail
```

Inside the Modmail folder, ensure `pip` is installed correctly and is defaulting to Python 3.9 with:

```bash
python3.9 -m ensurepip --default-pip
```

And then, install `pipenv` and the bot dependencies with:

```bash
pip install pipenv
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

If no error shows up, it means your bot is now running correctly.

## Updating

Your Modmail is set to auto-update itself by default, but you can also run the `?update` command on your bot manually, replacing `?` with your bot prefix.

If for some reason your update command isn't working correctly, you can update your bot by going into your modmail folder and pulling the latest changes from GitHub like so:

```bash
cd modmail && git pull
```

Be sure to restart your bot to apply the update.

