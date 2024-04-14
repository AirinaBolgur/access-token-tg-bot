# 🤖 TON Token Access Control Bot

[![TON](https://img.shields.io/badge/TON-grey?logo=TON&logoColor=40AEF0)](https://ton.org)
[![Telegram Bot](https://img.shields.io/badge/Bot-grey?logo=telegram)](https://core.telegram.org/bots)
[![Python](https://img.shields.io/badge/Python-3.10-blue.svg)](https://www.python.org/downloads/release/python-3100/)
[![License](https://img.shields.io/github/license/nessshon/token-access-control-bot)](https://github.com/nessshon/token-access-control-bot/blob/main/LICENSE)
[![Redis](https://img.shields.io/badge/Redis-Yes?logo=redis&color=white)](https://redis.io/)
[![Docker](https://img.shields.io/badge/Docker-blue?logo=docker&logoColor=white)](https://www.docker.com/)

TON Token Access Control Bot is a specialized bot that utilizes NFT tokens and/or Jettons to manage access to your
private
Telegram chats. This convenient solution allows you to control who has access to your groups and when, using tokens as
unique non-transferable identifiers for each participant.

* Bot example: [@TONTokenAccessControlBot](https://t.me/TONTokenAccessControlBot)

## Features

* **Token Access Control:** Allows access via NFT tokens and Jettons, with customizable token limits.

* **Testnet and Mainnet Support:** Flexible testing and deployment on both networks.

* **TON-Connect Integration:** Ensures a secure and user-friendly experience.

* **User-Friendly Admin Panel:** Built-in panel for easy administration.

* **Multilingual Support:** Supports Russian and English for user interaction.

* **Newsletters to All Users:** Distributes newsletters to all users, including delayed scheduling.

## Usage

<details>
<summary><b>Preparation and installation</b></summary>

1. Create a private group and/or channel.

2. Create a bot via [@BotFather](https://t.me/BotFather) and save the `TOKEN` (later referred to as `BOT_TOKEN`).

3. Create an API key on [tonconsole.com](https://tonconsole.com) (later referred to as `TONAPI_KEY`).

4. Obtain a key for TON Connect (Optional, later referred to as `TONAPI_TONCONNECT_KEY`).
   <blockquote>This key is necessary for the
   proper functioning of TON Connect on the backend under heavy user load. You can get the key by
   contacting <a href="https://t.me/subden" alt=''">@subden</a>  via private message. Inform him about your project and the need for this
   key.</blockquote>

5. Clone the repository:

    ```bash
    git clone https://github.com/nessshon/token-access-control-bot.git
    ```

6. Navigate to the bot directory:

    ```bash
    cd token-access-control-bot
    ```

7. Clone the environment variables file:

   ```bash
   cp .env.example .env
   ```

8. Configure [environment variables](#environment-variables-reference) variables file:

   ```bash
   nano .env
   ```

9. Install Docker and Docker Compose:

   ```bash
   sudo apt install docker.io && docker-compose -y
   ```

10. Run the bot in a Docker container:

    ```bash
    docker-compose up --build
    ```

11. Start the bot with the command `/start`, choose the language, and connect wallet.

12. Access the admin panel with the command `/admin` and add the token.

13. Add the bot to your private chat, ensuring you grant permissions to add administrators. After that, the bot will
    prompt you to add the chat to the database for monitoring.

14. You're all set!

<blockquote>
Customize the bot's texts in the <a href="https://github.com/nessshon/token-access-control-bot/blob/main/app/texts.py">texts</a> file according to your requirements. Additionally, if desired, add your preferred language to <a href="https://github.com/nessshon/token-access-control-bot/blob/main/app/texts.py#L4">SUPPORTED_LANGUAGES</a> and insert the corresponding codes into <a href="https://github.com/nessshon/token-access-control-bot/blob/main/app/texts.py#L9">TEXT_BUTTONS</a> and <a href="https://github.com/nessshon/token-access-control-bot/blob/main/app/texts.py#L54">TEXT_MESSAGES</a>.
</blockquote>

</details>

## Environment Variables Reference

<details>
<summary><b>Click to expand</b></summary>

Here's a comprehensive reference guide for the environment variables used in the project:

| Variable                                  | Type   | Description                                                                                                                                                                                                                   | Example                                                                                   |
|-------------------------------------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| `BOT_TOKEN`                               | `str`  | Bot token obtained from [@BotFather](https://t.me/BotFather)                                                                                                                                                                  | `123456:qweRTY`                                                                           | 
| `BOT_DEV_ID`                              | `int`  | User ID of the bot developer, obtain it from [my_id_bot](https://t.me/my_id_bot)                                                                                                                                              | `123456789`                                                                               |
| `BOT_ADMIN_ID`                            | `int`  | User ID of the bot admin, obtain it from [my_id_bot](https://t.me/my_id_bot)                                                                                                                                                  | `123456789`                                                                               |
| `IS_TESTNET`                              | `bool` | Set to `True` for TON testnet or `False` for mainnet                                                                                                                                                                          | `False`                                                                                   |
| `MANIFEST_URL`                            | `str`  | URL of the bot's manifest file                                                                                                                                                                                                | `https://github.com/nessshon/token-access-control-bot/blob/main/tonconnect-manifest.json` |
| `TONAPI_KEY`                              | `str`  | API key for TONAPI, obtain it from [tonconsole.com](https://tonconsole.com)                                                                                                                                                   | `AE33E...3FYQ`                                                                            |
| `TONAPI_TONCONNECT_KEY`                   | `str`  | API key for TON Connect (optional), obtain it by contacting [@subden](https://t.me/subden)                                                                                                                                    | `587d4...5a71`                                                                            |
| `SCHEDULER_CHECK_CHAT_MEMBERS_INTERVAL`   | `int`  | Interval (minutes) for checking chat members (1-5 minutes is acceptable)                                                                                                                                                      | `587d4...5a71`                                                                            |
| `SCHEDULER_UPDATE_TOKEN_HOLDERS_INTERVAL` | `int`  | Interval (minutes) for updating token holders (adjust value by Jetton holders or NFT elements. Every 1000 tokens or holders equals 1-2 seconds. For instance, for collections with 30k or fewer elements, set the value to 1) | `587d4...5a71`                                                                            |
| `REDIS_HOST`                              | `str`  | Hostname or IP address of the Redis server (set `redis` if you don't have your own Redis server)                                                                                                                              | `redis`                                                                                   |
| `REDIS_PORT`                              | `int`  | Port number of the Redis server (set `6379` if you don't have your own Redis server)                                                                                                                                          | `6379`                                                                                    |
| `REDIS_DB`                                | `int`  | Redis database number (set `0` if you don't have your own Redis server)                                                                                                                                                       | `0`                                                                                       |

</details>

## Contribution

We welcome your contributions! If you have ideas for improvement or have identified a bug, please create an issue or
submit a pull request.

## Donations

**TON** - `EQC-3ilVr-W0Uc3pLrGJElwSaFxvhXXfkiQA3EwdVBHNNess`

**USDT** (TRC-20) - `TJjADKFT2i7jqNJAxkgeRm5o9uarcoLUeR`

## Support

Supported by [TON Society](https://github.com/ton-society/grants-and-bounties), Grants and Bounties program.

## License

This repository is distributed under
the [MIT License](https://github.com/nessshon/token-access-control-bot/blob/main/LICENSE).
