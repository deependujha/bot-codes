---
title: Create & Manage a Telegram Bot
type: docs
sidebar:
  open: false
weight: 101
math: false
---

## Creating a Telegram Bot

![botfather](/telegram/botfather.png)

- Search for [BotFather](https://t.me/BotFather) on Telegram. (`make sure to use the official BotFather account`)
- Start a chat and use the `/newbot` command to create a new bot.
- Follow the prompts to set a name and username for your bot.
- After creation, BotFather will provide you with a **`token`**. Keep this token safe, as it is required to access the Telegram Bot API.
- Optionally, you can set a profile picture and description for your bot using BotFather commands.

---

## Managing Your Telegram Bot

- Create a python project, and activate a virtual environment:

```bash
uv init --package my-tele-bot
cd my-tele-bot
uv venv
source .venv/bin/activate
```

- Install the `pyTelegramBotAPI` library:

```bash
uv add pyTelegramBotAPI

# to update
uv add pyTelegramBotAPI --upgrade
```

- check documentation for more details: [pyTelegramBotAPI Documentation](https://github.com/eternnoir/pyTelegramBotAPI/tree/master?tab=readme-ov-file#getting-started)

```python
import telebot

bot = telebot.TeleBot("YOUR_BOT_TOKEN")

@bot.message_handler(commands=['start', 'help'])
def send_welcome(message):
	bot.reply_to(message, "Howdy, how are you doing?")

@bot.message_handler(func=lambda message: True)
def echo_all(message):
	bot.reply_to(message, message.text)

bot.infinity_polling()
```
