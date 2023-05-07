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

###
