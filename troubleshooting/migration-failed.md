# Migration Failed!

## Unsupported Database: MariaDB xx.x

This error can happen if Flyway does not support your MariaDB version, but in most cases it's because Flyway is just a bit silly, or I messed something up :D!

You can bypass this issue by running a script to generate the base schematic of the database. This script will create all tables and add all Flyway entries so in case Flyway works again, it can start where the script stopped.

To run this script you can either use PhpMyAdmin to import this script, or access your mysql/mariadb server directly and run the script via that.

<details>

<summary>Base Schematic Script</summary>

{% code title="ree6_struture-05-01-2024.sql" overflow="wrap" %}
```sql
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;


CREATE TABLE IF NOT EXISTS `AutoRoles` (
  `guildId` bigint(20) NOT NULL,
  `roleId` bigint(20) NOT NULL,
  PRIMARY KEY (`guildId`,`roleId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `BirthdayWish` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) DEFAULT NULL,
  `channelId` bigint(20) DEFAULT NULL,
  `userId` bigint(20) DEFAULT NULL,
  `birthday` date DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=24 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `ChannelStats` (
  `guildId` bigint(20) NOT NULL,
  `memberChannelId` varchar(255) DEFAULT NULL,
  `onlyRealMemberChannelId` varchar(255) DEFAULT NULL,
  `botMemberChannelId` varchar(255) DEFAULT NULL,
  `twitterFollowerChannelId` varchar(255) DEFAULT NULL,
  `twitterFollowerChannelUsername` varchar(255) DEFAULT NULL,
  `instagramFollowerChannelId` varchar(255) DEFAULT NULL,
  `instagramFollowerChannelUsername` varchar(255) DEFAULT NULL,
  `twitchFollowerChannelId` varchar(255) DEFAULT NULL,
  `twitchFollowerChannelUsername` varchar(255) DEFAULT NULL,
  `youtubeSubscribersChannelId` varchar(255) DEFAULT NULL,
  `youtubeSubscribersChannelUsername` varchar(255) DEFAULT NULL,
  `subredditMemberChannelId` varchar(255) DEFAULT NULL,
  `subredditMemberChannelSubredditName` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`guildId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `ChatLevelAutoRoles` (
  `guildId` bigint(20) NOT NULL,
  `roleId` bigint(20) NOT NULL,
  `lvl` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`guildId`,`roleId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `ChatProtector` (
  `guildId` bigint(20) NOT NULL,
  `name` varchar(255) NOT NULL,
  PRIMARY KEY (`guildId`,`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `CommandStats` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `command` varchar(255) DEFAULT NULL,
  `uses` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=92 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `CustomCommands` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guild` bigint(20) DEFAULT NULL,
  `command` varchar(255) DEFAULT NULL,
  `responseChannel` bigint(20) DEFAULT NULL,
  `responseMessage` varchar(255) DEFAULT NULL,
  `responseEmbed` mediumblob DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `CustomEvents` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guild` bigint(20) DEFAULT NULL,
  `eventName` varchar(255) DEFAULT NULL,
  `eventTyp` varchar(255) DEFAULT NULL,
  `actions` mediumblob DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `flyway_schema_history` (
  `installed_rank` int(11) NOT NULL,
  `version` varchar(50) DEFAULT NULL,
  `description` varchar(200) NOT NULL,
  `type` varchar(20) NOT NULL,
  `script` varchar(1000) NOT NULL,
  `checksum` int(11) DEFAULT NULL,
  `installed_by` varchar(100) NOT NULL,
  `installed_on` timestamp NOT NULL DEFAULT current_timestamp(),
  `execution_time` int(11) NOT NULL,
  `success` tinyint(1) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

INSERT INTO `flyway_schema_history` (`installed_rank`, `version`, `description`, `type`, `script`, `checksum`, `installed_by`, `installed_on`, `execution_time`, `success`) VALUES
(1, '1', 'Initial', 'SQL', 'V1__Initial.sql', 868184986, 'Ree6-SQL', '2023-10-24 11:45:10', 236, 1),
(2, '2', 'Add Giveaway', 'SQL', 'V2__Add_Giveaway.sql', -1883877325, 'Ree6-SQL', '2023-10-24 11:45:10', 5, 1),
(3, '3', 'DataTyp Update', 'SQL', 'V3__DataTyp_Update.sql', 903780844, 'Ree6-SQL', '2024-01-05 09:51:16', 8001, 1),
(4, '4', 'FK Update', 'SQL', 'V4__FK_Update.sql', -787838562, 'Ree6-SQL', '2024-01-05 09:51:18', 2418, 1),
(5, '5', 'Correcting Names', 'SQL', 'V5__Correcting_Names.sql', 1070891862, 'Ree6-SQL', '2024-01-05 09:51:19', 535, 1),
(6, '6', 'Finishing FKs', 'SQL', 'V6__Finishing_FKs.sql', -1787610997, 'Ree6-SQL', '2024-01-05 09:51:20', 1901, 1),
(7, '7', 'FixingFKs', 'SQL', 'V7__FixingFKs.sql', -1253861431, 'Ree6-SQL', '2024-01-05 09:54:07', 166697, 1);

CREATE TABLE IF NOT EXISTS `Giveaway` (
  `messageId` bigint(20) NOT NULL,
  `creatorId` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channelId` bigint(20) NOT NULL,
  `prize` varchar(255) DEFAULT NULL,
  `winners` bigint(20) NOT NULL,
  `created` datetime DEFAULT NULL,
  `ending` datetime DEFAULT NULL,
  PRIMARY KEY (`messageId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `GuildStats` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `gid` bigint(20) DEFAULT NULL,
  `command` varchar(255) DEFAULT NULL,
  `uses` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=5346 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `InstagramNotify` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB AUTO_INCREMENT=13 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Invites` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) DEFAULT NULL,
  `uses` bigint(20) DEFAULT NULL,
  `code` varchar(255) NOT NULL,
  PRIMARY KEY (`guildId`,`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Level` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) NOT NULL,
  `xp` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`guildId`,`userId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `LogWebhooks` (
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `cid` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  PRIMARY KEY (`guildId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Money_Holder` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) NOT NULL,
  `cash` double DEFAULT NULL,
  `bank` double DEFAULT NULL,
  PRIMARY KEY (`guildId`,`userId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Money_Transaction` (
  `transactionId` bigint(20) NOT NULL AUTO_INCREMENT,
  `isSystemPayment` bit(1) NOT NULL,
  `guildId` bigint(20) DEFAULT NULL,
  `isReceiverBank` bit(1) NOT NULL,
  `isSenderBank` bit(1) NOT NULL,
  `amount` double DEFAULT NULL,
  `creation` datetime(6) DEFAULT NULL,
  `receiver_guildId` bigint(20) NOT NULL,
  `receiver_userId` bigint(20) NOT NULL,
  `sender_guildId` bigint(20) NOT NULL,
  `sender_userId` bigint(20) NOT NULL,
  PRIMARY KEY (`transactionId`),
  KEY `FK_MONEY_TRANSACTION_RECEIVER` (`receiver_guildId`,`receiver_userId`),
  KEY `FK_MONEY_TRANSACTION_SENDER` (`sender_guildId`,`sender_userId`)
) ENGINE=InnoDB AUTO_INCREMENT=14 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Opt_out` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) NOT NULL,
  PRIMARY KEY (`guildId`,`userId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Punishments` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `warnings` int(11) NOT NULL,
  `action` int(11) NOT NULL,
  `roleId` bigint(20) NOT NULL,
  `timeoutTime` bigint(20) NOT NULL,
  `reason` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `ReactionRole` (
  `guildId` bigint(20) NOT NULL,
  `emoteId` bigint(20) DEFAULT NULL,
  `formattedEmote` varchar(255) DEFAULT NULL,
  `channelId` bigint(20) DEFAULT NULL,
  `roleId` bigint(20) NOT NULL,
  `messageId` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`guildId`,`roleId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Recording` (
  `id` varchar(255) NOT NULL,
  `guildId` bigint(20) DEFAULT NULL,
  `channelId` bigint(20) DEFAULT NULL,
  `creator` bigint(20) DEFAULT NULL,
  `recording` text DEFAULT NULL,
  `participants` mediumblob DEFAULT NULL,
  `created` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `RedditNotify` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `subreddit` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `RSSFeed` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `url` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `ScheduledMessage` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `message` varchar(255) DEFAULT NULL,
  `delay` bigint(20) DEFAULT NULL,
  `shouldRepeat` bit(1) DEFAULT NULL,
  `webhook_id` bigint(20) NOT NULL,
  `lastExecute` datetime(6) DEFAULT NULL,
  `lastUpdated` datetime(6) DEFAULT NULL,
  `created` datetime(6) DEFAULT NULL,
  `webhook_guildId` bigint(20) NOT NULL,
  PRIMARY KEY (`id`,`guildId`),
  KEY `FK_SCHEDULEDMESSAGE_ON_WEBHOOK` (`webhook_id`),
  KEY `FK_SCHEDULED_MESSAGE_WEBHOOK` (`webhook_id`,`webhook_guildId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `ScheduledMessageWebhooks` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Settings` (
  `guildId` bigint(20) NOT NULL,
  `name` varchar(255) NOT NULL,
  `displayname` varchar(255) DEFAULT NULL,
  `value` text DEFAULT NULL,
  PRIMARY KEY (`guildId`,`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Statistics` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `day` int(11) DEFAULT NULL,
  `month` int(11) DEFAULT NULL,
  `year` int(11) DEFAULT NULL,
  `stats` mediumblob DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=461 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `StreamActions` (
  `guildId` bigint(20) NOT NULL,
  `name` varchar(255) NOT NULL,
  `auth_id` varchar(255) NOT NULL,
  `listener` int(11) DEFAULT NULL,
  `argument` varchar(255) DEFAULT NULL,
  `actions` mediumblob DEFAULT NULL,
  PRIMARY KEY (`guildId`,`name`),
  KEY `FK_STREAMACTIONS_ON_AUTH` (`auth_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Suggestions` (
  `guildId` bigint(20) NOT NULL,
  `channelId` bigint(20) NOT NULL,
  PRIMARY KEY (`guildId`,`channelId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `TemporalVoicechannel` (
  `guildId` bigint(20) NOT NULL,
  `channelId` bigint(20) NOT NULL,
  PRIMARY KEY (`guildId`,`channelId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Tickets` (
  `guildId` bigint(20) NOT NULL,
  `channelId` bigint(20) DEFAULT NULL,
  `ticketCategory` bigint(20) DEFAULT NULL,
  `logChannelId` bigint(20) DEFAULT NULL,
  `logChannelWebhookId` bigint(20) DEFAULT NULL,
  `logChannelWebhookToken` varchar(255) DEFAULT NULL,
  `ticketCount` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`guildId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `TikTokNotify` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `TwitchIntegration` (
  `channel_id` varchar(255) NOT NULL,
  `user_id` bigint(20) DEFAULT NULL,
  `token` varchar(255) DEFAULT NULL,
  `refresh` varchar(255) DEFAULT NULL,
  `channel_name` varchar(255) DEFAULT NULL,
  `expires` int(11) DEFAULT NULL,
  `lastUpdated` datetime(6) DEFAULT NULL,
  PRIMARY KEY (`channel_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `TwitchNotify` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB AUTO_INCREMENT=17 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `TwitterNotify` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB AUTO_INCREMENT=22 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `VCLevel` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) NOT NULL,
  `xp` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`guildId`,`userId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `VCLevelAutoRoles` (
  `guildId` bigint(20) NOT NULL,
  `roleId` bigint(20) NOT NULL,
  `lvl` bigint(20) DEFAULT NULL,
  PRIMARY KEY (`guildId`,`roleId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `Warning` (
  `userId` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `warnings` int(11) NOT NULL,
  PRIMARY KEY (`guildId`,`userId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `WelcomeWebhooks` (
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `cid` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  PRIMARY KEY (`guildId`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `YouTubeNotify` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`,`guildId`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;


ALTER TABLE `Money_Transaction`
  ADD CONSTRAINT `FK_MONEY_TRANSACTION_RECEIVER` FOREIGN KEY (`receiver_guildId`,`receiver_userId`) REFERENCES `Money_Holder` (`guildId`, `userId`),
  ADD CONSTRAINT `FK_MONEY_TRANSACTION_SENDER` FOREIGN KEY (`sender_guildId`,`sender_userId`) REFERENCES `Money_Holder` (`guildId`, `userId`);

ALTER TABLE `ScheduledMessage`
  ADD CONSTRAINT `FK_SCHEDULED_MESSAGE_WEBHOOK` FOREIGN KEY (`webhook_id`,`webhook_guildId`) REFERENCES `ScheduledMessageWebhooks` (`id`, `guildId`);

ALTER TABLE `StreamActions`
  ADD CONSTRAINT `FK_STREAMACTIONS_ON_AUTH` FOREIGN KEY (`auth_id`) REFERENCES `TwitchIntegration` (`channel_id`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;

```
{% endcode %}



</details>
