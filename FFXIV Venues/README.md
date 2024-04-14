## Assumptions

* You have WSL, docker, and docker compose installed
* You have an IDE such as Visual Studio, JetBrains Riders, VS Code or fleet
* You know how to set user-secrets with your IDE

## Notes

This stack does not currently include the React frontend client.

## Getting Started

1) Clone or download the files in [this directory](https://github.com/FFXIVVenues/ffxivvenues-infrastructure/tree/master/FFXIV%20Venues).  
2) Edit the `.env` file and add all the relevant settings for Veni and API (see [Compose Variables](#Compose Variables) for more information).
3) [Local Development Only] Add a `ports` section with a `- "5432:5432"` port mapping inside to the `postgres` service definition of the `docker-compose.yml`.
4) [Local Development Only] Add a `ports` section with a `- "27017:27017"` port mapping inside to the `mongo` service definition of the `docker-compose.yml`
5) Open WSL at the location of the file and run `docker compose up -d`

You should now have a working API and Veni stack. 

## Compose Variables

| Variable Name | Description |
|---------------|-------------|
| API_AUTH_KEY  | Provide an authentication key that will be used for the API to authenticate calling clients. This key will have all permissions and full scope, and will be used for Veni in this stack. |
| API_PUBLIC_URI | Provide the base public URI (without trailing slash) that the API will be running on, such as `http://api.myvenues.com`. For local/development, this can be left as `http://localhost:5001` |
| POSTGRES_PASSWORD | Provide a password that will be used for the Postgres instance and by the API to authenticate with it. |
| DISCORD_CLIENT_ID | Provide the Client ID for the Discord application setup in the [Discord Developers Portal](https://discord.com/developers). This will be used for OAuth2 Discord SSO authentication. |
| DISCORD_CLIENT_SECRET | Provide the Client Secret for the Discord application setup in the [Discord Developers Portal](https://discord.com/developers). This will be used for OAuth2 Discord SSO authentication. |
| UI_PUBLIC_URI | Provide the base public URI (without trailing slash) that the React Web UI will be running on (if any), such as `http://myvenues.com`. For local/development, this can be left as `http://localhost:3000` |
| DISCORD_BOT_TOKEN | Provide the Bot Token for the Discord bot setup in the [Discord Developers Portal](https://discord.com/developers). This will be used to authenticate and use the Discord API. |
| MASTER_DISCORD_USER_ID | Provide the Discord User ID for the user that should be able to use this instance of Veni with all permissions. |
| BETTERSTACK_LOGGING_TOKEN | Provide the Source Token from the Better Stack instance to which to sending logging. Optional. |

For further configuration, take a look at the `api.env` and `veni.env` files, and refer to the configuration documentation in the appropriate respository's READMEs. 
