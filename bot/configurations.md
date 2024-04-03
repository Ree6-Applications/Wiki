---
description: >-
  This page contains the entire config file content as a table, we have marked
  what you will need to run the bot. And its default values and
  descriptions/explanations.
---

# Configurations

## NOTE

The current content is based on the pre-release of Ree6 V3.

## Config file

| Name                               | Description                                                                                                          | default                                    | required                    |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ | --------------------------- |
| `config.version`                   | The config file version                                                                                              | 2.0.0                                      | yes                         |
| `config.creation`                  | The config file creation time                                                                                        | ?                                          | yes                         |
| `hikari.sql.user`                  | The SQL username                                                                                                     | root                                       | yes                         |
| `hikari.sql.db`                    | The SQL Databasename                                                                                                 | root                                       | yes                         |
| `hikari.sql.pw`                    | The SQL password                                                                                                     | yourpw                                     | yes                         |
| `hikari.sql.host`                  | The SQL Server address                                                                                               | localhost                                  | yes                         |
| `hikari.sql.port`                  | The SQL Server port                                                                                                  | 3306                                       | yes                         |
| `hikari.misc.storage`              | Possible entries: sqlite, mariadb, postgresql, h2, h2-server                                                         | sqlite                                     | no                          |
| `hikari.sql.storageFile`           | The SQL storage file                                                                                                 | storage/Ree6.db                            | no                          |
| `hikari.misc.createEmbeddedServer` | Should an instance of an embedded Server be created? Only used for H2-Server.                                        | false                                      | no                          |
| `hikari.sql.poolSize`              | Hikari SQL pool size                                                                                                 | 10                                         | yes                         |
| `bot.tokens.release`               | Token used when set to release build.                                                                                | ReleaseTokenhere                           | yes                         |
| `bot.tokens.beta`                  | Token used when set to beta build.                                                                                   | BetaTokenhere                              | no                          |
| `bot.tokens.dev`                   | Token used when set to dev build.                                                                                    | DevTokenhere                               | no                          |
| `bot.misc.status`                  | The Status of the Bot.                                                                                               | ree6.de                                    | %guilds% Servers. (%shard%) |
| `bot.misc.feedbackChannelId`       | The Channel used for Feedback.                                                                                       | 0                                          | no                          |
| `bot.misc.ownerId`                 | The ID of the Bot Owner. Change this to yours!                                                                       | 321580743488831490                         | yes                         |
| `bot.misc.predefineInformation`    | Predefined Information for the AI.                                                                                   | You are Ree6 a Discord bot.                | no                          |
| `bot.misc.invite`                  | The Invite Link of the Bot.                                                                                          | https://invite.ree6.de                     | no                          |
| `bot.misc.support`                 | The Support Server Link of the Bot.                                                                                  | https://support.ree6.de                    | no                          |
| `bot.misc.github`                  | The GitHub Link of the Bot.                                                                                          | https://github.ree6.de                     | no                          |
| `bot.misc.website`                 | The Website Link of the Bot.                                                                                         | https://ree6.de                            | no                          |
| `bot.misc.webinterface`            | The Webinterface Link of the Bot.                                                                                    | https://cp.ree6.de                         | no                          |
| `bot.misc.record`                  | The Recording Link of the Bot.                                                                                       | https://cp.ree6.de/external/recording      | no                          |
| `bot.misc.twitchAuth`              | The Twitch AuthenticationLink of the Bot.                                                                            | https://cp.ree6.de/external/twitch         | no                          |
| `bot.misc.advertisement`           | The Advertisement in Embed Footers and the rest.                                                                     | powered by Tube-hosting                    | no                          |
| `bot.misc.name`                    | The Name of the Bot.                                                                                                 | Ree6                                       | yes                         |
| `bot.misc.shards`                  | The shard amount of the Bot. Check out https://anidiots.guide/understanding/sharding/#sharding for more information. | 1                                          | yes                         |
| `bot.misc.modules.moderation`      | Enable the moderation module.                                                                                        | true                                       | no                          |
| `bot.misc.modules.music`           | Enable the music module.                                                                                             | true                                       | no                          |
| `bot.misc.modules.fun`             | Enable the fun commands.                                                                                             | true                                       | no                          |
| `bot.misc.modules.community`       | Enable the community commands.                                                                                       | true                                       | no                          |
| `bot.misc.modules.economy`         | Enable the economy commands.                                                                                         | true                                       | no                          |
| `bot.misc.modules.level`           | Enable the level module.                                                                                             | true                                       | no                          |
| `bot.misc.modules.nsfw`            | Enable the nsfw module.                                                                                              | true                                       | no                          |
| `bot.misc.modules.info`            | Enable the info commands.                                                                                            | true                                       | no                          |
| `bot.misc.modules.hidden`          | Enable the hidden commands.                                                                                          | true                                       | no                          |
| `bot.misc.modules.logging`         | Enable the logging module.                                                                                           | true                                       | no                          |
| `bot.misc.modules.notifier`        | Enable the notifier module.                                                                                          | true                                       | no                          |
| `bot.misc.modules.streamtools`     | Enable the Stream-tools module.                                                                                      | true                                       | no                          |
| `bot.misc.modules.temporalvoice`   | Enable the Temporal-voice module.                                                                                    | true                                       | no                          |
| `bot.misc.modules.tickets`         | Enable the Tickets module.                                                                                           | true                                       | no                          |
| `bot.misc.modules.suggestions`     | Enable the suggestions module.                                                                                       | true                                       | no                          |
| `bot.misc.modules.customcommands`  | Enable the custom Commands module.                                                                                   | true                                       | no                          |
| `bot.misc.modules.customevents`    | Enable the custom Events module.                                                                                     | true                                       | no                          |
| `bot.misc.modules.ai`              | Enable the AI module.                                                                                                | true                                       | no                          |
| `bot.misc.modules.addons`          | Enable the Addons module.                                                                                            | false                                      | no                          |
| `bot.misc.modules.news`            | Enable the news command/module.                                                                                      | true                                       | no                          |
| `bot.misc.modules.games`           | Enable the Games module.                                                                                             | true                                       | no                          |
| `bot.misc.modules.reactionroles`   | Enable the reaction-roles module.                                                                                    | true                                       | no                          |
| `bot.misc.modules.slashcommands`   | Enable the slash-commands support.                                                                                   | true                                       | no                          |
| `bot.misc.modules.messagecommands` | Enable the message-commands support.                                                                                 | true                                       | no                          |
| `heartbeat.url`                    | The URL to the Heartbeat-Server                                                                                      | none                                       | no                          |
| `heartbeat.interval`               | The Interval of the Heartbeat                                                                                        | 60                                         | no                          |
| `dagpi.apitoken`                   | Your Dagpi.xyz API-Token, for tweet image generation!                                                                | DAGPI.xyz API-Token                        | no                          |
| `amari.apitoken`                   | Your Amari API-Token, for Amari Level imports!                                                                       | Amari API-Token                            | no                          |
| `openai.apiToken`                  | Your OpenAI API-Token, for ChatGPT!                                                                                  | OpenAI API-Token                           | no                          |
| `openai.apiUrl`                    | The URL to the OpenAI API.                                                                                           | https://api.openai.com/v1/chat/completions | no                          |
| `openai.model`                     | The Model used for the OpenAI API.                                                                                   | gpt-3.5-turbo-0301                         | no                          |
| `sentry.dsn`                       | Your Sentry DSN, for error reporting!                                                                                | yourSentryDSNHere                          | no                          |
| `spotify.client.id`                | Your Spotify Application Client Id                                                                                   | yourspotifyclientid                        | no                          |
| `spotify.client.secret`            | Your Spotify Application Client Secret                                                                               | yourspotifyclientsecret                    | no                          |
| `twitch.client.id`                 | Your Twitch Application Client Id                                                                                    | yourtwitchclientid                         | no                          |
| `twitch.client.secret`             | Your Twitch Application Client Secret                                                                                | yourtwitchclientsecret                     | no                          |
| `twitter.bearer`                   | Your Twitter APIv2 Bearer Token                                                                                      | yourTwitterBearerToken                     | no                          |
| `reddit.client.id`                 | Your Reddit Application Client Id                                                                                    | yourredditclientid                         | no                          |
| `reddit.client.secret`             | Your Reddit Application Client Secret                                                                                | yourredditclientsecret                     | no                          |
| `instagram.username`               | Your Instagram Username                                                                                              | yourInstagramUsername                      | no                          |
| `instagram.password`               | Your Instagram Password                                                                                              | yourInstagramPassword                      | no                          |
