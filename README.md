# EA Sales Bot

A friendly Telegram bot that answers buyers' questions and sells an MT5 Expert Advisor, with payment approval, delivery, licences and reminders.

> **Keep this repository private.** Never commit `config.json` after you've put your real bot token in it. Anyone with the token can control your bot.

## Setup

You need Python 3 (free from python.org). No other installs are needed.

### 1. Create the bot
1. In Telegram, open **@BotFather** and send `/newbot`.
2. Pick a name and a username. BotFather replies with a **token**.
3. Paste the token into `config.json` as `"bot_token"`.

### 2. Make yourself the admin
1. Run the bot: `python3 bot.py`
2. In Telegram, send your bot `/myid`.
3. Put that number into `config.json` as `"admin_chat_id"` (no quotes), then stop the bot (Ctrl+C) and start it again.

### 3. Upload your EA file
Send the **.ex5** file to your bot with the caption `/setfile`. Send only the compiled .ex5, never the .mq5 source.

### 4. Edit what the bot says
Everything is in `config.json`. Restart the bot after you change it.
- **product**: name, simple description, features, results link
- **plans**: prices
- **payment_instructions**: your bank and USDT details
- **smart_replies**: answers to typed questions. Each entry has `keywords` (words people might type) and an `answer`. Add as many as you like. Answers can use `{price_list}`, `{results_url}`, `{min_balance}`, `{setup_guide}` and `{support}`.
- **payment_reminder_hours**: how long to wait before reminding someone who hasn't paid (set it to 0 to turn reminders off)

## What the bot does
- Greets new people and asks whether they're new to trading robots, then explains things at their level
- Answers questions people type in their own words ("how much?", "is it a scam?", "which broker?")
- Passes any question it can't answer to you. **Reply** to that message in Telegram and the bot sends your answer to the buyer.
- Walks buyers through buying in 3 steps: plan, MT5 account number, payment
- Sends one friendly reminder if someone orders but doesn't send a receipt
- Sends you each receipt with Approve and Reject buttons. When you tap Approve, it delivers the EA and the setup guide.

## Admin commands
- `/pending`: receipts waiting for you
- `/stats`: people and orders
- `/licenses`: licensed MT5 account numbers
- `/broadcast <text>`: message everyone who has started the bot
- `/adminhelp`: shows this list

## Keeping it online
The bot works only while `bot.py` is running. To keep it up 24/7, run it on the same VPS as your EA.
