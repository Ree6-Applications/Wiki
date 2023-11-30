---
description: A Guide about how to self host Ree6!
---

# Self hosting

## Requirements

* Java 17
* 2GB Ram

## Recommendation

* MariaDB/MySQL

## Pterodactyl

Incase you want to run Ree6 via Pterodactyl visit this [self-host-with-pterodactyl.md](self-host-with-pterodactyl.md "mention")

## Setup

### Builds

We have two different build types.\


The first one would be development builds, these are builds that are being created when ever a change happends.\
This can and will be unstable most of the time and might cause some Issues, but might also fix a major bug that is not in a release.

The second one are the release builds, these have been tested and should work as intended and be stable.\
We recommend to use these.

#### Development builds

These can be downloaded via our [CLI](https://github.com/Ree6-Applications/Ree6/actions/workflows/cli.yml).

#### Release builds

Download from our [release page](https://github.com/Ree6-Applications/Ree6/releases/latest).

You can either download the `Ree6-[x.x.x]-jar-with-dependencies.jar` for the Bot or download our Installer.\
The installer is called `Ree6-Installer-[x.x.x].jar`, it will help you with configurating the bot and download the latest file for you!

### Running the Bot

After downloading the desired file, you will need to run the file with Java.\
Running the Bot will cause a shutdown on first boot and you will need to update the `config.yml`.\
When using the Installer you will be prompted to configurate the bot before it downloads the latest file.\
For more informations and the defaults of the configurations visit our Configuration page: [configurations.md](../configurations.md "mention")

This should conclude all you need to selfhost Ree6!
