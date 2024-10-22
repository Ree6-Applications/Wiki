# Make your first Addon

## Requirements

Developing with the Ree6 Addon API requires Java 17.\
We recommend using Maven or Gradle to import Ree6 as a Library file into your project.

Example for Maven:

```xml
...
<repository>
   <id>jitpack.io</id>
   <url>https://jitpack.io</url>
</repository>

...

<dependency>
   <groupId>de.ree6</groupId>
   <artifactId>Ree6</artifactId>
   <version>VERSION</version>
</dependency>
...
```

## Lets get started!

When working with the Ree6 Addon API you need to create a Main class of your Addon which implements our `AddonInterface` class!

In this example we call the class AddonMain:

```java
public class AddonMain implements AddonInterface {
}
```

After implementing the AddonInterface you should start with the onEnable and onDisable Methods!

```java
    @Override
    public void onEnable() {
        System.out.println("Start!");
    }

    @Override
    public void onDisable() {
        System.out.println("Goodybye!");
    }
```

## Creating a command!

To create a command we need to first understand the concept behind the Ree6 Command System.\
We have a `CommandManager` which is handling all the internal works like command parameter parsing and more!\
For a command we need to create a class implements the `ICommand` class and having the `Command` Annonciation.

Lets make a command together called `PongCommand`:

```java
@Command(name = "ping", description = "Answer with Pong!", category = Category.FUN)
public class PongCommand extends ICommand {

    @Override
    public void onPerform(CommandEvent commandEvent) {
    }

    @Override
    public CommandData getCommandData() {
        return null;
    }

    @Override
    public String[] getAlias() {
        return new String[0];
    }
}
```

When creating the commands you will need to implement these 3 methods to work with them.\
The `onPerform` method is where you are going to do most of the stuff.\
I will give you a `CommandEvent` as parameter which will contain informations like:\


* Has this Command been executed as SlashCommand?
* Who executed this Command?
* In which Guild has this Command been executed?

Now, lets continue with our work!\
Since we want the Bot to respond with `Pong!` when someone writes `/ping` or `ree!ping`\
We need to go into the `onPerform` method and respond to it!\
For this we can use the internal reply method.\
Just like this:

```java
@Override
public void onPerform(CommandEvent commandEvent) {
    commandEvent.reply("Pong!");
}
```

## Register the command.

Well now that we finished our great `PongCommand` we will need to register it!\


How do we do that?\
Simple, we go into our Main class into the `onEnable` method and tell the `CommandManager` to add it into the system!

It would look like this:

```java
@Override
public void onEnable() {
    System.out.println("Start!");
    Main.getInstance().getCommandManager().addCommand(new PongCommand());
}
```

But we shouldn't forget to also remove the Command once the Addon shutsdown!\
You can do this like this:

```java
@Override
public void onDisable() {
    System.out.println("Goodybye!");
    Main.getInstance().getCommandManager().removeCommand(new PongCommand());
}
```

## The missing Addon.yml

To let Ree6 now where to look you will need to create a `Addon.yml`!\
In this you will need to add the name of the Addon, the Author name, the path to the main class, the version of the addon, the version of Ree6 it has been made for!\
For example addon it would looks like this:

```yaml
name: Pong Command
version: 1.0
api-version: 2.4.11
author: Presti
main: de.presti.pongcommand.AddonMain
```

## Finishing up!

You should be ready to go with your Addon!\
Now you will need to export it either via Maven, Gradle or any desired way you have!

After exporting it you just need to put it into the `addons` folder of Ree6!\
You can either restart Ree6 to load the addon or use the `/addon load NAME` to load it!
