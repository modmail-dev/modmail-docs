---
description: Deploy Modmail on a Windows machine.
---

# Windows

## Prerequisites

* Minimum 2GB of RAM**\***
* At least 2GB available disk space.
* Supported Windows version: Windows 10 or Windows 11.

{% hint style="info" %}
Note that while it is possible to run Modmail with even less memory, Windows 10 itself recommend at least 2GB (4GB for Windows 11). This guide assumes the lowest threshold to comfortably run Modmail without possibly running into any resource bottleneck.
{% endhint %}

{% hint style="warning" %}
It is not recommended to run Modmail with previous versions of Windows such as Windows 7 or Windows 8.1 as they no longer receive important security updates, making your hosted applications significantly more prone to security vulnerabilities.
{% endhint %}

## Dependencies

We will be using the following dependencies:

* Chocolatey
* Python 3.10
* Additional Modmail requirements: [GTK for Windows](https://github.com/tschoonj/GTK-for-Windows-Runtime-Environment-Installer/)

To install these dependencies, we will be using Powershell.

Search “powershell” in the Windows start menu, right-click on it and then click “Run as administrator”.

Then run each of the following commands:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
choco upgrade git --params "/GitOnlyOnPath /WindowsTerminal" -y
choco upgrade python310 -y
```

After the above installation has finished, download and install the **GTK runtime for Windows** by [clicking here](https://github.com/tschoonj/GTK-for-Windows-Runtime-Environment-Installer/releases/latest).

## Installing Bot

In any folder location of your choice, `Shift+Right Click` and click on `Open PowerShell window here`.

In your PowerShell window, run these commands to clone the official Modmail repository locally and `cd` into the folder:

```powershell
git clone https://github.com/modmail-dev/modmail; cd modmail
```

Install Pipenv and project dependencies with:

```powershell
pip install pipenv; pipenv install
```

Create a new file in the modmail folder named `.env` and paste in your environmental variables needed to run Modmail. Refer to the steps in the [parent Installation page](../#preparing-your-environmental-variables) to find where to obtain these.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Lastly, in your PowerShell window simply enter the command below to run your Modmail bot:

```powershell
pipenv run bot
```

If no error shows up, it means that your Modmail is now running correctly.

## Updating

Your Modmail is set to auto-update itself by default, but you can also run the `?update` command on your bot manually, replacing `?` with your bot prefix.

If for some reason your update command isn't working correctly, you can update your bot by opening PowerShell or any terminal application in your modmail folder and pulling the latest changes from GitHub like so:

```
git pull
```

After that, simply restart your bot to apply the latest changes.
