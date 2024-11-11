# Migration Failed!

## Unsupported Database: MariaDB xx.x

This error can happen if Flyway does not support your MariaDB version, but in most cases it's because Flyway is just a bit silly, or I messed something up :D!

You can bypass this issue by running a script to generate the base schematic of the database. This script will create all tables and add all Flyway entries so in case Flyway works again, it can start where the script stopped.

To run this script you can either use PhpMyAdmin to import this script, or access your mysql/mariadb server directly and run the script via that.

After running this script, the error will still occur but the Bot will just be able to start up and work as intended.

<details>

<summary>Base Schematic Script</summary>

{% code title="ree6_struture-11-11-2024.sql" overflow="wrap" %}
```sql
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

CREATE TABLE `AutoRoles` (
  `guildId` bigint(20) NOT NULL,
  `roleId` bigint(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `BirthdayWish` (
  `id` int(11) NOT NULL,
  `guildId` bigint(20) DEFAULT NULL,
  `channelId` bigint(20) DEFAULT NULL,
  `userId` bigint(20) DEFAULT NULL,
  `birthday` date DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `ChannelStats` (
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
  `subredditMemberChannelSubredditName` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `ChatLevelAutoRoles` (
  `guildId` bigint(20) NOT NULL,
  `roleId` bigint(20) NOT NULL,
  `lvl` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `ChatProtector` (
  `guildId` bigint(20) NOT NULL,
  `name` varchar(255) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `CommandStats` (
  `id` int(11) NOT NULL,
  `command` varchar(255) DEFAULT NULL,
  `uses` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `CustomCommands` (
  `id` bigint(20) NOT NULL,
  `guild` bigint(20) DEFAULT NULL,
  `command` varchar(255) DEFAULT NULL,
  `responseChannel` bigint(20) DEFAULT NULL,
  `responseMessage` varchar(255) DEFAULT NULL,
  `responseEmbed` varbinary(32600) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `CustomEvents` (
  `id` bigint(20) NOT NULL,
  `guild` bigint(20) DEFAULT NULL,
  `eventName` varchar(255) DEFAULT NULL,
  `eventTyp` varchar(255) DEFAULT NULL,
  `actions` varbinary(32600) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `flyway_schema_history` (
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
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

INSERT INTO `flyway_schema_history` (`installed_rank`, `version`, `description`, `type`, `script`, `checksum`, `installed_by`, `installed_on`, `execution_time`, `success`) VALUES
(1, '1', 'Initial', 'SQL', 'V1__Initial.sql', 868184986, 'Ree6-SQL', '2024-11-11 12:36:52', 1901, 1),
(2, '2', 'Add Giveaway', 'SQL', 'V2__Add_Giveaway.sql', -1883877325, 'Ree6-SQL', '2024-11-11 12:36:52', 102, 1),
(3, '3', 'DataTyp Update', 'SQL', 'V3__DataTyp_Update.sql', 903780844, 'Ree6-SQL', '2024-11-11 12:36:55', 2000, 1),
(4, '4', 'FK Update', 'SQL', 'V4__FK_Update.sql', -787838562, 'Ree6-SQL', '2024-11-11 12:36:58', 3134, 1),
(5, '5', 'Correcting Names', 'SQL', 'V5__Correcting_Names.sql', 1070891862, 'Ree6-SQL', '2024-11-11 12:37:00', 1275, 1),
(6, '6', 'Finishing FKs', 'SQL', 'V6__Finishing_FKs.sql', -1787610997, 'Ree6-SQL', '2024-11-11 12:37:02', 1314, 1),
(7, '7', 'FixingFKs', 'SQL', 'V7__FixingFKs.sql', -1253861431, 'Ree6-SQL', '2024-11-11 12:37:03', 901, 1),
(8, '8', 'Fix Recording', 'SQL', 'V8__Fix_Recording.sql', 111776244, 'Ree6-SQL', '2024-11-11 12:37:04', 109, 1),
(9, '9', 'Add User Cards', 'SQL', 'V9__Add_User_Cards.sql', 1026768596, 'Ree6-SQL', '2024-11-11 12:37:04', 119, 1),
(10, '10', 'Add Spotify Notifications', 'SQL', 'V10__Add_Spotify_Notifications.sql', 1904001082, 'Ree6-SQL', '2024-11-11 12:37:05', 98, 1),
(11, '11', 'Indexs', 'SQL', 'V11__Indexs.sql', 1265533884, 'Ree6-SQL', '2024-11-11 12:37:06', 669, 1);

CREATE TABLE `Giveaway` (
  `messageId` bigint(20) NOT NULL,
  `creatorId` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channelId` bigint(20) NOT NULL,
  `prize` varchar(255) DEFAULT NULL,
  `winners` bigint(20) NOT NULL,
  `created` datetime DEFAULT NULL,
  `ending` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `GuildStats` (
  `id` int(11) NOT NULL,
  `gid` bigint(20) DEFAULT NULL,
  `command` varchar(255) DEFAULT NULL,
  `uses` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `InstagramNotify` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Invites` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) DEFAULT NULL,
  `uses` bigint(20) DEFAULT NULL,
  `code` varchar(255) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Level` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) NOT NULL,
  `xp` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `LogWebhooks` (
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `cid` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Money_Holder` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) NOT NULL,
  `cash` double DEFAULT NULL,
  `bank` double DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Money_Transaction` (
  `transactionId` bigint(20) NOT NULL,
  `isSystemPayment` bit(1) NOT NULL,
  `guildId` bigint(20) DEFAULT NULL,
  `isReceiverBank` bit(1) NOT NULL,
  `isSenderBank` bit(1) NOT NULL,
  `amount` double DEFAULT NULL,
  `creation` datetime DEFAULT NULL,
  `receiver_guildId` bigint(20) NOT NULL,
  `receiver_userId` bigint(20) NOT NULL,
  `sender_guildId` bigint(20) NOT NULL,
  `sender_userId` bigint(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Opt_out` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Punishments` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `warnings` int(11) NOT NULL,
  `action` int(11) NOT NULL,
  `roleId` bigint(20) NOT NULL,
  `timeoutTime` bigint(20) NOT NULL,
  `reason` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `ReactionRole` (
  `guildId` bigint(20) NOT NULL,
  `emoteId` bigint(20) DEFAULT NULL,
  `formattedEmote` varchar(255) DEFAULT NULL,
  `channelId` bigint(20) DEFAULT NULL,
  `roleId` bigint(20) NOT NULL,
  `messageId` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Recording` (
  `id` varchar(255) NOT NULL,
  `guildId` bigint(20) DEFAULT NULL,
  `channelId` bigint(20) DEFAULT NULL,
  `creator` bigint(20) DEFAULT NULL,
  `participants` varbinary(32600) DEFAULT NULL,
  `created` bigint(20) DEFAULT NULL,
  `recording` longblob DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `RedditNotify` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `subreddit` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `RSSFeed` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `url` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `ScheduledMessage` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `message` varchar(255) DEFAULT NULL,
  `delay` bigint(20) DEFAULT NULL,
  `shouldRepeat` bit(1) DEFAULT NULL,
  `webhook_id` bigint(20) NOT NULL,
  `lastExecute` datetime DEFAULT NULL,
  `lastUpdated` datetime DEFAULT NULL,
  `created` datetime DEFAULT NULL,
  `webhook_guildId` bigint(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `ScheduledMessageWebhooks` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Settings` (
  `guildId` bigint(20) NOT NULL,
  `name` varchar(255) NOT NULL,
  `displayname` varchar(255) DEFAULT NULL,
  `value` text DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `SpotifyNotify` (
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `entityId` varchar(255) DEFAULT NULL,
  `typ` int(11) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL,
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Statistics` (
  `id` int(11) NOT NULL,
  `day` int(11) DEFAULT NULL,
  `month` int(11) DEFAULT NULL,
  `year` int(11) DEFAULT NULL,
  `stats` varbinary(32600) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `StreamActions` (
  `guildId` bigint(20) NOT NULL,
  `name` varchar(255) NOT NULL,
  `auth_id` varchar(255) NOT NULL,
  `listener` int(11) DEFAULT NULL,
  `argument` varchar(255) DEFAULT NULL,
  `actions` varbinary(32600) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Suggestions` (
  `guildId` bigint(20) NOT NULL,
  `channelId` bigint(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `TemporalVoicechannel` (
  `guildId` bigint(20) NOT NULL,
  `channelId` bigint(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Tickets` (
  `guildId` bigint(20) NOT NULL,
  `channelId` bigint(20) DEFAULT NULL,
  `ticketCategory` bigint(20) DEFAULT NULL,
  `logChannelId` bigint(20) DEFAULT NULL,
  `logChannelWebhookId` bigint(20) DEFAULT NULL,
  `logChannelWebhookToken` varchar(255) DEFAULT NULL,
  `ticketCount` bigint(20) DEFAULT 0
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `TikTokNotify` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `TwitchIntegration` (
  `channel_id` varchar(255) NOT NULL,
  `user_id` bigint(20) DEFAULT NULL,
  `token` varchar(255) DEFAULT NULL,
  `refresh` varchar(255) DEFAULT NULL,
  `channel_name` varchar(255) DEFAULT NULL,
  `expires` int(11) DEFAULT NULL,
  `lastUpdated` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `TwitchNotify` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `TwitterNotify` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `UserRankCard` (
  `userId` bigint(20) NOT NULL,
  `rankCard` longblob DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `VCLevel` (
  `guildId` bigint(20) NOT NULL,
  `userId` bigint(20) NOT NULL,
  `xp` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `VCLevelAutoRoles` (
  `guildId` bigint(20) NOT NULL,
  `roleId` bigint(20) NOT NULL,
  `lvl` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `Warning` (
  `userId` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `warnings` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `WelcomeWebhooks` (
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `cid` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;

CREATE TABLE `YouTubeNotify` (
  `id` bigint(20) NOT NULL,
  `guildId` bigint(20) NOT NULL,
  `channel` bigint(20) NOT NULL,
  `webhookId` bigint(20) NOT NULL,
  `token` varchar(255) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_uca1400_ai_ci;


ALTER TABLE `AutoRoles`
  ADD PRIMARY KEY (`guildId`,`roleId`);

ALTER TABLE `BirthdayWish`
  ADD PRIMARY KEY (`id`),
  ADD KEY `idx_19996e465c82202aa18a5f903` (`userId`,`guildId`);

ALTER TABLE `ChannelStats`
  ADD PRIMARY KEY (`guildId`);

ALTER TABLE `ChatLevelAutoRoles`
  ADD PRIMARY KEY (`guildId`,`roleId`);

ALTER TABLE `ChatProtector`
  ADD PRIMARY KEY (`guildId`,`name`);

ALTER TABLE `CommandStats`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `CustomCommands`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `CustomEvents`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `flyway_schema_history`
  ADD PRIMARY KEY (`installed_rank`),
  ADD KEY `flyway_schema_history_s_idx` (`success`);

ALTER TABLE `Giveaway`
  ADD PRIMARY KEY (`messageId`),
  ADD KEY `idx_4eabfb36fcb96d367535a664f` (`guildId`);

ALTER TABLE `GuildStats`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `InstagramNotify`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `Invites`
  ADD PRIMARY KEY (`guildId`,`code`),
  ADD KEY `idx_61180fdd5c7e050bdf1afda91` (`code`,`guildId`);

ALTER TABLE `Level`
  ADD PRIMARY KEY (`guildId`,`userId`),
  ADD KEY `idx_8e431ff002adb1348ebe09932` (`userId`,`guildId`);

ALTER TABLE `LogWebhooks`
  ADD PRIMARY KEY (`guildId`);

ALTER TABLE `Money_Holder`
  ADD PRIMARY KEY (`guildId`,`userId`),
  ADD KEY `idx_b161be6fddaf84985162c1fe3` (`userId`,`guildId`);

ALTER TABLE `Money_Transaction`
  ADD PRIMARY KEY (`transactionId`),
  ADD KEY `FK_MONEY_TRANSACTION_RECEIVER` (`receiver_guildId`,`receiver_userId`),
  ADD KEY `FK_MONEY_TRANSACTION_SENDER` (`sender_guildId`,`sender_userId`);

ALTER TABLE `Opt_out`
  ADD PRIMARY KEY (`guildId`,`userId`),
  ADD KEY `idx_8378fc7abe05674fc6c8ea8f6` (`userId`,`guildId`);

ALTER TABLE `Punishments`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `ReactionRole`
  ADD PRIMARY KEY (`guildId`,`roleId`),
  ADD KEY `idx_7fff13a15f26ab2c95acfc2c4` (`roleId`,`guildId`);

ALTER TABLE `Recording`
  ADD PRIMARY KEY (`id`),
  ADD KEY `idx_9a30f1a12245ef1f86755cf17` (`id`,`guildId`);

ALTER TABLE `RedditNotify`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `RSSFeed`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `ScheduledMessage`
  ADD PRIMARY KEY (`id`,`guildId`),
  ADD KEY `FK_SCHEDULED_MESSAGE_WEBHOOK` (`webhook_id`,`webhook_guildId`);

ALTER TABLE `ScheduledMessageWebhooks`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `Settings`
  ADD PRIMARY KEY (`guildId`,`name`),
  ADD KEY `idx_de5259bea32e95dcc26373fcd` (`name`,`guildId`);

ALTER TABLE `SpotifyNotify`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `Statistics`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `StreamActions`
  ADD PRIMARY KEY (`guildId`,`name`),
  ADD KEY `FK_STREAMACTIONS_ON_AUTH` (`auth_id`),
  ADD KEY `idx_f3d1609a03578e84862863eef` (`name`,`guildId`);

ALTER TABLE `Suggestions`
  ADD PRIMARY KEY (`guildId`,`channelId`),
  ADD KEY `idx_0df616b5cc4427eb5e3294360` (`channelId`,`guildId`);

ALTER TABLE `TemporalVoicechannel`
  ADD PRIMARY KEY (`guildId`,`channelId`),
  ADD KEY `idx_a384068c6a22b1afe3da2a233` (`channelId`,`guildId`);

ALTER TABLE `Tickets`
  ADD PRIMARY KEY (`guildId`),
  ADD KEY `idx_df865b7031c2af9280b22aaea` (`channelId`,`guildId`);

ALTER TABLE `TikTokNotify`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `TwitchIntegration`
  ADD PRIMARY KEY (`channel_id`);

ALTER TABLE `TwitchNotify`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `TwitterNotify`
  ADD PRIMARY KEY (`id`,`guildId`);

ALTER TABLE `UserRankCard`
  ADD PRIMARY KEY (`userId`);

ALTER TABLE `VCLevel`
  ADD PRIMARY KEY (`guildId`,`userId`),
  ADD KEY `idx_0b656a7171f415c0665378c5e` (`userId`,`guildId`);

ALTER TABLE `VCLevelAutoRoles`
  ADD PRIMARY KEY (`guildId`,`roleId`);

ALTER TABLE `Warning`
  ADD PRIMARY KEY (`guildId`,`userId`),
  ADD KEY `idx_7a4d8ddfcefc5ec5753a77e0a` (`userId`,`guildId`);

ALTER TABLE `WelcomeWebhooks`
  ADD PRIMARY KEY (`guildId`);

ALTER TABLE `YouTubeNotify`
  ADD PRIMARY KEY (`id`,`guildId`);


ALTER TABLE `BirthdayWish`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

ALTER TABLE `CommandStats`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

ALTER TABLE `CustomCommands`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `CustomEvents`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `GuildStats`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

ALTER TABLE `InstagramNotify`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `Money_Transaction`
  MODIFY `transactionId` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `Punishments`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `RedditNotify`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `RSSFeed`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `ScheduledMessage`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `ScheduledMessageWebhooks`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `Statistics`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

ALTER TABLE `TikTokNotify`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `TwitchNotify`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `TwitterNotify`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;

ALTER TABLE `YouTubeNotify`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT;


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
