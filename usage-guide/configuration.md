---
description: Configuring and customizing modmail.
---

# Configuration

Modmail offers an assort of customizations to make your Modmail bot unique to your server. Most customizations can be set with `?config`, but some has its own special command, such as `?activity`. You may find all of the personalizable tweaks available for Modmail below:

{% hint style="info" %}
All examples presume your prefix is \`?\`.
{% endhint %}

{% hint style="warning" %}
Things covered in brackets are optional: \`\[]\` Things covered in angled brackets are required: \`<>\`
{% endhint %}

**Quick Navigation:**

**Moderation:**

* [Prefix](configuration.md)
* [Mention](usage-guide/configuration/#mention-mention)

## Moderation Configurations

### Account Age ( account\_age )

_**Default:**_ No Age Threshold

Set an amount of time a users account has to be created in order to open a ticket.

_**Example:**_

* `?config set account_age P12DT3H` (stands for 12 days and 3 hours in [ISO-8601 Duration Format](https://en.wikipedia.org/wiki/ISO\_8601#Durations))
* `?config set account_age 3 days and 5 hours` (accepted readable time)

_**Note(s):**_

* To remove this restriction, do ?config del account\_age.
* See also: `guild_age`.

### Alert on Mention ( alert\_on\_mention )

_**Default:**_ No

Mentions all mods (mention) in mention channel when bot is mentioned

_**Example:**_

* `?config set alert_on_mention yes`

_**Notes:**_

* See also: `mention`, `mention_channel_id`

### Prefix ( prefix )

The prefix of the bot

_**Default:**_ `?`

_**Example:**_

* `?config set prefix !`
* `?prefix !`

This both result in commands now prefixed with !, for example:

{% hint style="success" %}
!about
{% endhint %}

_**Notes:**_

* If you forgot the bot prefix, Modmail will always respond to its mention (ping).
* To reset the prefix back to default: `?config del prefix`

### Guild Age ( guild\_age )

The join date of the recipient user into this server must be greater than the number of days, hours, minutes or any time-interval specified by this configuration.

_**Default:**_ No age threshold

_**Example:**_

* `?config set guild_age P12DT3H` (stands for 12 days and 3 hours in [ISO-8601 Duration Format](https://en.wikipedia.org/wiki/ISO\_8601#Durations))
* `?config set guild_age 3 days and 5 hours` (accepted readable time)

_**Notes:**_

* To remove this restriction, do `{prefix}config del guild_age`.
* See also: `account_age`.

### Reply Without Command ( reply\_without\_command )

_**Default:**_ Disabled

Setting this configuration will make all non-command messages sent in the thread channel to be forwarded to the recipient without the need of `?reply`.

_**Example:**_

* `?config set reply_without_command yes`
* `?config set reply_without_command no`

_**Notes:**_

* See also: `anon_reply_without_command`, `plain_reply_without_command`.

### Show Timestamps ( show\_timestamp )

_**Default:**_ Yes

Shows timestamps on thread embeds

_**Example:**_

* `?config set show_timestamp no`

### Silent Alert On Commands ( silent\_alert\_on\_mention )

Send a message in the mention channel without mentioning all mods (mention).

_**Default:**_ No

_**Example:**_

* `?config set alert_on_mention yes`

_**Notes:**_ This has no effect unless `alert_on_mention` is set to yes. See also: `mention`, `mention_channel_id`

### Update Channel ID ( update\_channel\_id )

This is the channel where update notifications are sent to.

_**Default:**_ Log Channel (normally `#bot-logs`)

_**Example:**_

* `?config set update_channel_id 9234932582312` (9234932582312 is the channel ID)\`

_**Notes:**_

* This has no effect unless `disable_autoupdates` is set to no and `update_notifications` is set to yes.
* See also: `log_channel_id`

### Update Notifications ( update\_notifications )

This is the channel where update notifications are sent to.

_**Default:**_ Yes

_**Example:**_

* `?config set update_notifications no`

_**Notes:**_

* This has no effect unless `disable_autoupdates` is set to no.
* See also: `update_channel_id`

### Fallback Category ID ( fallback\_category\_id )

This is the category that will hold the threads when the main category is full.\n\nTo change the Fallback category, you will need to find the [category’s ID](https://support.discordapp.com/hc/en-us/articles/206346498).

_**Default:**_ `Fallback Modmail` (created when the main category is full)

_**Example:**_

* `?config set fallback_category_id 9234932582312` (`9234932582312` is the category ID)

_**Notes:**_

* If the Fallback category ended up being non-existent/invalid, Modmail will create a new one. To fix this, set `fallback_category_id` to a valid category.
* See also: `main_category_id`.

### Log Channel ID ( log\_channel\_id )

This is the channel where all log messages will be sent (ie. thread close message, update message, etc.).\n\nTo change the log channel, you will need to find the [channel’s ID](https://support.discordapp.com/hc/en-us/articles/206346498). The channel doesn’t necessary have to be under the `main_category`.

_**Default:**_ `#bot-logs` (created with `?setup`)

_**Example:**_

* `?config set log_channel_id 9234932582312` (9234932582312 is the channel ID)

_**Notes:**_

* If the Modmail logging channel ended up being non-existent/invalid, no logs will be sent.

### Main Category ID ( main\_category\_id )

