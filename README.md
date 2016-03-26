# Zoe Tgbot ![Agent version](https://img.shields.io/badge/Zoe_Agent-0.2.1-blue.svg "Zoe Tgbot")

Connect Zoe to Telegram using the new Bot API.

## Warning

This agent is not compatible with the original Telegram agent developed by
[@voiser](https://github.com/voiser). Although **it is closely based on his
code**, this version does not require a phone number to work.

Both agents share the same Agent name (`tg`) internally in order to reuse already
implemented code in the library core.

## Requirements

This agent uses
[pyTelegramBotAPI](https://github.com/eternnoir/pyTelegramBotAPI) in order to
poll the server for new messages and send messages to users. The `postinst`
script will install it automatically.

## Usage

Once installed, the file `ZOE_HOME/etc/tgbot.conf` will be created. In this
file, you will need to write your private Bot Token obtained from the [bot
creation process](https://core.telegram.org/bots#3-how-do-i-create-a-bot). Now
start the agent and you are ready to go.

The way this agent works is very similar to the `jabber` agent:

- Start a conversation with Zoe (or invite her to a group)
- For the agent to recognize a message, you should either include your bot's
  name in the message (`@BOT_NAME ayuda`) or start the message with a `/`
  character
- The message is parsed and the `natural` agent matches it with natural
  language commands in `cmdproc/`
- Magic happens

Note that there are no `/` commands as defined in the Telegram Bot API. We do
things our own way (and it works!).

## User configuration

If you want to start speaking with Zoe through Telegram, you must first add
your Telegram ID in the `tg` section of the `ZOE_HOME/etc/zoe-users.conf` file.

**You don't know your own unique ID???** No problem, just write your username
(without @) and the agent will tell you so you can add it. It is very important
to add this unique ID (either in the form of `user#xxxx` or `group#xxxx`),
because that's the way the agent sends messages to you when demanded by other
agents (feedback of other agents, etc.).

## Groups

You may also use the agent in groups. The recommended way of doing so is by
creating a new Zoe user for that group in `ZOE_HOME/etc/zoe-users.conf` like:

~~~
[subject test]
name = text
preferred = tg
tg = group#-xxxxxx
locale = en
~~~

Of course, you may simply speak to her in the group without creating the user,
but only your commands will be executed and you may end up getting responses in
your private conversation with Zoe.
