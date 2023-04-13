---
description: Deploy Modmail on an Ubuntu server.
---

# Ubuntu

{% hint style="warning" %}
For safety reasons, **DO NOT** install Modmail with a root user. A misbehaving or malicious plugin installed on your Modmail bot can easily access your entire system. If you are unsure how to create a new user on Linux, see [DigitalOcean’s tutorial: How To Create a New Sudo-enabled User](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-sudo-enabled-user-on-ubuntu-20-04-quickstart).
{% endhint %}

## Prerequisites

1. Root access (**`sudo`**).
2. Minimum 1GB of RAM
3. At least 2GB available disk space.
4. Supported releases:&#x20;
   * Ubuntu 18.04 LTS (Bionic Beaver)
   * Ubuntu 20.04 LTS (Focal Fossa)
   * Ubuntu 22.04 LTS (Jammy Jellyfish)

## Dependencies

We will be using the following dependencies:

* Python 3.10
* Tools: `git`, `wget`, `nano`, `software-properties-common`
* Additional Modmail requirements: `libcairo2-dev`, `libffi-dev`, `g++`

{% hint style="info" %}
All code blocks should be executed in bash and line by line unless specified otherwise.
{% endhint %}

To install these dependencies, we will be using **`apt`**.

We recommend adding the `deadsnakes` ppa to install Python 3.10:

```bash
sudo apt update
sudo apt -y install software-properties-common
sudo add-apt-repository -y ppa:deadsnakes/ppa
```

Now install the pre-requirements with `apt`, you can copy and run these 3 lines at once:

```bash
sudo apt -y install python3.10 python3.10-dev python3.10-venv python3-pip \
                    libcairo2-dev libffi-dev g++ \
                    git nano
```

<details>

<summary>Failed to install Python 3.10?</summary>

You can manually compile Python instead of adding using the Deadsnakes PPA. Compiling Python may take a while (est. 5-10 minutes). Copy and run line 2-7 all at once.

{% code lineNumbers="true" %}
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
make altinstall
```
{% endcode %}

</details>

After that, ensure `pip` is installed for Python 3.10 with:

```bash
python3.10 -m ensurepip --upgrade --default-pip
```

## Installing Bot

Clone and change directory into the Modmail folder with:

```bash
git clone https://github.com/modmail-dev/modmail
cd modmail
```

Inside the Modmail folder, Install `pipenv` and its Python packages with:

```bash
pip install pipenv
pipenv install --python 3.10
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