This is the category where all new threads will be created.\n\nTo change the Modmail category, you will need to find the [category’s ID](https://support.discordapp.com/hc/en-us/articles/206346498).

_**Default:**_ `Modmail` (created with `?setup`)

_**Example:**_

* `?config set main_category_id 9234932582312` (`9234932582312` is the category ID)\`

_**Notes:**_

* If the Modmail category ended up being non-existent/invalid, Modmail will break. To fix this, run `?setup` again or set `main_category_id` to a valid category.
* When the Modmail category is full, new channels will be created in the fallback category.
* See also: `fallback_category_id`

### Mod Typing ( mod\_typing )

When this is set to `yes`, whenever a moderator starts to type in the thread channel, the recipient user will see "{bot.user.display\_name} is typing…" in their DM channel.

_**Default:**_ Disabled

_**Example:**_

* `?config set mod_typing yes`
* `?config set mod_typing no`

_**Notes:**_

* See also: `mod_typing`

### User Typing ( user\_typing )

When this is set to `yes`, whenever the recipient user starts to type in their DM channel, the moderator will see “{bot.user.display\_name} is typing…” in the thread channel.

_**Default:**_ Enabled

_**Example:**_

* `?config set user_typing yes`
* `?config set user_typing no`

_**Notes:**_

* See also: `mod_typing`.

### Twitch URL ( twitch\_url )

This channel dictates the linked Twitch channel when the activity is set to "Streaming".

_**Default:**_ `https://www.twitch.tv/discordmodmail/`

_**Example:**_

* `?config set twitch_url https://www.twitch.tv/yourchannelname/`

_**Notes:**_

* This has no effect when the activity is not set to "Streaming".
* See also: `?help activity`

### Close On Leave ( close\_on\_leave )

Closes a modmail thread upon user leave automatically

_**Default:**_ No

_**Example:**_

* `?config set close_on_leave yes`

_**Notes:**_

* See also: `close_on_leave_reason`.

### Confirm Thread Creation ( confirm\_thread\_creation )

Ensure users confirm that they want to create a new thread

_**Default:**_ No

_**Example:**_

* `?config set confirm_thread_creation yes`

_**Notes:**_

* See also: `confirm_thread_creation_title`, `confirm_thread_response`, `confirm_thread_creation_accept`, `confirm_thread_creation_deny`

### Mention ( mention )

This is the message above user information for when a new thread is created in the channel.

_**Default:**_ `@here`

_**Example:**_

* `?config set mention Yo~ Here's a new thread for ya!`
* `?mention Yo~ Here's a new thread for ya!`

_**Notes:**_

* To disable mention, use command `?mention disable`.
* See also: `?help mention`.

### Require Close Reason ( require\_close\_reason )

Require a reason to close threads.

_**Default:**_ No

_**Example:**_

* `?config set require_close_reason yes`

### Thread Auto Close ( thread\_auto\_close )

Setting this configuration will close threads automatically after the number of days, hours, minutes or any time-interval specified by this configuration.

_**Default:**_ Never

_**Example:**_

* `?config set thread_auto_close P12DT3H` (stands for 12 days and 3 hours in [ISO-8601 Duration Format](https://en.wikipedia.org/wiki/ISO\_8601#Durations))
* `?config set thread_auto_close 3 days and 5 hours` (accepted readable time)

_**Notes:**_

* To disable auto close, do `?config del thread_auto_close`.
* To prevent a thread from auto-closing, do `?close cancel`.
* See also: `thread_auto_close_silently`, `thread_auto_close_response`.

### Thread Cooldown ( thread\_cooldown )

Specify the time required for the recipient to wait before allowed to create a new thread.

_**Default:**_ Never

_**Example:**_

* `?config set thread_cooldown P12DT3H` (stands for 12 days and 3 hours in [ISO-8601 Duration Format](https://en.wikipedia.org/wiki/ISO\_8601#Durations))
* `?config set thread_cooldown 3 days and 5 hours` (accepted readable time)

_**Notes:**_

* To disable thread cooldown, do `?config del thread_cooldown`.

### Thread Move Notify ( thread\_move\_notify )

Notify the recipient if the thread was moved.

_**Default:**_ No

_**Example:**_

* `?config set thread_move_notify yes`
* `?config set thread_move_notify no`

_**Notes:**_

* See also: `thread_move_title`, `thread_move_response`, `thread_move_notify_mods`.

### Thread Move Notify Mods ( thread\_move\_notify\_mods )

Notify mods again after the thread is moved

_**Default:**_ No

_**Example:**_

* `?config set thread_move_notify_mods yes`
* `?config set thread_move_notify_mods no`

_**Notes:**_

* See also: `thread_move_title`, `thread_move_response`, `thread_move_notify`.

### Use Regex Autotrigger ( use\_regex\_autotrigger )

Whether to use regex to compare in autotriggers.

_**Default:**_ No

_**Example:**_

* `?config set use_regex_autotrigger yes`

_**Notes:**_

{% hint style="danger" %}
This is meant for advanced user that understand regular expressions.
{% endhint %}

* You can test it out with https://regexr.com on `PCRE (Server)` mode
* See command: `autotrigger`

### Plain Reply Without Command ( plain\_reply\_without\_command )

Setting this configuration will make all non-command messages sent in the thread channel to be forwarded to the recipient in a plain form without the need of `?reply`.

_**Default:**_ Disabled

_**Example:**_

* `?config set plain_reply_without_command yes`
* `?config set plain_reply_without_command no`

_**Notes:**_

* See also: `reply_without_command`, `anon_reply_without_command`.

### Anonymous Snippets ( anonymous\_snippets )

Sends snippets anonymously.

_**Default:**_ No

_**Example:**_

* `?config set anonymous_snippets yes`

_**Notes:**_

* See also: `anon_avatar_url`, `anon_tag`, `plain_snippets`.

## Appearance Configurations

### Blocked Emoji ( blocked\_emoji )

This is the emoji added to the message when when a Modmail action is invoked unsuccessfully (ie. DM Modmail when blocked, failed to reply, etc.).

_**Default:**_ 🚫

_**Example:**_

* `?config set blocked_emoji 🙅‍`

_**Notes:**_

* You can disable `blocked_emoji` with `?config set blocked_emoji disable`.
* Custom/animated emojis are also supported, however, the emoji must be added to the server.
* See also: `sent_emoji`.

### Close Emoji ( close\_emoji )

This is the emoji the recipient can click to close a thread themselves. The emoji is automatically added to the `thread_creation_response` embed.

_**Default:**_ 🔒

_**Example:**_

* `?config set close_emoji 👍‍`

_**Notes:**_

* This will only have an effect when `recipient_thread_close` is enabled.
* See also: `recipient_thread_close`.

### Confirm Thread Creation Accept ( confirm\_thread\_creation\_accept )

Emoji to accept thread creation

_**Default:**_ \u2705

_**Example:**_

* `?config set confirm_thread_creation_accept \u2611`

_**Notes:**_

* This has no effect unless `confirm_thread_creation` is set
* See also: `confirm_thread_creation`, `confirm_thread_creation_title`, `confirm_thread_response`, `confirm_thread_creation_deny`

### Confirm Thread Creation Deny ( confirm\_thread\_creation\_deny )

Emoji to cancel thread creation

_**Default:**_ \uD83D\uDEAB

_**Example:**_

* `?config set confirm_thread_creation_deny \u26D4`

_**Notes:**_

* This has no effect unless `confirm_thread_creation` is set
* See also: `confirm_thread_creation`, `confirm_thread_creation_title`, `confirm_thread_response`, `confirm_thread_creation_accept`

### Error Color ( error\_color )

This is the color for Modmail when anything goes wrong, unsuccessful commands, or a stern warning.

_**Default:**_ Discord Red [#E74C3C](https://placehold.it/100/e74c3c?text=+)

_**Example:**_

* `?config set error_color ocean blue`
* `?config set error_color ff1242`
* `?config set error_color #ff1242`
* `?config set error_color fa1`

_**Notes:**_

* Available color names can be found on [Color Options](https://docs.modmail.dev/old-docs/color-names).
* See also: `main_color`, `mod_color`, `recipient_color`.

### Main Color ( main\_color )

This is the main color for Modmail (help/about/ping embed messages, subscribe, move, etc.).

_**Default:**_ Discord Blurple [#7289DA](https://placehold.it/100/7289da?text=+)

_**Example:**_

* `?config set main_color olive green`
* `?config set main_color 12de3a`
* `?config set main_color #12de3a`
* `?config set main_color fff`

_**Notes:**_

* Available color names can be found on [Color Options](https://docs.modmail.dev/old-docs/color-names).
* See also: `error_color`, `mod_color`, `recipient_color`.

### Mod Color ( mod\_color )

This is the color of the messages sent by the moderators, this applies to messages within in the thread channel and the DM thread messages received by the recipient.

_**Default:**_ Discord Green [#2ECC71](https://placehold.it/100/2ecc71?text=+)

_**Example:**_

* `?config set mod_color dark beige`
* `?config set mod_color cb7723`
* `?config set mod_color #cb7723`
* `?config set mod_color c4k`

_**Notes:**_

* Available color names can be found on [Color Options](https://docs.modmail.dev/old-docs/color-names).
* See also: `recipient_color`, `main_color`, `error_color`.

### React To Contact Emoji ( react\_to\_contact\_emoji )

An emoji which is tracked in `react_to_contact_message`

_**Default:**_ \u2705

_**Example:**_

* `?config set react_to_contact_emoji \u2705`

_**Notes:**_

* See also: `react_to_contact_message \u2705`

### Recipient Color ( recipient\_color )

This is the color of the messages sent by the recipient, this applies to messages received in the thread channel.

_**Default:**_ "Discord Gold [#F1C40F](https://placehold.it/100/f1c40f?text=+)

_**Example:**_

* `?config set recipient_color dark beige`
* `?config set recipient_color cb7723`
* `?config set recipient_color #cb7723`
* `?config set recipient_color c4k`

_**Notes:**_

* Available color names can be found on [Color Options](https://docs.modmail.dev/old-docs/color-names).
* See also: `mod_color`, `main_color`, `error_color`.

### Sent Emoji ( sent\_emoji )

This is the emoji added to the message when when a Modmail action is invoked successfully (ie. DM Modmail, edit message, etc.).

_**Default:**_ ✅

_**Example:**_

* `?config set sent_emoji ✨`

_**Notes:**_

* You can disable `sent_emoji` with `?config set sent_emoji disable`.
* Custom/animated emojis are also supported, however, the emoji must be added to the server.
* See also: `blocked_emoji`.

### Show Log URL Button ( show\_log\_url\_button )

Shows the button to open the Log URL.

_**Default:**_ No

_**Example:**_

* `?config set show_log_url_button yes`

## Thread Appearance

### Use Random Channel Name ( use\_random\_channel\_name )

When this is set to `yes`, new thread channels will be named with random characters tied to their user ID.

_**Default:**_ No

_**Example:**_

* `?config set use_random_channel_name yes`
* `?config set use_random_channel_name no`

_**Notes:**_

{% hint style="warning" %}
This config is suitable for servers in Server Discovery to comply with channel name restrictions.
{% endhint %}

{% hint style="danger" %}
This cannot be applied with \`use\_timestamp\_channel\_name\`, \`use\_nickname\_channel\_name\`, or \`use\_user\_id\_channel\_name\`.
{% endhint %}

* See also: `use_timestamp_channel_name`, `use_user_id_channel_name`, `use_nickname_channel_name`.

### Use Timestamp Channel Name ( use\_timestamp\_channel\_name )

When this is set to `yes`, new thread channels will be named with the recipient's account creation date instead of the recipient's name.

_**Default:**_ No

_**Example:**_

* `?config set use_timestamp_channel_name yes`
* `?config set use_timestamp_channel_name no`

_**Notes:**_

{% hint style="warning" %}
This config is \*\*NOT\*\* suitable for servers in Server Discovery to comply with channel name restrictions.
{% endhint %}

{% hint style="danger" %}
This cannot be applied with \`use\_user\_id\_channel\_name\`, \`use\_random\_channel\_name\` or \`use\_nickname\_channel\_name\`.
{% endhint %}

* See also: `use_user_id_channel_name`, `use_nickname_channel_name`, `use_random_channel_name`.

### Use User ID Channel Name ( use\_user\_id\_channel\_name )

When this is set to `yes`, new thread channels will be named with the recipient's ID instead of the recipient's name.

_**Default:**_ No

_**Example:**_

* `?config set use_user_id_channel_name yes`
* `?config set use_user_id_channel_name no`

_**Notes:**_

{% hint style="warning" %}
This config is suitable for servers in Server Discovery to comply with channel name restrictions.
{% endhint %}

{% hint style="danger" %}
This cannot be applied with \`use\_timestamp\_channel\_name\`, \`use\_random\_channel\_name\` or \`use\_nickname\_channel\_name\`.
{% endhint %}

* See also: `use_timestamp_channel_name`, `use_nickname_channel_name`, `use_random_channel_name`.

### Use Nickname Channel Name ( use\_nickname\_channel\_name )

When this is set to `yes`, new thread channels will be named with the recipient's nickname instead of the recipient's name.

_**Default:**_

_**Example:**_

* `?config set use_nickname_channel_name yes`
* `?config set use_nickname_channel_name no`

_**Notes:**_

{% hint style="warning" %}
This config is suitable for servers in Server Discovery to comply with channel name restrictions.
{% endhint %}

{% hint style="danger" %}
This cannot be applied with \`use\_timestamp\_channel\_name\`, \`use\_random\_channel\_name\` or \`use\_user\_id\_channel\_name\`.
{% endhint %}

* See also: `use_timestamp_channel_name`, `use_user_id_channel_name`, `use_random_channel_name`.

### Use Hoisted Top Role ( use\_hoisted\_top\_role )

Controls if only hoisted roles are evaluated when finding top role.

_**Default:**_ Yes

_**Example:**_

* `?config set use_hoisted_top_role yes`
* `?config set use_hoisted_top_role no`

_**Notes:**_

* Top role is displayed in embeds when replying or adding/removing users to a thread in the case mod\_tag and anon\_username are not set.
* If this configuration is enabled, only roles that are hoisted (displayed seperately in member list) will be used. If a user has no hoisted roles, it will return 'None'.
* If you would like to display the top role of a user regardless of if it's hoisted or not, disable `use_hoisted_top_role`.

### Thread Show Account Age ( thread\_show\_account\_age )

Shows account age on first message sent in thread channels to mods

_**Default:**_ Yes

_**Example:**_

* `?config set thread_show_account_age no`

_**Notes:**_

* See also: `thread_show_roles`, `thread_show_join_age`

### Thread Show Join Age ( thread\_show\_join\_age )

Shows join age on first message sent in thread channels to mods

_**Default:**_ Yes

_**Example:**_

* `?config set thread_show_join_age no`

_**Notes:**_

* See also: `thread_show_account_age`, `thread_show_roles`.

### Thread Show Roles ( thread\_show\_roles )

Shows roles on first message sent in thread channels to mods

_**Default:**_ Yes

_**Example:**_

* `?config set thread_show_account_age no`

_**Notes:**_

* See also: `thread_show_roles`, `thread_show_join_age`.

### Mod Tag ( mod\_tag )

This is the name tag in the “footer” section of the embeds sent by moderators in the recipient DM and thread channel.

_**Default:**_ The moderator's highest role

_**Example:**_

* `?config set mod_tag Moderator`

_**Notes:**_

{% hint style="warning" %}
When the message is sent anonymously, \`anon\_tag\` is used instead.
{% endhint %}

* See also: `anon_tag`.

### Anon Tag ( anon\_tag )

This is the name tag in the “footer” section of the embeds sent by anonymous moderators in the recipient DM.

_**Default:**_ "Response"

_**Example:**_

* `?config set anon_tag Support Agent`

_**Notes:**_

* See also: `anon_avatar_url`, `anon_username`, `mod_tag`.

### Anon Avatar URL ( anon\_avatar\_url )

This is the avatar of the embeds sent by anonymous moderators in the recipient DM.

_**Default:**_ Server avatar

_**Example:**_

* `?config set anon_avatar_url https://path.to/your/avatar.png` (you will need to upload the avatar to somewhere)

_**Notes:**_

* See also: `anon_username`, `anon_tag`.

### Anon Username ( anon\_username )

This is the name in the “author” section of the embeds sent by anonymous moderators in the recipient DM.

_**Default:**_ Fallback on `mod_tag`

_**Example:**_

* `?config set anon_username Incognito Mod`

_**Notes:**_

* See also: `anon_avatar_url`, `anon_tag`.

### Transfer Reactions ( transfer\_reactions )

Transfer users reactions to mods and vice versa _(If someone reacts to a thread message the other party will see it.)_

_**Default:**_ Yes

_**Example:**_

* `?config set transfer_reactions no`

## Thread Responses

### Close On Leave Reason ( close\_on\_leave\_reason )

Reason for closing the thread once member leaves

_**Default:**_ The recipient has left the server.

_**Example:**_

* `?config set close_on_leave_reason Member left`

_**Notes:**_

* This has no effect unless `close_on_leave` is set.
* See also: `close_on_leave`.

### Confirm Thread Creation Title ( confirm\_thread\_creation\_title )

Title for the embed message sent to users to confirm a thread creation

_**Default:**_ Confirm thread creation

_**Example:**_

* `?config set confirm_thread_creation_title Are you sure you want to create a new thread?`

_**Notes:**_

* See also: `confirm_thread_creation`, `confirm_thread_response`, `confirm_thread_creation_accept`, `confirm_thread_creation_deny`

### Confirm Thread Response ( confirm\_thread\_response )

Description for the embed message sent to users to confirm a thread creation

_**Default:**_ React to confirm thread creation which will directly contact the moderators

_**Example:**_

* `?config set confirm_thread_response React to confirm`

_**Notes:**_

* See also: `confirm_thread_creation`, `confirm_thread_creation_title`, `confirm_thread_creation_accept`, `confirm_thread_creation_deny`

### Cooldown Thread Response ( cooldown\_thread\_response )

The description of the message embed when the user has a cooldown before creating a new thread.

_**Default:**_ Your cooldown ends {delta}. Try contacting me then.

{% hint style="info" %}
\`{delta}\` will be replaced with whatever time you gave it.
{% endhint %}

_**Example:**_

* `?config set cooldown_thread_response Be patient! You are on cooldown, wait {delta} more.`

_**Notes:**_

* "Only has an effect when `thread_cooldown` is set
* Must have a {delta} included which will be replaced with the duration of time.
* See also: `cooldown_thread_title`.

### Cooldown Thread Title ( cooldown\_thread\_title )

The title of the message embed when the user has a cooldown before creating a new thread.

_**Default:**_ Message not sent!

_**Example:**_

* `?config set cooldown_thread_title Error`

_**Notes:**_

* Only has an effect when `thread_cooldown` is set
* See also: `cooldown_thread_response`.

### Disabled Current Thread Footer ( disabled\_current\_thread\_footer )

The footer of the message embed when Modmail DM is disabled and user DMs Modmail from existing thread.

_**Default:**_ Please try again later...

_**Example:**_

* `?config set disabled_current_thread_footer Message back!`

_**Notes:**_

* Only has an effect when `{prefix}disable all` is set.
* See also: `disabled_current_thread_title`, `disabled_current_thread_response`, `disabled_new_thread_footer`.

### Disabled Current Thread Response ( disabled\_current\_thread\_response )

The body of the message embed when Modmail DM is disabled and user DMs Modmail from existing thread.

_**Default:**_ We are not accepting any messages.

_**Example:**_

* `?config set disabled_current_thread_response On break right now.`

_**Notes:**_

* Only has an effect when `{prefix}disable all` is set.
* See also: `disabled_current_thread_title`, `disabled_current_thread_footer`, `disabled_new_thread_response`.

### Disabled Current Thread Title ( disabled\_current\_thread\_title )

The title of the message embed when Modmail DM is disabled and user DMs Modmail from existing thread.

_**Default:**_ Not Delivered.

_**Example:**_

* `?config set disabled_current_thread_title Unavailable`

_**Notes:**_

* Only has an effect when `{prefix}disable all` is set.
* See also: `disabled_current_thread_response`, `disabled_current_thread_footer`, `disabled_new_thread_title`.

### Disabled New Thread Footer ( disabled\_new\_thread\_footer )

The footer of the message embed when Modmail new thread creation is disabled and user tries to create a new thread.

_**Default:**_ Please try again later...

_**Example:**_

* `?config set disabled_new_thread_footer Contact us later`

_**Notes:**_

* Only has an effect when `{prefix}disable` or `{prefix}disable all` is set.
* See also: `disabled_new_thread_title`, `disabled_new_thread_response`, `disabled_current_thread_footer`.

### Disabled New Thread Response ( disabled\_new\_thread\_response )

The body of the message embed when Modmail new thread creation is disabled and user tries to create a new thread.

_**Default:**_ We are not accepting new threads.

_**Example:**_

* `?config set disabled_new_thread_response Our working hours is between 8am - 6pm EST.`

_**Notes:**_

* Only has an effect when `{prefix}disable` or `{prefix}disable all` is set.
* See also: `disabled_new_thread_title`, `disabled_new_thread_footer`, `disabled_current_thread_response`.

### Disabled New Thread Title ( disabled\_new\_thread\_title )

The title of the message embed when Modmail new thread creation is disabled and user tries to create a new thread.

_**Default:**_ Not Delivered.

_**Example:**_

* `?config set disabled_new_thread_title Closed`

_**Notes:**_

* Only has an effect when `{prefix}disable` or `{prefix}disable all` is set.
* See also: `disabled_new_thread_response`, `disabled_new_thread_footer`, `disabled_current_thread_title`.

### Private Added To Group Description Anon ( private\_added\_to\_group\_description\_anon )

This is the message embed content sent to the recipient that is just added to a thread when adduser is used anonymously.

_**Default:**_ A moderator has added you to a Modmail thread.

_**Example:**_

* `?config set private_added_to_group_description_anon Any message sent here will be sent to all other thread recipients.`

_**Notes:**_

* When adduser (no anon) is used, `private_added_to_group_description` is used instead.
* The public\_ variant is used when sending to other thread recipients.
* See also: `private_added_to_group_title`, `public_added_to_group_description_anon`

### Private Added To Group Response ( private\_added\_to\_group\_response )

This is the message embed content sent to the recipient that is just added to a thread.

_**Default:**_ "\{{moderator.name\}} has added you to a Modmail thread."

_**Example:**_

* `?config set private_added_to_group_description Any message sent here will be sent to all otherthread recipients.`

_**Notes:**_

* You may use the `{{moderator}}` variable for access to the [Member](https://discordpy.readthedocs.io/en/latest/api.html#discord.Member) that added the user.
* When anonadduser is used, `private_added_to_group_description_anon` is used instead.
* The public\_ variant is used when sending to other thread recipients.
* See also: `private_added_to_group_title`, `public_added_to_group_description`

### Private Added To Group Title ( private\_added\_to\_group\_title )

This is the message embed title sent to the recipient that is just added to a thread.

_**Default:**_ New Thread (Group)

_**Example:**_

* `?config set private_added_to_group_title Welcome to this new group thread!`

_**Notes:**_

* The public\_ variant is used when sending to other thread recipients.
* See also: `private_added_to_group_description`, `public_added_to_group_title`

### Private Removed From Group Description Anon ( private\_removed\_from\_group\_description\_anon )

This is the message embed content sent to the recipient that is just removed from a thread when removeuser is used anonymously.

_**Default:**_ A moderator has removed you from the Modmail thread.

_**Example:**_

* `?config set private_removed_from_group_description_anon You are permenantly removed from this thread.`

_**Notes:**_

* When adduser (no anon) is used, `private_removed_from_group_description` is used instead.
* The public\_ variant is used when sending to other thread recipients.
* See also: `private_removed_from_group_title`, `public_removed_from_group_description_anon`

### Private Removed From Group Response ( private\_removed\_from\_group\_response )

This is the message embed content sent to the recipient that is just removed from a thread.

_**Default:**_ "\{{moderator.name\}} has removed you from the Modmail thread."

_**Example:**_

* `?config set private_removed_from_group_description Bye`

_**Notes:**_

* You may use the `{{moderator}}` variable for access to the [Member](https://discordpy.readthedocs.io/en/latest/api.html#discord.Member) that added the user.
* When anonremoveuser is used, `private_removed_from_group_description_anon` is used instead.
* The public\_ variant is used when sending to other thread recipients.
* See also: `private_removed_from_group_title`, `public_removed_from_group_description`

### Private Removed From Group Title ( private\_removed\_from\_group\_title )

This is the message embed title sent to the recipient that is just removed from a thread.

_**Default:**_ Removed From Thread (Group)

_**Example:**_

* `?config set private_removed_from_group_title Welcome to this new group thread!`

_**Notes:**_

* The public\_ variant is used when sending to other thread recipients.
* See also: `private_removed_from_group_description`, `public_removed_from_group_title`

### Public Added To Group Description Anon ( public\_added\_to\_group\_description\_anon )

This is the message embed content sent to all other recipients when someone is added to the thread when adduser is used anonymously.

_**Default:**_ "A moderator has added \{{users\}} to the Modmail thread."

_**Example:**_

* `?config set public_added_to_group_description_anon Any message sent here will be sent to all other thread recipients.`

_**Notes:**_

* When adduser (no anon) is used, `public_added_to_group_description` is used instead.
* The private\_ variant is used when sending to the new user.
* See also: `public_added_to_group_title`, `private_added_to_group_description_anon`

### Public Added To Group Response ( public\_added\_to\_group\_response )

This is the message embed content sent to all other recipients when someone is added to the thread.

_**Default:**_ "\{{moderator.name\}} has added \{{users\}} to the Modmail thread."

_**Example:**_

* `?config set public_added_to_group_response Welcome {users}!`

_**Notes:**_

* You may use the `{{moderator}}` variable for access to the [Member](https://discordpy.readthedocs.io/en/latest/api.html#discord.Member) that added the user.
* When anonadduser is used, `public_added_to_group_description_anon` is used instead.
* The private\_ variant is used when sending to the new user.
* See also: `public_added_to_group_title`, `private_added_to_group_description`

### Public Added To Group Title ( public\_added\_to\_group\_title )

This is the message embed title sent to all other recipients when someone is added to the thread.

_**Default:**_ New User

_**Example:**_

* `?config set public_added_to_group_title Welcome to our new user!`

_**Notes:**_

* The private\_ variant is used when sending to the new user.
* See also: `private_added_to_group_title`, `private_added_to_group_title`

### Public Removed From Group Description Anon ( public\_removed\_from\_group\_description\_anon )

This is the message embed content sent to all other recipients when someone is removed from the thread when removeuser is used anonymously.

_**Default:**_ "A moderator has removed \{{users\}} from the Modmail thread."

_**Example:**_

* `?config set public_removed_from_group_description_anon Goodbye {users}!`

_**Notes:**_

* When adduser (no anon) is used, `public_removed_from_group_description` is used instead.
* The private\_ variant is used when sending to the new user.
* See also: `public_removed_from_group_title`, `private_removed_from_group_description_anon`

### Public Removed From Group Response ( public\_removed\_from\_group\_response )

This is the message embed content sent to all other recipients when someone is removed from the thread.

_**Default:**_ "\{{moderator.name\}} has removed \{{users\}} from the Modmail thread."

_**Example:**_

* `?config set public_removed_from_group_response Goodbye {users}!`

_**Notes:**_

* You may use the `{{moderator}}` variable for access to the [Member](https://discordpy.readthedocs.io/en/latest/api.html#discord.Member) that added the user.
* When anonremoveuser is used, `public_removed_from_group_description_anon` is used instead.

### Public Removed From Group Title ( public\_removed\_from\_group\_title )

This is the message embed title sent to all other recipients when someone is removed from the thread.

_**Default:**_ User Removed

_**Example:**_

* `?config set public_removed_from_group_title User is now gone!`

_**Notes:**_

* The private\_ variant is used when sending to the new user.
* See also: `private_removed_from_group_title`, `private_removed_from_group_title`

### React To Contact Message ( react\_to\_contact\_message )

A message ID where reactions are tracked. If the `react_to_contact_emoji` is added, the bot opens a thread with them.

_**Default:**_ None

_**Example:**_

* `?config set react_to_contact_message 773575608814534717`

_**Notes:**_

* See also: `react_to_contact_emoji`

### Recipient Thread Close ( recipient\_thread\_close )

Setting this configuration will allow recipients to use the `close_emoji` to close the thread themselves.

_**Default:**_ Disabled

_**Example:**_

* `?config set recipient_thread_close yes`
* `?config set recipient_thread_close no`

_**Notes:**_

* The close emoji is dictated by the configuration `close_emoji`.
* See also: `close_emoji`.

### Thread Auto Close Response ( thread\_auto\_close\_response )

This is the message to display when the thread when the thread auto-closes.

_**Default:**_ "This thread has been closed automatically due to inactivity after \{{timeout\}}."

_**Example:**_

* `?config set thread_auto_close_response Your close message here.`

_**Notes:**_

* Its possible to use `{{timeout}}` as a placeholder for a formatted timeout text.
* This will not have an effect when `thread_auto_close_silently` is enabled.
* Discord flavoured markdown is fully supported in `thread_auto_close_response`.
* See also: `thread_auto_close`, `thread_auto_close_silently`.

### Thread Auto Close Silently ( thread\_auto\_close\_silently )

Setting this configuration will close silently when the thread auto-closes.

_**Default:**_ No

_**Example:**_

* `?config set thread_auto_close_silently yes`
* `?config set thread_auto_close_silently no`

_**Notes:**_

* This will only have an effect when `thread_auto_close` is set.
* See also: `thread_auto_close`.

### Thread Cancelled ( thread\_cancelled )

This is the message to display when a thread times out and creation is cancelled.

_**Default:**_ "Cancelled"

_**Example:**_

* `?config set thread_cancelled Gone.`

### Thread Close Footer ( thread\_close\_footer )

This is the message embed footer sent to the recipient upon the closure of a thread.

_**Default:**_ "Replying will create a new thread"

_**Example:**_

* `?config set thread_close_footer Bye!`

_**Notes:**_

* See also: `thread_close_title`, `thread_close_response`, `thread_creation_footer`.

### Thread Close Response ( thread\_close\_response )

This is the message embed content sent to the recipient upon the closure of a thread.

There are three variables you can use within the thread close message: - `closer`: the discord User object of the user who closed the thread. - `logkey`: the key for the thread logs. (ie. 51ecd946dc29) - `loglink`: the full link URL to the thread logs. (ie. https://logviewer.herokuapp.com/logs/51ecd946dc29)

_**Default:**_ "\{{closer.mention\}} has closed this Modmail thread"

_**Example:**_

* `?config set thread_close_response Your message is appriciated!`

To use variables in the thread close message:

* `?config set thread_close_response {closer.mention} has closed this thread, here's your log key: **`{logkey}`**.`

_**Notes:**_

* When `recipient_thread_close` is enabled and the recipient closed their own thread, `thread_self_close_response` is used instead of this configuration.
* You may use the `{{closer}}` variable for access to the [Member](https://discordpy.readthedocs.io/en/latest/api.html#discord.Member) that closed the thread.
* Discord flavoured markdown is fully supported in `thread_close_response`.
* See also: `thread_close_title`, `thread_close_footer`, `thread_self_close_response`, `thread_creation_response`.

### Thread Close Title ( thread\_close\_title )

This is the message embed title sent to the recipient upon the closure of a thread.

_**Default:**_ "Thread Closed"

_**Example:**_

* `?config set thread_close_title Farewell!`

_**Notes:**_

* See also: `thread_close_response`, `thread_close_footer`, `thread_creation_title`.

### Thread Contact Silently ( thread\_contact\_silently )

Setting this configuration will always open a new thread silently in contact.

_**Default:**_ No

_**Example:**_

* `?config set thread_contact_silently yes`
* `?config set thread_contact_silently no`

_**Notes:**_

* Works like `{prefix}contact <user> silent` for every new thread.

### Thread Creation Contact Response ( thread\_creation\_contact\_response )

This is the message embed description sent to recipients when contacted by a mod.

_**Default:**_ "\{{creator.name\}} has opened a Modmail thread."

_**Example:**_

* `?config set thread_creation_contact_response New thread opened.`

_**Notes:**_

* You may use the `{{creator}}` variable for access to the [Member](https://discordpy.readthedocs.io/en/latest/api.html#discord.Member) that created the thread.
* `thread_creation_self_contact_response` is used when contacted by self.
* See also: `thread_creation_contact_title`, `thread_creation_self_contact_response`.

### Thread Creation Contact Title ( thread\_creation\_contact\_title )

This is the message embed title sent to recipients when contacted.

_**Default:**_ "New Thread"

_**Example:**_

* `?config set thread_creation_contact_title New Message!`

_**Notes:**_

* See also: `thread_creation_self_contact_response`, `thread_creation_contact_response`.

### Thread Creation Footer ( thread\_creation\_footer )

This is the message embed footer sent to the recipient upon the creation of a new thread.

_**Default:**_ "Your message has been sent"

_**Example:**_

* \`?config set thread\_creation\_footer Please Hold...

_**Notes:**_

* This is used in place of `thread_self_closable_creation_footer` when `recipient_thread_close` is enabled.
* See also: `thread_creation_title`, `thread_creation_response`, `thread_self_closable_creation_footer`, `thread_close_footer`.

### Thread Creation Response ( thread\_creation\_response )

This is the message embed content sent to the recipient upon the creation of a new thread.

_**Default:**_ "The staff team will get back to you as soon as possible."

_**Example:**_

* `?config set thread_creation_response You will be contacted shortly.`

_**Notes:**_

* Discord flavoured markdown is fully supported in `thread_creation_response`.
* See also: `thread_creation_title`, `thread_creation_footer`, `thread_close_response`.

### Thread Creation Self Contact Response ( thread\_creation\_self\_contact\_response )

This is the message embed description sent to recipients when self-contacted.

_**Default:**_ "You have opened a Modmail thread."

_**Example:**_

* `?config set thread_creation_self_contact_response You contacted yourself.`

_**Notes:**_

* `thread_creation_contact_response` is used when contacted by another user.
* See also: `thread_creation_contact_title`, `thread_creation_contact_response`.

### Thread Creation Title ( thread\_creation\_title )

This is the message embed title sent to the recipient upon the creation of a new thread.

_**Default:**_ "Thread Created"

_**Example:**_

* `?config set thread_creation_title Hello!`

_**Notes:**_

* See also: `thread_creation_response`, `thread_creation_footer`, `thread_close_title`.

### Thread Move Response ( thread\_move\_response )

This is the message to display to the user when the thread is moved.

_**Default:**_ This thread has been moved.

_**Example:**_

* `?config set thread_move_response This thread has been moved to another category for review!`

_**Notes:**_

* Only has an effect when `thread_move_notify` is on.
* See also: `thread_move_title`, `thread_move_notify`.

### Thread Move Title ( thread\_move\_title )

The title of the message embed when a thread is moved.

_**Default:**_ Thread Moved

_**Example:**_

* `?config set thread_move_title Thread transferred to another channel!`

_**Notes:**_ -See also: `thread_move_notify`, `thread_move_notify_mods`, `thread_move_response`.

### Thread Self Closable Creation Footer ( thread\_self\_closable\_creation\_footer )

This is the message embed footer sent to the recipient upon the creation of a new thread.

_**Default:**_ "Click the lock to close the thread"

_**Example:**_

* `?config set thread_self_closable_creation_footer Please Hold...`

_**Notes:**_

* This is used in place of `thread_creation_footer` when `recipient_thread_close` is disabled.
* See also: `thread_creation_title`, `thread_creation_response`, `thread_creation_footer`.

### Thread Self Close Response ( thread\_self\_close\_response )

This is the message embed content sent to the recipient upon the closure of a their own thread.

_**Default:**_ "You have closed this Modmail thread."

_**Example:**_

* `?config set thread_self_close_response You have closed your own thread...`

_**Notes:**_

* When `recipient_thread_close` is disabled or the thread wasn't closed by the recipient, `thread_close_response` is used instead of this configuration.
* You may use the `{{closer}}` variable for access to the [Member](https://discordpy.readthedocs.io/en/latest/api.html#discord.Member) that closed the thread.
* `{{loglink}}` can be used as a placeholder substitute for the full URL linked to the thread in the log viewer and `{{loglink}}` for the unique key (ie. s3kf91a) of the log.
* Discord flavoured markdown is fully supported in `thread_self_close_response`. -See also: `thread_close_title`, `thread_close_footer`, `thread_close_response`.

## `.env` Config Options

**The following is a list of config options that can **_**ONLY**_** be added by editing the `.env` file. Please use whichever guide you followed to set up the bot to see how to add these variables.**

{% hint style="danger" %}
It is recommended you avoid and ignore changing any of these you do not fully understand
{% endhint %}

| Option                   |                                  Description                                  | Required |                                          Usage                                          |
| ------------------------ | :---------------------------------------------------------------------------: | :------: | :-------------------------------------------------------------------------------------: |
| modmail\_guild\_id       |                            Inbox server for tickets                           |    No    |                             `MODMAIL_GUILD_ID = GUILDIDHERE`                            |
| guild\_id                |                           Main server the bot is in                           |    Yes   |                                 `GUILD_ID = GUILDIDHERE`                                |
| log\_url\_prefix         |                               Default is `/logs`                              |    Yes   |                                `LOG_URL_PREFIX = PREFIX`                                |
| mongo\_uri               |                      The connection uri for the database                      |    Yes   |    `MONGO_URI = mongodb+srv://Papiersnipper:mypassword123@modmail-rdm99.mongodb.net/`   |
| connection\_uri          |                      The connection uri for the database                      |    Yes   | `CONNECTION_URI = mongodb+srv://Papiersnipper:mypassword123@modmail-rdm99.mongodb.net/` |
| owners                   |                  ID's of the users who will have owner perms                  |    Yes   |                                `OWNERS = 1234,5678,91011`                               |
| enable\_presence\_intent | Enables the presence intent, required for some plugins. Uses extra resources. |    No    |                             `ENABLE_PRESENCE_INTENT = True`                             |
| registry\_plugins\_only  | Disallows the ability to download plugins that aren’t in the plugin registry. |    No    |                              `REGISTRY_PLUGINS_ONLY = True`                             |
| token                    |                                 The bots token                                |    Yes   |              `TOKEN = MTAyMjk2NTA4MzYxtewgw3eNw.thisis.afaketoken-WGjwfvQ`              |
| enable\_eval             |           Enables the eval command to run arbitrary code on the bot.          |    No    |                                   `ENABLE_EVAL = True`                                  |
| github\_token            |                        Needed to use the update command                       |    No    |                         `GITHUB_TOKEN = ghp_ABC132gfdsg4321fds`                         |
| disable\_autoupdates     |                            Allows for auto updates                            |    No    |                               `DISABLE_AUTOUPDATES = True`                              |
| disable\_updates         |                         Disables updates all together                         |    No    |                                 `DISABLE_UPDATES = True`                                |
| log\_level               |       The type of information posted in the terminal, Default is `INFO`       |    No    |                      `LOG_LEVEL = ERROR/WARNING/INFO/DEBUG/NOTSET`                      |
