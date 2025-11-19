# Configuration Variables (Config Vars)

These are currently all the valid configuration variables you can change with the `config set` command.

{% tabs %}

{% tab title="Categorized" %} <details>

<summary>Table of Contents</summary>

## 🧩 General Bot Settings
- `prefix`
- `twitch_url`
- `main_color`
- `error_color`
- `tag_color`
- `mod_color`
- `recipient_color`
- `mention`
- `blocked_response`
- `dm_notification`
- `recipient_language`
- `mod_language`

## 💬 Thread & Channel Behavior
- `main_category_id`
- `fallback_category_id`
- `use_user_id_channel_name`
- `use_timestamp_channel_name`
- `use_nickname_channel_name`
- `use_random_channel_name`
- `thread_channel_topic_template`
- `thread_auto_pin`
- `thread_limit_per_user`
- `thread_auto_close`
- `thread_auto_close_silently`
- `thread_cooldown`
- `thread_lockdown_mode`
- `lockdown_reason`
- `thread_blacklist_roles`
- `thread_blacklist_users`
- `thread_blacklist_channels`

## 💌 Thread Message & Interaction
- `reply_without_command`
- `anon_reply_without_command`
- `plain_reply_without_command`
- `anonymous_mod_replies`
- `mod_typing`
- `user_typing`
- `mod_reply_indicator`
- `recipient_thread_close`
- `close_emoji`
- `recipient_thread_close_reason`
- `thread_cancelled`

## 🧠 Thread Display & Metadata
- `thread_show_roles`
- `thread_show_account_age`
- `thread_show_join_age`
- `thread_creation_response`
- `thread_close_response`
- `thread_auto_close_response`
- `thread_close_footer`
- `thread_activity_alerts`
- `thread_priority_tag`
- `thread_priority_color`

## 📦 Logging & Archiving
- `log_channel_id`
- `log_format`
- `log_embed_color`
- `log_expiration`
- `archive_channel_id`
- `archive_expiration`
- `update_channel_id`
- `update_notifications`
- `modmail_logging_level`

## 📣 Mentions, Alerts & Notifications
- `mention_channel_id`
- `alert_on_mention`
- `support_role_id`
- `sent_emoji`
- `blocked_emoji`
- `status_channel_id`

## ⚙️ Automation, Tags & Updates
- `auto_tag`
- `auto_tag_rules`
- `auto_update_interval`
- `disable_autoupdates`

## 🚨 Access & Security Controls
- `account_age`
- `guild_age`


</details> 

## 🧩 General Bot Settings

| Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `prefix` | String | `?` | The command prefix for Modmail commands. | Bot also responds to direct mentions. |
| `twitch_url` | URL | `https://www.twitch.tv/discordmodmail/` | URL used when activity is set to “Streaming”. | Only used in streaming status mode. |
| `main_color` | Color | `#7289DA` | Primary embed color used throughout Modmail. | See also: `error_color`, `mod_color`, `recipient_color`. |
| `error_color` | Color | `#E74C3C` | Embed color for errors and warnings. | Distinct from `main_color`. |
| `tag_color` | Color | `#7289DA` | Default color for auto-assigned tags. | Used with `auto_tag_rules`. |
| `mod_color` | Color | None | Optional color for mod reply embeds. | Defaults to `main_color` if unset. |
| `recipient_color` | Color | None | Optional color for user reply embeds. | Defaults to `main_color`. |
| `mention` | String | `@here` | Mention text displayed above thread info. | Disable via `{prefix}mention disable`. |
| `blocked_response` | Message | `"You cannot DM this bot."` | Message shown when blocked users try to DM Modmail. | Triggered by blacklist rules. |
| `dm_notification` | Boolean | Enabled | Sends DMs to mods when a user opens a new thread. | Disable to reduce mod pings. |
| `recipient_language` | Language Code | `en` | Language used for user-facing messages. | Requires translation files. |
| `mod_language` | Language Code | `en` | Language used for moderator messages. | Supports multilingual teams. |


---

## 💬 Thread & Channel Behavior

| Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `main_category_id` | Category ID | Auto-created during setup | Category for new threads. | Required for Modmail to work. |
| `fallback_category_id` | Category ID | Auto-created fallback | Used when main category is full. | Auto-created if missing. |
| `use_user_id_channel_name` | Boolean | No | Names threads by user ID. | Mutually exclusive with other naming options. |
| `use_timestamp_channel_name` | Boolean | No | Names threads by user’s account creation date. | Mutually exclusive with others. |
| `use_nickname_channel_name` | Boolean | No | Names threads by nickname. | Mutually exclusive with others. |
| `use_random_channel_name` | Boolean | No | Names threads with random characters. | Best for privacy/discovery servers. |
| `thread_channel_topic_template` | Template | `"Thread for {user.name} ({user.id})"` | Template for thread channel topics. | Supports placeholders. |
| `thread_auto_pin` | Boolean | Disabled | Pins the first message in a thread. | Keeps context visible. |
| `thread_limit_per_user` | Integer | 1 | Max concurrent threads per user. | Helps prevent spam. |
| `thread_auto_close` | Duration | Never | Auto-closes inactive threads. | Use `{prefix}config del` to disable. |
| `thread_auto_close_silently` | Boolean | No | Closes threads without notifying the user. | Requires `thread_auto_close`. |
| `thread_cooldown` | Duration | Never | Delay before users can reopen threads. | Prevents spam reopenings. |
| `thread_lockdown_mode` | Boolean | Disabled | Prevents new threads globally. | Used during maintenance. |
| `lockdown_reason` | String | `"Modmail temporarily unavailable."` | Message shown when locked down. | Displayed to users on DM. |
| `thread_blacklist_roles` | Role List | None | Roles not allowed to open threads. | Commonly used for bots. |
| `thread_blacklist_users` | User List | None | Users blocked from Modmail. | Enforced on DM. |
| `thread_blacklist_channels` | Channel List | None | Channels excluded from forwarding. | Optional. |


---

## 💌 Thread Message & Interaction

| Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `reply_without_command` | Boolean | Disabled | Automatically sends replies without `{prefix}reply`. | Useful for quick replies. |
| `anon_reply_without_command` | Boolean | Disabled | Sends anonymous replies automatically. | Used with staff anonymity. |
| `plain_reply_without_command` | Boolean | Disabled | Sends plain replies automatically. | Used for informal setups. |
| `anonymous_mod_replies` | Boolean | Disabled | Makes all mod replies anonymous. | Can be overridden per message. |
| `mod_typing` | Boolean | Disabled | Shows typing indicator to users when mods type. | Adds realism. |
| `user_typing` | Boolean | Enabled | Shows typing indicator to mods when users type. | Gives feedback to mods. |
| `mod_reply_indicator` | Emoji | 💬 | Emoji that marks mod replies. | Visual separation. |
| `recipient_thread_close` | Boolean | Disabled | Allows users to close their own threads. | Uses `close_emoji`. |
| `close_emoji` | Emoji | 🔒 | Emoji users click to close thread. | Requires `recipient_thread_close`. |
| `recipient_thread_close_reason` | Boolean | Disabled | Asks users for a reason when closing thread. | Requires `recipient_thread_close`. |
| `thread_cancelled` | Message | `"Thread creation has been cancelled."` | Message sent when setup aborted. | Confirmation for user. |


---

## 🧠 Thread Display & Metadata

| Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `thread_show_roles` | Boolean | Yes | Displays user’s roles in new thread info. | Helpful for context. |
| `thread_show_account_age` | Boolean | Yes | Displays account age in new thread info. | Helps detect alts. |
| `thread_show_join_age` | Boolean | Yes | Displays server join age in new thread info. | Contextual metadata. |
| `thread_creation_response` | Message | *Embed with user/thread info* | Message shown to user when thread opens. | Includes close emoji if enabled. |
| `thread_close_response` | Message | `"The thread has been closed. Thank you!"` | Message shown on manual close. | Fully customizable. |
| `thread_auto_close_response` | Message | `"This thread was closed due to inactivity."` | Sent on auto-close. | Requires `thread_auto_close`. |
| `thread_close_footer` | String | `"Have a great day!"` | Footer added to close message. | Optional. |
| `thread_activity_alerts` | Boolean | Enabled | Notifies mods of thread activity. | Keeps staff aware. |
| `thread_priority_tag` | Choice | `normal` | Default priority for threads. | `low`, `normal`, or `high`. |
| `thread_priority_color` | Color | None | Highlight color for high-priority threads. | Optional visual indicator. |


---

## 📦 Logging & Archiving

| Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `log_channel_id` | Channel ID | `#bot-logs` | Channel for Modmail logs. | Must exist or logging fails. |
| `log_format` | Choice | `compact` | Format for logs. | Options: compact, detailed, json. |
| `log_embed_color` | Color | `#7289DA` | Embed color for logs. | Overrides main color. |
| `log_expiration` | Duration | Never | Deletes old logs after duration. | Optional cleanup. |
| `archive_channel_id` | Channel ID | None | Channel for archived threads. | Optional. |
| `archive_expiration` | Duration | Never | Deletes archives after set time. | Use `{prefix}config del` to disable. |
| `update_channel_id` | Channel ID | Log Channel | Channel for update notifications. | Used by update system. |
| `update_notifications` | Boolean | Yes | Sends update announcements. | Requires updates enabled. |
| `modmail_logging_level` | Choice | `info` | Log detail level. | `debug`, `info`, `warning`, `error`. |


---

## 📣 Mentions, Alerts & Notifications

| Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `mention_channel_id` | Channel ID | Log Channel | Channel where mentions are posted. | Used when `alert_on_mention` is enabled. |
| `alert_on_mention` | Boolean | Disabled | Alerts mods when bot is mentioned. | Requires `mention_channel_id`. |
| `support_role_id` | Role ID | None | Role mentioned when new threads open. | Commonly @Support or @Moderators. |
| `sent_emoji` | Emoji | ✅ | Emoji for successful Modmail actions. | Used in reactions or confirmations. |
| `blocked_emoji` | Emoji | 🚫 | Emoji for failed actions. | Used in logs and messages. |
| `status_channel_id` | Channel ID | None | Channel where status/uptime messages appear. | Optional. |


---

## ⚙️ Automation, Tags & Updates

| Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `auto_tag` | Boolean | Disabled | Automatically tags threads using rules. | Uses `auto_tag_rules`. |
| `auto_tag_rules` | JSON Object | None | Defines automatic tagging logic. | Keyword or regex rules. |
| `auto_update_interval` | Duration | `7 days` | Time between automatic update checks. | Used when autoupdates are active. |
| `disable_autoupdates` | Boolean | No | Prevents the bot from auto-updating. | Manual updates only. |


---

## 🚨 Access & Security Controls

| Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `account_age` | Duration | None | Minimum account age required to DM Modmail. | Anti-spam measure. |
| `guild_age` | Duration | None | Minimum server join age required to use Modmail. | Works alongside `account_age`. |



{% endtab %}

