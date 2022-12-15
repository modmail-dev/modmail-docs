# Modmail Usage

### Basic Usage

Once someone DMs the bot a channel will be created for their thread. You can reply to their thread using the `[p]reply` command. Once you are done communicating you can use the `[p]close` command

### Ease of Use

You can configure aliases and snippets, which is highly recommended. For example, you can shorten the `reply` command to `r` (In case you want to do this you can use the command `[p]alias add r reply`)

You can use snippets to shorten text like "Thanks for Contacting Modmail Support! How can I help you today?" to a simple command such as `[p]hi` (In case you want to do this you can use the command `[p]snippets add hi Thanks for Contacting Modmail Support! How can I help you today?`)

### Advanced Usage

You can use times with the close command for example `[p]close 20m Bye` to close in 20 minutes with the reason "Bye" if you don't want to close on a timer but still add a reason you can use `[p]close Bye` which will close the thread with the reason "Bye"

### Anonymous Snippets

\[p]alias add \[snippetname] anonreply \[snippet text]

_Note: In this page, the meaning of `[p]` is `bot prefix` this defaults to `?` but can be changed with the `[p]prefix` command_
