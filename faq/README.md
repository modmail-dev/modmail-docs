---
description: A list of commonly asked questions or problems related to Modmail.
---

# Frequently Asked Questions

### I tried installing the dependencies with another Python version and it messed up my Pipfile! How can I get the original Pipfile back?

First remove the broken `Pipfile` and `Pipfile.lock` with:

```bash
rm Pipfile && rm Pipfile.lock
```

Fetch in the changes from the remote repository:

```bash
git fetch origin
```

And then, fetch the original files with:

```bash
git checkout FETCH_HEAD -- Pipfile && git checkout FETCH_HEAD -- Pipfile.lock
```

### I would like to have threads in a seperate guild inbox, how can I do that?

If you want to use a separate server to the main one as the inbox server (Where threads get relayed to) add the following environment variables into your ``.env`` file:

* `MODMAIL_GUILD_ID` (the server where messages are sent to)
* `GUILD_ID` (The server where users message from)
