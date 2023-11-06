---
description: Deploy Modmail on a macOS machine. (Tested with Apple Silicon M2)
---

# macOS

## Prerequisites

1. Minimum 2GB of RAM
2. At least 2GB available disk space.
3. Supported macOS version:
   - MacOS 14 Sonoma (Tested)
   - MacOS 11 Montery (Tested)

## Dependencies

We will be using the following dependencies:

* Python 3.10
* Tools: `git`, `homebrew`, `bash` or `zsh`
* Additional Modmail requirements: `cairo`, `libxml2`, `libxslt`, `libffi`

{% hint style="info" %}
All code blocks should be executed in bash and line by line unless specified otherwise.
{% endhint %}

To install these dependencies, we will be using Terminal (zsh or bash):

```bash
brew install python3 cairo libxml2 libxslt libffi
pip3 install cairosvg
```

After that, install `pipenv` with:

```bash
python3.10 -m pip install pipenv
```

## Installing Bot

Clone and change directory into the Modmail folder with:

```bash
git clone https://github.com/modmail-dev/modmail
cd modmail
```

Inside the Modmail folder, install `pipenv` and its Python packages with:

<pre class="language-bash"><code class="lang-bash"><strong>python3.10 -m pipenv install --python 3.10
</strong></code></pre>

Create a file named `.env` with `nano` and paste all the environmental variables (secrets) needed to run the bot via right-clicking in the nano editor. Refer to the steps in the [parent Installation page](../#preparing-your-environmental-variables) to find where to obtain these.

```bash
cp .env.example .env
nano .env
```

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

After that, close it and press "Yes" to save your changes. Exit the `nano` editor with `Ctrl+X`.

{% hint style="info" %}
If using the `nano` editor is a bit of a learning curve, you can edit the `.env` file manually with your preferred GUI-based editor like TextEdit.
{% endhint %}

After your `.env` file is ready, you can now go ahead and try running your bot with:

```bash
python3.10 -m pipenv run bot
```

If no error shows up, it means your bot is now running correctly. You can stop the bot from running with `Ctrl+C` to continue using your terminal.
