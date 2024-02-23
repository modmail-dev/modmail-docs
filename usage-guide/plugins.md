# Plugins

Visit the [Unofficial List of Plugins](https://docs.modmail.dev/old-docs/the-unofficial-list-of-plugins) for a list of plugins.

## Guidelines

To get approved and officially verified, you need to ensure you follow these guidelines:

* Supporting Python 3.8 (and above).
* No malicious intent.
* The plugin cannot be a feature pending to be added into [Modmail](https://github.com/modmail-dev/modmail/issues). You can submit a PR to add it to the core Modmail.
* Core Modmail still needs to 100% function.
* Cog name cannot be the same as any current class (`Core`, `Modmail`).
* It cannot have the same name as another approved plugin.

## Creating Plugins

We use [discord.py](https://discordpy.readthedocs.io/en/stable/) for the bot and plugins take the form of [Cogs](https://discordpy.readthedocs.io/en/stable/ext/commands/cogs.html).

Short example:

```py
from discord.ext import commands

class Hello(commands.Cog):
    def __init__(self, bot):
        self.bot = bot

    @commands.Cog.listener()
    async def on_message(self, message):
        print(message.content)

    @commands.command()
    async def say(self, ctx, *, message):
        await ctx.send(message)

async def setup(bot):
    await bot.add_cog(Hello(bot))
```

### Folder Structure

Your plugin has to be uploaded on Github on a **public repository.** (Note: private repositories are supported, but they require extra setup, see [Private Plugins](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token)). The repository folder structure has to be as follows:

```yaml
root:
    plugin_name:
        ..
        plugin_name.py
        requirements.txt [optional]
    plugin_name:
        ..
        plugin_name.py
        requirements.txt [optional]
```

The plugin will be loaded with something similar to

```py
await bot.load_extension('username.plugin_name.plugin_name')
```

To install a plugin that is not in the official registry, type:

```
?plugin add githubusername/plugin_repo/plugin_name[@branch]
```

An example of a plugin can be seen at [`fourjr/modmail-plugins`](https://github.com/fourjr/modmail-plugins) or any of the plugins in our [registry](https://github.com/modmail-dev/modmail/blob/master/plugins/registry.json).

#### Branch parameter

The branch parameter is **optional** (default to `master`) and can be used to test in-development/unstable plugins with a development branch.

Users will always be updated to the latest version. Thus, if there is a broken plugin on the latest version, users would not be able to use the plugin.

#### @local (For Developers)

To make it easier to develop a plugin, there's a folder named `@local` in the plugins folder. You can directly put a folder for each plugin in it.

Using the example cog above, the load command would be

```
?plugin load @local/hello
```

#### Best Practices

1. Create a development branch
2. Push to it until you are confident that your code is stable
3. Merge it into `master` using pull requests or `git merge -v dev --squash`
4. Update your plugin!

### Private Plugins

* Obtain a [Github Personal Access Token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) with `repo` scope
* Include `GITHUB_TOKEN` as a config variable (or in .env) with the token as the value.
* Upload your code to a private Github repository.
* Install just like a normal public plugin.

### Database Interfacing

Do **not** interact with `bot.api` directly. Fetch a partition and use it:

```python
def __init__(self, bot):  # in the class init
    self.coll = bot.api.get_plugin_partition(self)
```

`self.coll` is a [motor.motor\_asyncio.AsyncIOMotorCollection](https://motor.readthedocs.io/en/stable/api-asyncio/asyncio\_motor\_collection.html)

### Additional PIP requirements

Create a [`requirements.txt` file](https://pip.pypa.io/en/stable/user\_guide/#requirements-files) in the plugin folder. Packages listed here would be installed via something similar to the following command:

```
python3 -m pip install -r requirements.txt --user -q -q
```

### Exposed Events

The bot dispatches custom events to aid plugin developers to extend Modmail functionality.

Currently, we have these custom coroutines:

* `Bot.format_channel_name(bot, author, exclude_channel=None, force_null=False)` can be overwritten for custom behaviour.
* `on_plugins_ready()` which is dispatched when all the plugins are fully loaded and ready to be used.
* `on_thread_initiate(thread, creator, category, initial_message)` which is dispatched at the beginning of setup process. It is recommended to use the other events instead.
* `on_thread_create(thread)` which is dispatched when the thread is registered as a thread by Modmail (i.e., when channel topic is edited).
* `on_thread_ready(thread, creator, category, initial_message)` which is dispatched when a thread channel is created and the `genesis_message` (info embed) is sent. It is recommended to use this event.
* `on_thread_close(thread, closer, silent, delete_channel, message, scheduled)` which is dispatched when a thread is closed, after channel deletion.
* `on_thread_reply(thread, from_mod, message, anonymous, plain)` which is dispatched upon any reply.

e.g.

```py
@commands.Cog.listener()
async def on_thread_ready(self, thread, creator, category, initial_message):
    msg = thread.genesis_message
    ... # do stuff
```

### Approval request

Create a [Pull Request](https://github.com/modmail-dev/modmail/pulls) adding your plugin into [`plugins/registry.json`](https://github.com/modmail-dev/modmail/blob/master/plugins/registry.json) and we will take a look at it.
