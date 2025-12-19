# Running the FFXIV Venues stack

## Assumptions

* You are on Linux and have docker, and docker compose installed

## Getting Started

1) Clone or download the files in [the infrastructure repository](https://github.com/FFXIVVenues/ffxivvenues-infrastructure/tree/main/FFXIV%20Venues).
```Bash Command
wget https://github.com/FFXIVVenues/ffxiv-venues-infrastructure/archive/refs/heads/main.zip && unzip main.zip && rm main.zip
```
2) Take and copy of `template.env`, naming it `.env` and add all the relevant settings configuration variables (see [Compose Variables](https://github.com/FFXIVVenues/ffxivvenues-infrastructure/blob/main/README.md#compose-variables) for more information).


3) Launch the stack with Docker Compose
```Back Command
docker compose up -d
```

You should now have a working Web, API and Veni stack.

## Compose Variables

| Variable Name | Description |
|---------------|-------------|
| UI_PUBLIC_URI | Provide the base public URI (without trailing slash) that the React Web UI will be running on (if any), such as `http://myvenues.com`. For local/development, this can be left as `http://localhost:3000` |
| API_PUBLIC_URI | Provide the base public URI (without trailing slash) that the API will be running on, such as `http://api.myvenues.com`. For local/development, this can be left as `http://localhost:5001` |
| DISCORD_BOT_TOKEN | Provide the Bot Token for the Discord bot setup in the [Discord Developers Portal](https://discord.com/developers). This will be used to authenticate and use the Discord API. |
| DISCORD_CLIENT_ID | Provide the Client ID for the Discord application setup in the [Discord Developers Portal](https://discord.com/developers). This will be used for OAuth2 Discord SSO authentication. |
| DISCORD_CLIENT_SECRET | Provide the Client Secret for the Discord application setup in the [Discord Developers Portal](https://discord.com/developers). This will be used for OAuth2 Discord SSO authentication. |
| MASTER_DISCORD_USER_ID | Provide the Discord User ID for the user that should be able to use this instance of Veni with all permissions. |
| MASTER_DISCORD_GUILD_ID | Provide the Discord Guild ID for the server that should receive all service level commands. |
| CLU_RUNTIME_KEY | Provide the API Key for Microsoft Cognitive Language APIs. Used for natural language commands. |
| BETTERSTACK_LOGGING_TOKEN | Provide the Source Token from the Better Stack instance to which to sending logging. Optional. |
| API_AUTH_KEY  | Provide an authentication key that will be used for the API to authenticate calling clients. This key will have all permissions and full scope, and will be used for Veni in this stack. |
| POSTGRES_PASSWORD | Provide a password that will be used for the Postgres instance and by the domain services to authenticate with it. |
| RABBITMQ_USER | Provide a username that will be used for the RabbitMQ instance and by the domain Service to authenticate with it. |
| RABBITMQ_PASSWORD | Provide a password that will be used for the RabbitMQ instance and by the domain services to authenticate with it. |
For further configuration, take a look at the `api.env` and `veni.env` files, and refer to the configuration documentation in the appropriate respository's READMEs.
