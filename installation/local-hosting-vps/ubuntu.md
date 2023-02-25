---
description: Deploy Modmail on an Ubuntu server.
---

# Ubuntu

## Prerequisites

* Root access (**`sudo`**).
* Minimum 1GB of RAM, 2GB recommended.
* 2GB available disk space.
* Supported releases: Ubuntu 18.04 LTS, Ubuntu 20.04 LTS, Ubuntu 22.04 LTS.

## Dependencies

We will be using the following dependencies:

* Python 3.10
* NGINX web server
* Tools: `git`, `wget`, `software-properties-common`
* Additional Modmail requirements: `libcairo2-dev`, `libffi-dev`, `g++`

To install these dependencies, we will be using the **`apt`**.

{% hint style="info" %}
All code blocks should be executed in bash unless specified otherwise.
{% endhint %}

{% code title="bash" %}
```bash
sudo apt update && sudo apt upgrade -y  # Update and upgrade all packages
sudo apt install -y software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa  # Official Python PPA
sudo apt update
sudo apt install -y python3.10 python3.10-dev python3.10-venv \
                    libcairo2-dev libffi-dev g++ \
                    git wget nginx
```
{% endcode %}

<details>

<summary>Failed to install Python 3.10?</summary>

You can manually compile Python instead of adding using the Deadsnakes PPA. Compiling Python may take a while (est. 5-10 minutes).

{% code title="bash" %}
```bash
sudo apt update && sudo apt upgrade -y  # Update and upgrade all packages
sudo apt install -y software-properties-common \
                    libcairo2-dev libffi-dev g++ \
                    git wget nginx \
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





## Updating
