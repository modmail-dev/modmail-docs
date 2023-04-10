---
description: Configuring and customizing modmail.
---

Modmail offers an assort of customizations to make your Modmail bot unique to your server. Most customizations can be set with `?config`, but some has its own special command, such as `?activity`.
You may find all of the personalizable tweaks available for Modmail below:

{% hint style="info" %} All examples presume your prefix is `?`.{% endhint %}

{% hint style="warning" %} Things covered in brackets are optional: `[]`
Things covered in angled brackets are required: `<>`  {% endhint %}


Moderation Configurations
======

Account Age ( account_age )
------

***Default:*** No Age Threshold 

Set an amount of time a users account has to be created in order to open a ticket. 

***Example:***

- `?config set account_age P12DT3H` (stands for 12 days and 3 hours in [ISO-8601 Duration Format](https://en.wikipedia.org/wiki/ISO_8601#Durations))
- `?config set account_age 3 days and 5 hours` (accepted readable time)

***Note(s):***
- To remove this restriction, do ?config del account_age.
- See also: `guild_age`.


Alert on Mention ( alert_on_mention )
------

***Default: No***

Mentions all mods (mention) in mention channel when bot is mentioned

***Example:***

- `?config set alert_on_mention yes`

***Notes:***
- See also: `mention`, `mention_channel_id`


Reply Without Command ( reply_without_command )
------

***Default:*** Disabled

Setting this configuration will make all non-command messages sent in the thread channel to be forwarded to the recipient without the need of `?reply`.

***Example:*** 
- `?config set reply_without_command yes`
- `?config set reply_without_command no`

***Notes:***
- See also: `anon_reply_without_command`, `plain_reply_without_command`.


Show Timestamps ( show_timestamp )
------

***Default:*** Yes

Shows timestamps on thread embeds

***Example:*** 

- `?config set show_timestamp no`


Silent Alert On Commands ( silent_alert_on_mention )
------

Send a message in the mention channel without mentioning all mods (mention).

***Default:*** No 

***Example:*** 
- `?config set alert_on_mention yes`

***Notes:***
This has no effect unless `alert_on_mention` is set to yes.
See also: `mention`, `mention_channel_id`


Update Channel ID ( update_channel_id )
------

This is the channel where update notifications are sent to.

***Default:*** Log Channel (normally `#bot-logs`)

***Example:*** 
- `?config set update_channel_id 9234932582312` (9234932582312 is the channel ID)`

***Notes:***
- This has no effect unless `disable_autoupdates` is set to no and `update_notifications` is set to yes.
- See also: `log_channel_id`


Update Notifications ( update_notifications )
------

This is the channel where update notifications are sent to.

***Default:*** Yes 

***Example:*** 
- `?config set update_notifications no`

***Notes:***
- This has no effect unless `disable_autoupdates` is set to no.
- See also: `update_channel_id`


Fallback Category ID ( fallback_category_id )
------

This is the category that will hold the threads when the main category is full.\n\nTo change the Fallback category, you will need to find the [category’s ID](https://support.discordapp.com/hc/en-us/articles/206346498).

***Default:*** `Fallback Modmail` (created when the main category is full)

***Example:*** 
- `?config set fallback_category_id 9234932582312` (`9234932582312` is the category ID)

***Notes:***
- If the Fallback category ended up being non-existent/invalid, Modmail will create a new one. To fix this, set `fallback_category_id` to a valid category.
- See also: `main_category_id`.


Log Channel ID ( log_channel_id )
------

This is the channel where all log messages will be sent (ie. thread close message, update message, etc.).\n\nTo change the log channel, you will need to find the [channel’s ID](https://support.discordapp.com/hc/en-us/articles/206346498). The channel doesn’t necessary have to be under the `main_category`.

***Default:*** `#bot-logs` (created with `{prefix}setup`)

***Example:*** 
- `?config set log_channel_id 9234932582312` (9234932582312 is the channel ID)

***Notes:*** 
- If the Modmail logging channel ended up being non-existent/invalid, no logs will be sent.

Main Category ID ( main_category_id )
------

This is the category where all new threads will be created.\n\nTo change the Modmail category, you will need to find the [category’s ID](https://support.discordapp.com/hc/en-us/articles/206346498).

***Default:*** `Modmail` (created with `{prefix}setup`)

***Example:*** 
- `?config set main_category_id 9234932582312` (`9234932582312` is the category ID)`

***Notes:***
- If the Modmail category ended up being non-existent/invalid, Modmail will break. To fix this, run `?setup` again or set `main_category_id` to a valid category.
- When the Modmail category is full, new channels will be created in the fallback category.
- See also: `fallback_category_id`

Mod Typing ( mod_typing )
------

When this is set to `yes`, whenever a moderator starts to type in the thread channel, the recipient user will see \"{bot.user.display_name} is typing…\" in their DM channel.

***Default:*** Disabled

***Example:*** 
- `{prefix}config set mod_typing yes`
- `{prefix}config set mod_typing no`

***Notes:***
- See also: `mod_typing`

User Typing ( user_typing )
------

When this is set to `yes`, whenever the recipient user starts to type in their DM channel, the moderator will see “{bot.user.display_name} is typing…” in the thread channel.

***Default:*** Enabled

***Example:*** 
- `?config set user_typing yes`
- `?config set user_typing no`

***Notes:***
- See also: `mod_typing`.

Twitch URL ( twitch_url )
------

This channel dictates the linked Twitch channel when the activity is set to \"Streaming\".

***Default:*** `https://www.twitch.tv/discordmodmail/`

***Example:***
- `?config set twitch_url https://www.twitch.tv/yourchannelname/`

***Notes:***
- This has no effect when the activity is not set to \"Streaming\".
- See also: `?help activity`

Close On Leave ( close_on_leave )
------

Closes a modmail thread upon user leave automatically

***Default:*** No 

***Example:*** 
- `?config set close_on_leave yes`

***Notes:***
- See also: `close_on_leave_reason`.

Confirm Thread Creation ( confirm_thread_creation )
------

Ensure users confirm that they want to create a new thread

***Default:*** No 

***Example:*** 
- `?config set confirm_thread_creation yes`

***Notes:***
- See also: `confirm_thread_creation_title`, `confirm_thread_response`, `confirm_thread_creation_accept`, `confirm_thread_creation_deny`

Mention ( mention )
------

This is the message above user information for when a new thread is created in the channel.

***Default:*** `@here`

***Example:*** 
- `?config set mention Yo~ Here's a new thread for ya!`
- `?mention Yo~ Here's a new thread for ya!`

***Notes:***
- To disable mention, use command `{prefix}mention disable`.
- See also: `{prefix}help mention`.

Require Close Reason ( require_close_reason )
------

Require a reason to close threads.

***Default:*** No 

***Example:*** 
- `?config set require_close_reason yes`


Thread Auto Close ( thread_auto_close )
------

Setting this configuration will close threads automatically after the number of days, hours, minutes or any time-interval specified by this configuration.

***Default:*** Never 

***Example:*** 
- `?config set thread_auto_close P12DT3H` (stands for 12 days and 3 hours in [ISO-8601 Duration Format](https://en.wikipedia.org/wiki/ISO_8601#Durations))
- `?config set thread_auto_close 3 days and 5 hours` (accepted readable time)

***Notes:***
- To disable auto close, do `{prefix}config del thread_auto_close`.
- To prevent a thread from auto-closing, do `{prefix}close cancel`.
- See also: `thread_auto_close_silently`, `thread_auto_close_response`.

Thread Cooldown ( thread_cooldown )
------

Specify the time required for the recipient to wait before allowed to create a new thread.

***Default:*** Never 

***Example:*** 
- `?config set thread_cooldown P12DT3H` (stands for 12 days and 3 hours in [ISO-8601 Duration Format](https://en.wikipedia.org/wiki/ISO_8601#Durations))
- `?config set thread_cooldown 3 days and 5 hours` (accepted readable time)

***Notes:***
- To disable thread cooldown, do `?config del thread_cooldown`.


Thread Move Notify ( thread_move_notify )
------

Notify the recipient if the thread was moved.

***Default:*** No 

***Example:***
- `?config set thread_move_notify yes`
- `?config set thread_move_notify no`

***Notes:***
- See also: `thread_move_title`, `thread_move_response`, `thread_move_notify_mods`.

Thread Move Notify Mods ( thread_move_notify_mods )
------

Notify mods again after the thread is moved

***Default:*** No 

***Example:*** 
- `?config set thread_move_notify_mods yes`
- `?config set thread_move_notify_mods no`

***Notes:***
- See also: `thread_move_title`, `thread_move_response`, `thread_move_notify`.

Use Regex Autotrigger ( use_regex_autotrigger )
------

Whether to use regex to compare in autotriggers.

***Default:*** No 

***Example:***
- `?config set use_regex_autotrigger yes`

***Notes:***

{% hint style="danger" %} This is meant for advanced user that understand regular expressions. {% endhint %}

- You can test it out with https://regexr.com on `PCRE (Server)` mode
- See command: `autotrigger`

Plain Reply Without Command ( plain_reply_without_command )
------

Setting this configuration will make all non-command messages sent in the thread channel to be forwarded to the recipient in a plain form without the need of `{prefix}reply`.

***Default:*** Disabled 

***Example:*** 
- `?config set plain_reply_without_command yes`
- `?config set plain_reply_without_command no`

***Notes:***
- See also: `reply_without_command`, `anon_reply_without_command`.

Anonymous Snippets ( anonymous_snippets )
------

Sends snippets anonymously.

***Default:*** No 

***Example:*** 
- `?config set anonymous_snippets yes`

***Notes:***
- See also: `anon_avatar_url`, `anon_tag`, `plain_snippets`.

Appearance Configurations
======

Blocked Emoji ( blocked_emoji )
------

This is the emoji added to the message when when a Modmail action is invoked unsuccessfully (ie. DM Modmail when blocked, failed to reply, etc.).

***Default:*** 🚫

***Example:***
- `?config set blocked_emoji 🙅‍`

***Notes:***
- You can disable `blocked_emoji` with `{prefix}config set blocked_emoji disable`.
- Custom/animated emojis are also supported, however, the emoji must be added to the server.
- See also: `sent_emoji`.

Close Emoji ( close_emoji )
------

This is the emoji the recipient can click to close a thread themselves. The emoji is automatically added to the `thread_creation_response` embed.

***Default:*** 🔒

***Example:***
- `?config set close_emoji 👍‍`

***Notes:***
- This will only have an effect when `recipient_thread_close` is enabled.
- See also: `recipient_thread_close`.

Confirm Thread Creation Accept ( confirm_thread_creation_accept )
------

Emoji to accept thread creation  

***Default:*** \u2705

***Example:***
- `?config set confirm_thread_creation_accept \u2611`

***Notes:***
- This has no effect unless `confirm_thread_creation` is set
- See also: `confirm_thread_creation`, `confirm_thread_creation_title`, `confirm_thread_response`, `confirm_thread_creation_deny`

Confirm Thread Creation Deny ( confirm_thread_creation_deny )
------

Emoji to cancel thread creation  

***Default:*** \uD83D\uDEAB

***Example:*** 
- `?config set confirm_thread_creation_deny \u26D4`

***Notes:***
- This has no effect unless `confirm_thread_creation` is set
- See also: `confirm_thread_creation`, `confirm_thread_creation_title`, `confirm_thread_response`, `confirm_thread_creation_accept`

Error Color ( error_color )
------

This is the color for Modmail when anything goes wrong, unsuccessful commands, or a stern warning. 

***Default:*** Discord Red [#E74C3C](https://placehold.it/100/e74c3c?text=+)

***Example:***
- `?config set error_color ocean blue`
- `?config set error_color ff1242`
- `?config set error_color #ff1242`
- `?config set error_color fa1`

***Notes:***
- Available color names can be found on [Color Options](https://docs.modmail.dev/old-docs/color-names).
- See also: `main_color`, `mod_color`, `recipient_color`.


Main Color ( main_color )
------

This is the main color for Modmail (help/about/ping embed messages, subscribe, move, etc.). 

***Default:*** Discord Blurple [#7289DA](https://placehold.it/100/7289da?text=+)

***Example:***
- `?config set main_color olive green`
- `?config set main_color 12de3a`
- `?config set main_color #12de3a`
- `?config set main_color fff`

***Notes:***
- Available color names can be found on [Color Options](https://docs.modmail.dev/old-docs/color-names).
- See also: `error_color`, `mod_color`, `recipient_color`.


Mod Color ( mod_color )
------

This is the color of the messages sent by the moderators, this applies to messages within in the thread channel and the DM thread messages received by the recipient. 

***Default:*** Discord Green [#2ECC71](https://placehold.it/100/2ecc71?text=+)

***Example:***
- `?config set mod_color dark beige`
- `?config set mod_color cb7723`
- `?config set mod_color #cb7723`
- `?config set mod_color c4k`

***Notes:***
- Available color names can be found on [Color Options](https://docs.modmail.dev/old-docs/color-names).
- See also: `recipient_color`, `main_color`, `error_color`.

React To Contact Emoji ( react_to_contact_emoji )
------

An emoji which is tracked in `react_to_contact_message` 

***Default:*** \u2705

***Example:***
- `?config set react_to_contact_emoji \u2705`

***Notes:***
- See also: `react_to_contact_message \u2705`

Recipient Color ( recipient_color )
------

This is the color of the messages sent by the recipient, this applies to messages received in the thread channel.

***Default:*** "Discord Gold [#F1C40F](https://placehold.it/100/f1c40f?text=+)

***Example:***
- `?config set recipient_color dark beige`
- `?config set recipient_color cb7723`
- `?config set recipient_color #cb7723`
- `?config set recipient_color c4k`

***Notes:***
- Available color names can be found on [Color Options](https://docs.modmail.dev/old-docs/color-names).
- See also: `mod_color`, `main_color`, `error_color`.

Sent Emoji ( sent_emoji )
------

This is the emoji added to the message when when a Modmail action is invoked successfully (ie. DM Modmail, edit message, etc.).

***Default:*** ✅

***Example:***
- `?config set sent_emoji ✨`

***Notes:***
- You can disable `sent_emoji` with `{prefix}config set sent_emoji disable`.
- Custom/animated emojis are also supported, however, the emoji must be added to the server.
- See also: `blocked_emoji`.

Show Log URL Button ( show_log_url_button )
------

Shows the button to open the Log URL.

***Default:*** No

***Example:***
- `?config set show_log_url_button yes`


Thread Appearance
======

Use Random Channel Name ( use_random_channel_name )
------

When this is set to `yes`, new thread channels will be named with random characters tied to their user ID. 

***Default:*** No

***Example:***
- `?config set use_random_channel_name yes`
- `?config set use_random_channel_name no`

***Notes:***
{% hint style="warning" %} This config is suitable for servers in Server Discovery to comply with channel name restrictions. {% endhint %}
{% hint style="danger" %} This cannot be applied with `use_timestamp_channel_name`, `use_nickname_channel_name`, or `use_user_id_channel_name`. {% endhint %}
- See also: `use_timestamp_channel_name`, `use_user_id_channel_name`, `use_nickname_channel_name`.

Use Timestamp Channel Name  ( use_timestamp_channel_name )
------

When this is set to `yes`, new thread channels will be named with the recipient's account creation date instead of the recipient's name. 

***Default:*** No

***Example:***
- `?config set use_timestamp_channel_name yes`
- `?config set use_timestamp_channel_name no`

***Notes:***
{% hint style="warning" %} This config is **NOT** suitable for servers in Server Discovery to comply with channel name restrictions. {% endhint %}
{% hint style="danger" %} This cannot be applied with `use_user_id_channel_name`, `use_random_channel_name` or `use_nickname_channel_name`. {% endhint %}
- See also: `use_user_id_channel_name`, `use_nickname_channel_name`, `use_random_channel_name`.

Use User ID Channel Name ( use_user_id_channel_name )
------

When this is set to `yes`, new thread channels will be named with the recipient's ID instead of the recipient's name. 

***Default:*** No 

***Example:***
- `?config set use_user_id_channel_name yes`
- `?config set use_user_id_channel_name no`

***Notes:***
{% hint style="warning" %} This config is suitable for servers in Server Discovery to comply with channel name restrictions. {% endhint %}
{% hint style="danger" %} This cannot be applied with `use_timestamp_channel_name`, `use_random_channel_name` or `use_nickname_channel_name`. {% endhint %}
- See also: `use_timestamp_channel_name`, `use_nickname_channel_name`, `use_random_channel_name`.

Use Nickname Channel Name ( use_nickname_channel_name )
------

When this is set to `yes`, new thread channels will be named with the recipient's nickname instead of the recipient's name. 

***Default:***

***Example:***
- `?config set use_nickname_channel_name yes`
- `?config set use_nickname_channel_name no`

***Notes:***
{% hint style="warning" %} This config is suitable for servers in Server Discovery to comply with channel name restrictions. {% endhint %}
{% hint style="danger" %} This cannot be applied with `use_timestamp_channel_name`, `use_random_channel_name` or `use_user_id_channel_name`. {% endhint %}
- See also: `use_timestamp_channel_name`, `use_user_id_channel_name`, `use_random_channel_name`.

Use Hoisted Top Role ( use_hoisted_top_role )
------

Controls if only hoisted roles are evaluated when finding top role. 

***Default:*** Yes 

***Example:***
- `?config set use_hoisted_top_role yes`
- `?config set use_hoisted_top_role no`

***Notes:***
- Top role is displayed in embeds when replying or adding/removing users to a thread in the case mod_tag and anon_username are not set.
- If this configuration is enabled, only roles that are hoisted (displayed seperately in member list) will be used. If a user has no hoisted roles, it will return 'None'.
- If you would like to display the top role of a user regardless of if it's hoisted or not, disable `use_hoisted_top_role`.

Thread Show Account Age ( thread_show_account_age )
------

Shows account age on first message sent in thread channels to mods 

***Default:*** Yes

***Example:***
- `?config set thread_show_account_age no`

***Notes:***
- See also: `thread_show_roles`, `thread_show_join_age`


Thread Show Join Age ( thread_show_join_age )
------

Shows join age on first message sent in thread channels to mods 

***Default:*** Yes 

***Example:***
- `?configconfig set thread_show_join_age no`

***Notes:***
- See also: `thread_show_account_age`, `thread_show_roles`.


Thread Show Roles ( thread_show_roles )
------

Shows roles on first message sent in thread channels to mods 

***Default:*** Yes

***Example:***
- `?config set thread_show_account_age no`

***Notes:***
- See also: `thread_show_roles`, `thread_show_join_age`.


Mod Tag ( mod_tag )
------

This is the name tag in the “footer” section of the embeds sent by moderators in the recipient DM and thread channel. 

***Default:*** The moderator's highest role

***Example:***
- `?config set mod_tag Moderator`

***Notes:***
{% hint style="warning" %} When the message is sent anonymously, `anon_tag` is used instead. {% endhint %}
- See also: `anon_tag`.

Anon Tag ( anon_tag )
------

This is the name tag in the “footer” section of the embeds sent by anonymous moderators in the recipient DM. 

***Default:*** \"Response\"

***Example:***
- `?config set anon_tag Support Agent`

***Notes:***
- See also: `anon_avatar_url`, `anon_username`, `mod_tag`.

Anon Avatar URL ( anon_avatar_url )
------

This is the avatar of the embeds sent by anonymous moderators in the recipient DM. 

***Default:*** Server avatar

***Example:***
- `?config set anon_avatar_url https://path.to/your/avatar.png` (you will need to upload the avatar to somewhere)

***Notes:***
- See also: `anon_username`, `anon_tag`.


Anon Username ( anon_username )
------

This is the name in the “author” section of the embeds sent by anonymous moderators in the recipient DM. 

***Default:*** Fallback on `mod_tag`

***Example:***
- `?config set anon_username Incognito Mod`

***Notes:***
- See also: `anon_avatar_url`, `anon_tag`.


Transfer Reactions ( transfer_reactions )
------

Transfer users reactions to mods and vice versa
*(If someone reacts to a thread message the other party will see it.)* 

***Default:*** Yes 

***Example:***
- `?config set transfer_reactions no`


Thread Responses 
======

TODO / In Progress 

`.env` Config Options
======
#### The following is a list of config options that can *ONLY* be added by editing the `.env` file. Please use whichever guide you followed to set up the bot to see how to add these variables. 

{% hint style="danger" %} It is recommended you avoid and ignore changing any of these you do not fully understand {% endhint %}

| Option        | Description | Required | Usage |
| ------------- |:-------------:|:-------------:|:-------------:|
| modmail_guild_id  | Inbox server for tickets | No | `MODMAIL_GUILD_ID = GUILDIDHERE` |
| guild_id  | Main server the bot is in | Yes | `GUILD_ID = GUILDIDHERE` |
| log_url_prefix  | Default is `/logs` | Yes | `LOG_URL_PREFIX = PREFIX` |
| mongo_uri  | The connection uri for the database | Yes | `MONGO_URI = mongodb+srv://Papiersnipper:mypassword123@modmail-rdm99.mongodb.net/` |
| connection_uri  | The connection uri for the database | Yes | `CONNECTION_URI = mongodb+srv://Papiersnipper:mypassword123@modmail-rdm99.mongodb.net/` |
| owners  | ID's of the users who will have owner perms | Yes | `OWNERS = 1234,5678,91011` |
| enable_presence_intent  | Enables the presence intent, required for some plugins. Uses extra resources. | No | `ENABLE_PRESENCE_INTENT = True` |
| registry_plugins_only  | Disallows the ability to download plugins that aren’t in the plugin registry. | No | `REGISTRY_PLUGINS_ONLY = True` |
| token  | The bots token | Yes | `TOKEN = MTAyMjk2NTA4MzYxtewgw3eNw.thisis.afaketoken-WGjwfvQ` |
| enable_eval  | Enables the eval command to run arbitrary code on the bot. | No | `ENABLE_EVAL = True` |
| github_token  | Needed to use the update command | No | `GITHUB_TOKEN = ghp_ABC132gfdsg4321fds` |
| disable_autoupdates  | Allows for auto updates | No | `DISABLE_AUTOUPDATES = True` |
| disable_updates  | Disables updates all together  | No | `DISABLE_UPDATES = True` |
| log_level  | The type of information posted in the terminal, Default is `INFO` | No | `LOG_LEVEL = ERROR/WARNING/INFO/DEBUG/NOTSET` |

