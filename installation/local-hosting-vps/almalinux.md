---
description: Deploy Modmail on RHEL / Alma Linux / CentOS server.
---

# Alma Linux

Alma Linux 8, 9 and CentOS Stream 8, 9 are based on Red Hat Enterprise Linux (RHEL) 8 and 9 respectively so you can essentially follow this guide if you're running any of the OS mentioned above.

## Prerequisites

* Root access (**`sudo`**).
* Minimum 1GB of RAM
* At least 2GB available disk space.
* Supported releases: Alma Linux 9, Alma Linux 8, CentOS Stream 9, CentOS Stream 8, RHEL 9 and RHEL 8

## Dependencies

* Python 3.9
* Tools: `git`, `nano`

{% hint style="info" %}
All code blocks should be executed in bash and line by line unless specified otherwise.
{% endhint %}

### RHEL 9 / Alma Linux 9 / CentOS Stream 9

Alma Linux 9 have all required packages available in official repositories. Install them with `dnf`:

```bash
sudo dnf -y install python39 git @development nano
```

### RHEL 8 / Alma Linux 8 / CentOS Stream 8.4-8.x

```bash
sudo dnf -y update
sudo dnf -y group install development
sudo dnf -y install python39 python39-pip python39-devel nano git
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

If no error shows up, it means your bot is now running correctly.

## Setting up auto-restart

To have the bot auto-restart on crash or system reboot, we will be using `systemd` by making a service file for our bot.

In order to create the service file, you will first need to know three things, your Linux `username`, your Modmail repository `path` and your `pipenv_path`.

First, your Linux `username` can be fetched with the following command:

```bash
whoami
```

If you have cloned the Modmail repo as a `root` user, your Modmail repo path should be:

```bash
/root/modmail
```

Otherwise, your path should be:

```bash
/home/$USER/modmail/
```

You can get your `pipenv_path` with:

```
whereis pipenv
```

Now, using `nano`, create a service file for `systemd` with:

```bash
sudo nano /etc/systemd/system/modmail.service
```

and paste in the contents below, replacing `username`, `modmail_path` and `pipenv_path` with yours respectively. `Ctrl+O` and `Enter` to save. `Ctrl+X` to exit the nano editor.

{% code title="modmail.service" %}
```bash
[Unit]
Description=Modmail bot
After=network.target

[Service]
User=username # replace this
Group=username # replace this
Restart=always
RestartSec=10
Type=simple
WorkingDirectory=modmail_path # replace this
ExecStart=pipenv_path run python bot.py # replace pipenv_path only

[Install]
WantedBy=multi-user.target
```
{% endcode %}

Now, start your Modmail bot with:

```bash
sudo systemctl start modmail
```

If everything goes correctly, you should see your bot online. You can also view the logs of your systemd process with:

```bash
sudo journalctl -eu modmail
```

With that said, go ahead and enable your Modmail service to auto-restart after crash and reboot with:

```bash
sudo systemctl enable modmail
```

If in the future you need to stop and disable your Modmail service, you can do so with:

```bash
sudo systemctl stop modmail
sudo systemctl disable modmai
```

## Updating

Your Modmail is set to auto-update itself by default, but you can also run the `?update` command on your bot manually, replacing `?` with your bot prefix.

If for some reason your update command isn't working correctly, you can update your bot by going into your modmail folder and pulling the latest changes from GitHub like so:

```bash
cd modmail && git pull
```

Be sure to restart your bot to apply the changes. If you followed the above instructions on setting up auto-restart, you can do so with:

```bash
sudo systemctl restart modmail
```
