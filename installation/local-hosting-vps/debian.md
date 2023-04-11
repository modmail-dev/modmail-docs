---
description: Deploy Modmail on Debian / Raspberry Pi OS.
---

# Debian

Raspberry Pi OS 11 Bullseye and Raspberry Pi OS 10 Buster are based on Debian 11 Bullseye and Debian 10 Buster respectively so you can essentially follow this guide if you're running any of the OS mentioned above.

## Prerequisites

* Root access (**`sudo`**).
* Minimum 1GB of RAM
* At least 2GB available disk space.
* Supported releases: Debian 11 Bullseye, Debian 10 Buster, Raspberry Pi OS 11 Bullseye, and Raspberry Pi OS 10 (Legacy) Buster

## Dependencies

* Python 3.9 / 3.10
* Tools: `git`, `wget`, `nano`
* Additional Modmail requirements: `libcairo2-dev`, `libffi-dev`, `g++`

{% hint style="info" %}
All code blocks should be executed in bash and line by line unless specified otherwise.
{% endhint %}

To install these dependencies, we will be using **`apt`**.

### **Debian 11 Bullseye /** Raspberry Pi OS 11 Bullseye

```bash
sudo apt update
sudo apt -y install python3 python3-dev python3-venv python3-pip libcairo2-dev libffi-dev g++ git wget nano
```

At the time of writing, this will install Python 3.9 from Debian's repository.

### **Debian 10 Buster /** Raspberry Pi OS 10 Buster

You will need to manually compile Python 3.10 from source. Compiling Python may take a while (est. 5-10 minutes).

```bash
sudo apt update && sudo apt upgrade -y  # Update and upgrade all packages
sudo apt install -y software-properties-common \
                    libcairo2-dev libffi-dev g++ \
                    git wget nano \
                    build-essential zlib1g-dev libncurses5-dev \
                    libgdbm-dev libnss3-dev libssl-dev \
                    libreadline-dev libffi-dev libsqlite3-dev libbz2-dev
wget https://www.python.org/ftp/python/3.10.9/Python-3.10.9.tgz
tar xzf Python-3.10.9.tgz
cd Python-3.10.9
./configure --enable-optimizations 
sudo make altinstall
```

After following this step, make sure to specify the version when running user-level Python commands later in the guide.

For example:

* `pip install pipenv` to `pip3.10 install pipenv`&#x20;
* `python bot.py` to `python3.10 bot.py`

## Installing Bot

In your home directory, clone and cd into the official Modmail repository with:

```bash
cd ~
git clone https://github.com/modmail-dev/modmail
cd modmail
```

Inside the Modmail folder, Install `pipenv` and the bot dependencies with:

```bash
pip install pipenv
pipenv install
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
