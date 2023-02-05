# Seperate Server Setup

If you want to use a separate server to the main one as the inbox server (Where threads get relayed to) add the following config variables on Heroku:

* `MODMAIL_GUILD_ID` (the server where messages are sent to)
* `GUILD_ID` (The server where users message from)
