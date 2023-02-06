---
description: How to use modmail
---

# How to use modmail

After initial setup is done, you can use modmail by using the in text commands. These use the prefix you set with the `prefix` command. The default prefix is `?`.
Users can DM the bot to start a thread. Any users or roles set with the `permissions` command can then see the thread in the server and reply to it.

## Replying

To reply to a thread, use the `reply` command inside the thread you wish to reply in. This will send a message to the thread. Image attachments and stickers are supported and will also be sent to the user.
Without command, any message sent in the thread will be seen as an internal message. This will not be visible to the user, but will still be logged to be viewed later in logviewer. If rather you want to send a message to the user without command, set the config variable `reply_without_command` to `true` using the `config` command.

## Closing

When communications with a user have come to a conclusion, the thread can be closed in a multitude of ways.
The recommended way is using the `close` command. By default, this will close the thread on invoking the command. A message will be sent to the user containing the value of the `thread_close_response` config variable. This can be changed using the `config` command. A one time override can be given by adding text to the `close` command. E.g. `?close Thanks for contacting us!` will send the message `Thanks for contacting us!` to the user instead of the default message.
A time can also be provided to the close command. This will result in the close being scheduled and will automatically close the thread after the given time has expired. Multiple formats for time are accepted, like `2m30s` or `5 hours`. A response message can also be added to a timed close. When either a staff member, or the user themselves, replies to the thread after the close has been scheduled, the close will be cancelled.

## Help command

To assist with command usage, every command has a description. This description can be retrieved by using the `help` command followed by the name of the command. E.g. `?help close` will show the description of the `close` command. Most command descriptions also contain examples of how to use the command. The `help` command can also be used without a command name to show a list of all commands.

## Snippets

The modmail bot has a snippet system to make frequent responses easier. Snippets can be created using the `snippet` command. This will create a snippet with the given name and content. The snippet can then be used by using the snippet name as a command. E.g. `?snippetname` will send the content of the snippet named `snippetname` to the thread. Using the `snippets` command will list all currently defined snippets. Using `snippet (snippet name)` will show the content of the snippet without sending it to the thread.

## Logging

All messages sent in a thread, including internal notes, are logged to the bot's database. When a thread is closed, a message will be sent by the bot in the logs channel containing a link to the log. This link can be used to view the log in the logviewer. In a thread, the `loglink` command can be used to retrieve the loglink before it is closed. This allows the user to view the log before it appears in the logs channel if required. Logviewer is read only, and cannot be used to edit or delete messages.