{% tab title="Uncategorized Vars" %} | Name | Type | Default Value | Description | Notes |
|------|------|----------------|--------------|--------|
| `twitch_url` | URL | `https://www.twitch.tv/discordmodmail/` | Linked Twitch channel when activity is set to “Streaming”. | Has no effect when not streaming. See also: `{prefix}help activity`. |
| `main_category_id` | Category ID | `Modmail` (created with `{prefix}setup`) | Category where new threads are created. | Must be valid or Modmail will break. See also: `fallback_category_id`. |
| `fallback_category_id` | Category ID | `Fallback Modmail` | Category used when main category is full. | Automatically created if invalid. See also: `main_category_id`. |
| `prefix` | String | `?` | The command prefix for the bot. | Bot also responds to direct mention if prefix is forgotten. |
| `mention` | String | `@here` | Message shown above user info when a new thread is created. | Use `{prefix}mention disable` to disable. See also: `{prefix}help mention`. |
| `main_color` | Color | Discord Blurple `#7289DA` | Main color for embeds and Modmail UI. | See also: `error_color`, `mod_color`, `recipient_color`. |
| `error_color` | Color | Discord Red `#E74C3C` | Color for errors or warnings. | See also: `main_color`, `mod_color`, `recipient_color`. |
| `user_typing` | Boolean | Enabled | Shows typing indicator to mods when user types in DM. | See also: `mod_typing`. |
| `use_user_id_channel_name` | Boolean | No | Names threads with recipient’s user ID. | Mutually exclusive with timestamp/random/nickname options. |
| `use_timestamp_channel_name` | Boolean | No | Names threads by account creation date. | Mutually exclusive with user ID/random/nickname options. |
| `use_nickname_channel_name` | Boolean | No | Names threads by recipient’s nickname. | Not suitable for Server Discovery. Mutually exclusive with other naming options. |
| `use_random_channel_name` | Boolean | No | Names threads with random characters tied to user ID. | Suitable for Server Discovery. Mutually exclusive with other naming options. |
| `mod_typing` | Boolean | Disabled | Shows typing indicator to user when mod types in thread. | See also: `user_typing`. |
| `account_age` | Duration | No age threshold | Minimum account age required to DM Modmail. | Use `{prefix}config del account_age` to remove. See also: `guild_age`. |
| `guild_age` | Duration | No age threshold | Minimum server join age required to DM Modmail. | Use `{prefix}config del guild_age` to remove. See also: `account_age`. |
| `reply_without_command` | Boolean | Disabled | Forwards thread messages automatically without `{prefix}reply`. | See also: `anon_reply_without_command`, `plain_reply_without_command`. |
| `anon_reply_without_command` | Boolean | Disabled | Forwards messages anonymously without `{prefix}reply`. | See also: `reply_without_command`, `plain_reply_without_command`. |
| `plain_reply_without_command` | Boolean | Disabled | Forwards plain messages without `{prefix}reply`. | See also: `reply_without_command`, `anon_reply_without_command`. |
| `log_channel_id` | Channel ID | `#bot-logs` (created with `{prefix}setup`) | Channel for logs (thread close, updates, etc.). | Must be valid or logs won’t be sent. |
| `mention_channel_id` | Channel ID | Log Channel (`#bot-logs`) | Channel where bot mentions are sent. | Only used when `alert_on_mention` is enabled. |
| `update_channel_id` | Channel ID | Log Channel (`#bot-logs`) | Channel where update notifications are sent. | Requires updates enabled. See also: `update_notifications`. |
| `update_notifications` | Boolean | Yes | Enables update notification messages. | Requires `disable_autoupdates` = no. |
| `sent_emoji` | Emoji | ✅ | Emoji for successful Modmail actions. | Can be disabled or customized. See also: `blocked_emoji`. |
| `blocked_emoji` | Emoji | 🚫 | Emoji for failed Modmail actions. | Can be disabled or customized. See also: `sent_emoji`. |
| `close_emoji` | Emoji | 🔒 | Emoji recipients can click to close a thread. | Requires `recipient_thread_close` enabled. |
| `recipient_thread_close` | Boolean | Disabled | Allows recipients to close threads themselves. | Uses `close_emoji`. |
| `thread_show_roles` | Boolean | Yes | Shows user’s roles in new thread message. | See also: `thread_show_account_age`, `thread_show_join_age`. |
| `thread_show_account_age` | Boolean | Yes | Shows account age in new thread message. | See also: `thread_show_roles`, `thread_show_join_age`. |
| `thread_show_join_age` | Boolean | Yes | Shows server join age in new thread message. | See also: `thread_show_account_age`, `thread_show_roles`. |
| `thread_auto_close_silently` | Boolean | No | Silently closes threads when auto-close triggers. | Requires `thread_auto_close` set. |
| `thread_auto_close` | Duration | Never | Automatically closes threads after a duration. | Use `{prefix}config del thread_auto_close` to disable. |
| `thread_cooldown` | Duration | Never | Required cooldown before users can open a new thread. | Use `{prefix}config del thread_cooldown` to disable. |
| `log_expiration` | Duration | Never | How long closed threads are stored before deletion. | Use `{prefix}config del log_expiration` to disable. |
| `thread_cancelled` | Message | `"Thread creation has been cancelled."` | Message sent when a thread creation is cancelled by the user. | Can be customized to fit your server’s tone. |
| `thread_creation_response` | Message | *Embed with thread info and `close_emoji`* | Response shown to recipient when a thread is created. | Includes the close emoji if `recipient_thread_close` is enabled. |
| `thread_auto_close_response` | Message | `"This thread has been automatically closed due to inactivity."` | Message sent when a thread auto-closes. | Only sent if `thread_auto_close` is configured. |
| `thread_close_response` | Message | `"The thread has been closed. Thank you for reaching out!"` | Message shown to the recipient when the thread is closed manually. | Customizable farewell message. |
| `thread_close_footer` | String | `"Have a great day!"` | Footer added to the closing message. | Optional — leave blank to omit. |
| `recipient_thread_close_reason` | Boolean | Disabled | Requires the recipient to provide a reason when closing the thread. | Works only if `recipient_thread_close` is enabled. |
| `log_format` | Choice | `compact` | Defines how logs are formatted when exported or displayed. | Options: `compact`, `detailed`, or `json`. |
| `auto_tag` | Boolean | Disabled | Automatically tags threads based on user or content triggers. | Depends on predefined tag rules. |
| `auto_tag_rules` | JSON Object | None | Custom set of keyword-based or regex-based tag rules. | Used only if `auto_tag` is enabled. |
| `tag_color` | Color | Discord Blurple `#7289DA` | The default color used for tags. | See also: `main_color`. |
| `thread_blacklist_roles` | Role List | None | Roles that are not allowed to open Modmail threads. | Useful for bot roles or restricted groups. |
| `thread_blacklist_channels` | Channel List | None | Channels where Modmail DMs should not be forwarded. | Used to filter out unwanted threads. |
| `thread_blacklist_users` | User List | None | Users who cannot open Modmail threads. | Permanent restriction list. |
| `alert_on_mention` | Boolean | Disabled | Alerts mods when the bot is mentioned in chat. | Requires `mention_channel_id` to be set. |
| `disable_autoupdates` | Boolean | No | Prevents Modmail from automatically updating itself. | Set to `yes` to disable update checks. |
| `auto_update_interval` | Duration | `7 days` | Time interval between automatic update checks. | Only used when autoupdates are enabled. |
| `status_channel_id` | Channel ID | None | Channel for posting Modmail status updates or uptime info. | Optional but useful for monitoring. |
| `thread_auto_pin` | Boolean | Disabled | Automatically pins the first message in each thread. | Useful for keeping context visible. |
| `archive_channel_id` | Channel ID | None | Channel where archived threads are posted. | Optional archival feature. |
| `archive_expiration` | Duration | Never | Duration before archived threads are automatically deleted. | Use `{prefix}config del archive_expiration` to disable. |
| `thread_limit_per_user` | Integer | `1` | Maximum number of concurrent threads a user can have open. | Helps prevent spam or abuse. |
| `blocked_response` | Message | `"You cannot DM this bot."` | Message shown when a blocked user tries to DM Modmail. | Triggered when user is in blacklist. |
| `dm_notification` | Boolean | Enabled | Sends a DM notification to the mod when a user starts a new thread. | May be disabled to reduce noise. |
| `modmail_logging_level` | Choice | `info` | Determines how much detail is logged by Modmail. | Options: `debug`, `info`, `warning`, `error`. |
| `thread_channel_topic_template` | Template String | `"Thread for {user.name} ({user.id})"` | Template for thread channel topics. | Supports placeholders like `{user.name}` and `{user.id}`. |
| `log_embed_color` | Color | Discord Blurple `#7289DA` | Color used for log embed messages. | Overrides `main_color` for log embeds. |
| `support_role_id` | Role ID | None | Role automatically mentioned when a new thread is opened. | Useful for mod or support team visibility. |
| `moderator_cooldown` | Duration | `None` | Minimum delay between mod responses to avoid spam. | Optional anti-flood control for staff. |
| `thread_activity_alerts` | Boolean | Enabled | Notifies moderators when there’s new activity in threads. | May be disabled for low-traffic servers. |
| `mod_reply_indicator` | Emoji | 💬 | Emoji added to indicate mod messages in the thread. | Helps visually distinguish mod messages. |
| `thread_priority_tag` | Choice | `normal` | Default priority level assigned to new threads. | Options: `low`, `normal`, `high`. |
| `thread_priority_color` | Color | None | Highlight color for high-priority threads. | Optional for visual distinction. |
| `recipient_language` | Language Code | `en` | Sets the language for messages sent to users. | Requires translation files to be configured. |
| `mod_language` | Language Code | `en` | Sets the language for mod-facing messages. | Useful for multilingual teams. |
| `anonymous_mod_replies` | Boolean | Disabled | Makes all mod replies anonymous by default. | Can be overridden per message with `{prefix}reply anon`. |
| `thread_lockdown_mode` | Boolean | Disabled | Prevents users from opening threads temporarily. | Useful for maintenance or emergencies. |
| `lockdown_reason` | String | `"Modmail temporarily unavailable."` | Message displayed when thread creation is disabled. | Shown to users when lockdown is active. |
 {% endtab %}

{% endtabs %}



Accepted color names can be found here: {% page-ref page="color-names.md" %}.

> AI Transparency Statement: Content on this page was compiled using Generative AI technologies for the benefit of our users. If you find an error in this content, please contact our Support Team. [discord.gg/zmdYe3ZVHG](https://discord.gg/zmdYe3ZVHG)