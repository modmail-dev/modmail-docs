---
description: Ways to setup auto restart for your bot on Linux hosts.
---

# Auto-Restart on Linux

{% tabs %}

{% tab title="PM2" %} PM2 is a process manager originally intended for Node.js but can also be used with Python applications, such as our Modmail bot and Logviewer. To use `pm2`, we will need to install Node Package Manager (`npm`).

#### Installing `pm2` Using `apt` (Ubuntu, Debian, etc):

```bash
sudo apt install npm -y && sudo npm i pm2 -g
```

#### Installing `pm2` using `dnf` (Fedora, Alma Linux, etc):

```bash
sudo dnf -y install npm && sudo npm i pm2 -g
```

Then, in the Modmail folder, start the Modmail process in the background with:

```
pm2 start modmail.sh --name "modmail"
```

You can see the logs of your Modmail process with:

```
pm2 logs modmail
```

And then, to make sure that `pm2` stays active and persistent between machine restarts, run the following commands:

```bash
pm2 save && pm2 startup
```

Here's some of the other PM2 commands for future reference:

```bash
pm2 restart modmail
pm2 reload modmail
pm2 stop modmail
pm2 delete modmail
pm2 list
``` {% endtab %}

{% tab title="systemd (Setting up Modmail as a Linux Service)" %} `systemd` is a built-in service manager for most Linux systems. It's primary used to manage background applications and services and to make applications auto-restart on crash and run on system startup.

We will be using `systemd` for Modmail by making a service file for our bot.

In order to create the service file, you will first need to know three things, your Linux `username`, your Modmail folder location as `modmail_path` and your Pipenv location as `pipenv_path`.

First, your Linux `username` can be fetched with the following command:

```bash
whoami
```

You can get your `pipenv_path` with:

```
whereis pipenv
```

Now, using `nano`, create a service file for systemd with:

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
sudo systemctl disable modmail
``` {% endtab %}

{% endtabs %}