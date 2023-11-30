---
description: >-
  StreamTools is a collection of features in Ree6 which aim to help out Content
  Creators!
---

# StreamTools

## Stream Actions

This is a feature that allows users to make Ree6 to something based on Twitch Redemptions, Twitch Subs and Twitch Follows.

These are all the Actions that Ree6 can do:

| Name               | Id          |
| ------------------ | ----------- |
| Join Voicechannel  | voice-join  |
| Leave Voicechannel | voice-leave |
| Play TTS           | play-tts    |
| Play URL           | play-url    |
| Play Blerp         | play-blerp  |
| Say message        | say         |

## Requirements

Before we start with anything lets talk about the requirements for this!\
You will first need to link you Twitch Account with Ree6.\
You can do this by going onto [cp.ree6.de/external/twitch](https://cp.ree6.de/external/twitch)!\


## Commands

## Create

With this Command we can create Stream-Actions:

```
/stream-action create
```

When creating a Stream-Action we have to give it a Name.\
We will need that Name to manage it.\


### Example

```
/stream-action create name:MyAction
```

## Delete

As simple as it sounds, this Command deletes a Stream-Action.

```
/stream-action delete
```

When wanting to delete a Stream-Action we also have to enter a Name.\


### Example

```
/stream-action delete name:MyAction
```

## Points

With this you can see every Redemption Ree6 has access to on your Twitch Channel.\
It will give a list that looks similiar to this one:

```
ID - NAME
```

## Manage

This Command allows you to manage your Stream-Actions.\
Before being able to use any of these you will need to already have a Stream-Action.\
For that check out this: [#create](streamtools.md#create "mention")!\


```
/stream-action manage
```

The Manage command has 4 different subcommands, lets talk about them!

### Create

The first subcommand is the create Command, it allows you to create Actions in the Stream-Action.\


```
/stream-action manage create
```

#### Example

Lets create a Action that lets Ree6 join a Voicechannel.\
For that we will use a Stream-Action we previously created called `TTS`!\


```
/stream-action manage create name:TTS action:voice-join VOICEID
```

And the `VOICEID` will be the channel ID of the Voicechannel!\


### Delete

The second subcommand is the delete Command, it allows us to delete specific Actions in a Stream-Action.\


```
/stream-action manage delete
```

#### Example

Lets delete the first Action in the Stream-Action.\
For that we will use a Stream-Action we previously created called `TTS`!\


```
/stream-action manage delete name:TTS line:1
```

### List

The third subcommand is the list command, it allows us to list every Action in a Stream-Action.\


```
/stream-action manage list
```

#### Example

Lets list all the Actions in a Stream-Action.\
For that we will use a Stream-Action we previously created called `TTS`!\


```
/stream-action manage list name:TTS
```

You will receive a message that looks like this:\


```
ActionName -> ActionParameter
```

### Listener

The fourth subcommand is the listener command, it allows us to let the Stream-Action listen to something.\


```
/stream-action manage listener
```

#### Example

Lets let the Stream-Action listen to a Redemption.\
For that we will use a Stream-Action we previously created called `TTS`!\


```
/stream-action manage listener name:TTS listener:redemption REDEMPTIONID
```

And the `REDEMPTIONID` will be the redemption ID that you found with the [points command](https://github.com/Ree6-Applications/Ree6/wiki/StreamTools#points)!\


***

## Example

Lets say you want to create a Stream-Action which plays a TTS Messages based on the Users Input.\


### Create

We first need to create a new Stream-Action likes this:

```
/stream-action create name:TTS
```

The name in this case is `TTS` keep that in mind since we will need the Action name to manage it.

### Manage

After that we will need to tell the Stream-Actions what to do!\
To be exact, we gotta tell it to join a Voicechannel and play a TTS Mesage.\
That would look like this:

```
/stream-action manage create name:TTS action:voice-join VOICEID
/stream-action manage create name:TTS action:play-tts %user_input%
```

In this case the `%user_input%` will take the message input of the user in a redemption.\
And the `VOICEID` will be the channel ID of the Voicechannel!\


### Listen

And at last we need to tell the Stream-Action to listen to a specific Redemption!\
For that we need the `REDEMPTIONID` we can get that one by running the [#points](streamtools.md#points "mention") command!\
Once you have the right ID we execute this command:

```
/stream-action manage listen name:TTS listen:redemption REDEMPTIONID
```
