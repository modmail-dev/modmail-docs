---
description: Ways to setup auto restart for your bot on Windows hosts.
---

# Auto-Restart on Windows

## Using PM2 on Windows

Todo: [https://github.com/jessety/pm2-installer](https://github.com/jessety/pm2-installer)

## Using NSSM on Windows

To have the bot auto-restart on crash or system reboot, we will be using `nssm` by making a service for our bot application.

First, find the Python path of your Modmail pipenv by running `pipenv shell` and `which python` in your Modmail folder. Copy the path that appears in your terminal and paste it in the first line of our next step.

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

As `nssm` itself is only a command-line program, we'll need to use our trusty Terminal to use the application to create our service. So, search up "Powershell" in your start menu, right-click it and click "Run as Administrator".&#x20;

Change directory (CD) into the folder path that you copied earlier, the command should look like something like this:

```powershell
cd "C:\Users\Raiden\Downloads\nssm-2.24\win64"
```

{% hint style="info" %}
Wrapping "your folder\directory" on Windows in double quotes is necessary to make sure spaces in our file path is parsed correctly.
{% endhint %}

And then, proceed to create a new service for Modmail using `nssm` with:

```powershell
.\nssm install "Modmail"
```

A GUI will pop up where you can fill in the details needed for your Modmail service. Replace the `Path` with the path of your `modmail.bat` script and the `Startup directory` with the path of your Modmail folder as follow:

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

You can fill in these extra details as you see fit as it's only for your own reference:

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

You can also optionally specify a log file as output and error in the `I/O` tab, just be sure to create the file beforehand so you can select it in the GUI.

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

And finally, click "Install Service" to install your Modmail bot as a service on your Windows system.

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

By now you should have the service installed but not yet running. You can start it by using this command below in the open `nssm` Terminal from earlier:

```
.\nssm start modmail
```

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

You should be able to see your bot running if everything goes well. You can also verify the status of your Modmail service with:

```
.\nssm status modmail
```

And if you specified the log output file in your previous step, you should be able to see your current Modmail logs like so:

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

And that's it! Your bot will now auto-start everytime you reboot your system. You can also additionally stop and restart your service with `.\nssm stop modmail` and `.\nssm restart modmail` respectively. Refer to [NSSM Documentation](http://nssm.cc/usage) for further customization as this guide is only meant to cover the basic needs adequate for standard Modmail usage.