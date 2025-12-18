---
description: Deploy Modmail on a Windows machine.
---

# Windows

## Prerequisites

1. Minimum 2GB of RAM\*
2. At least 2GB available disk space.
3. Supported Windows version: Windows 11

{% hint style="info" %}
Note that while it is possible to run Modmail with even less memory, Windows 10 itself recommend at least 2GB (4GB for Windows 11). This guide assumes the lowest threshold to comfortably run Modmail without possibly running into any resource bottleneck.
{% endhint %}

{% hint style="warning" %}
It is not recommended to run Modmail with previous versions of Windows such as Windows 7, 8, 8.1, or 10 as they no longer receive important security updates, making your hosted applications significantly more prone to security vulnerabilities.
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

After that, ensure `pip` and `pipenv` are installed and updated for Python 3.10 with:

```powershell
py -3.10 -m ensurepip --upgrade
py -3.10 -m pip install pipenv
```

After the above installation has finished, download and install the **GTK runtime for Windows** by [clicking here](https://github.com/tschoonj/GTK-for-Windows-Runtime-Environment-Installer/releases/latest).

## Installing Bot

In any folder location of your choice, `Shift+Right Click` and click on `Open PowerShell window here`.

In your PowerShell window, run these commands to clone the official Modmail repository locally and `cd` into the folder:

```powershell
git clone https://github.com/modmail-dev/modmail
cd modmail
```

Install project dependencies inside Modmail's pipenv with:

```powershell
py -3.10 -m pipenv install
```

{% hint style="info" %}
To be able to create file named `.env` you **must** have the option to `Hide extensions for known file types` to OFF. It will not allow you to create a correctly named file with this set to on. (To turn it off, press the `...` on the File Explorer options bar, then `Options`, then `View`, and finally uncheck the option.)
{% endhint %}

Create a new file in the modmail folder named `.env` and paste in your environmental variables needed to run Modmail. Refer to the steps in the [parent Installation page](../#preparing-your-environmental-variables) to find where to obtain these.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Lastly, in your PowerShell window simply enter the command below to run your Modmail bot:

```powershell
py -3.10 -m pipenv run bot
```

If no error shows up, it means that your Modmail is now running correctly.

