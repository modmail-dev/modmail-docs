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

## Setting up auto-restart

To have the bot auto-restart on crash or system reboot, we will be using `nssm` by making a service for our bot application.

First, find the Python path of your Modmail pipenv by running `pipenv shell` and `which python` in your Modmail folder. Copy the path that appears in your terminal and paste it in the first line of our next step.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Second, create a file named `modmail.bat` in your modmail directory with the following contents, replacing `python_path` with the one you copied previously and `python.exe` with `activate.bat`:

```batch
call python_path
call python bot.py
```

The finished file should look something like this:

{% code title="modmail.bat" %}
```batch
call C:\Users\Raiden\.virtualenvs\modmail-oXWHQUly\Scripts\activate.bat
call python bot.py
```
{% endcode %}

Third, download `nssm` by [clicking here](http://nssm.cc/download) and downloading the file under "Latest Release".

The download will be a `.zip` file so you'll need to extract it first using your file archiver program (such as WinRAR or 7-zip). After that, find `nssm.exe` in the folder corresponding to your OS bit version (these days it should be win64) and copy it's file path:

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

As `nssm` itself is only a command-line program, we'll need to use our trusty Terminal to use the application to create our service. So, search up "Powershell" in your start menu, right-click it and click "Run as Administrator".&#x20;

Change directory (CD) into the folder path that you copied earlier, the command should look like something like this:

```powershell
cd "C:\Users\Raiden\Downloads\nssm-2.24\win64"
```

{% hint style="info" %}
Wrapping "your folder\directory" on Windows in doublequotes is necessary to make sure spaces in our file path is parsed correctly.
{% endhint %}

And then, proceed to create a new service for Modmail using `nssm` with:

```powershell
.\nssm install "Modmail"
```

A GUI will pop up where you can fill in the details needed for your Modmail service. Replace the `Path` with the path of your `modmail.bat` script and the `Startup directory` with the path of your Modmail folder as follow:

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Details on the "Application" tab</p></figcaption></figure>

You can fill in these extra details as you see fit as it's only for your own reference:

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Details on the "Details" tab</p></figcaption></figure>

You can also optionally specify a log file as output and error in the `I/O` tab, just be sure to create the file beforehand so you can select it in the GUI.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Details on the "I/O" tab</p></figcaption></figure>

And finally, click "Install Service" to install your Modmail bot as a service on your Windows system.\


<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

By now you should have the service installed but not yet running. You can start it by using this command below in the open `nssm` Terminal from earlier:

```
.\nssm start modmail
```

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

You should be able to see your bot running if everything goes well. You can also verify the status of your Modmail service with:

```
.\nssm status modmail
```

And if you specified the log output file in your previous step, you should be able to see your current Modmail logs like so:

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

And that's it! Your bot will now auto-start everytime you reboot your system. You can also additionally stop and restart your service with `.\nssm stop modmail` and `.\nssm restart modmail` respectively. Refer to [NSSM Documentation](http://nssm.cc/usage) for further customization as this guide is only meant to cover the basic needs adequate for standard Modmail usage.

## Updating

Your Modmail is set to auto-update itself by default, but you can also run the `?update` command on your bot manually, replacing `?` with your bot prefix.

If for some reason your update command isn't working correctly, you can update your bot by opening PowerShell or any terminal application in your modmail folder and pulling the latest changes from GitHub like so:

```
git pull
```

After that, simply restart your bot to apply the latest changes.
