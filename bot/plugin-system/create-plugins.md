# Create Plugins

## Requirements

* Java 17
* Basic knowledge of programming with Java

## Import Library

{% tabs %}
{% tab title="Maven" %}
```xml
<repository>
   <id>jitpack.io</id>
   <url>https://jitpack.io</url>
</repository>

<dependency>
   <groupId>de.ree6</groupId>
   <artifactId>Ree6</artifactId>
   <version>VERSION</version>
</dependency>
```
{% endtab %}

{% tab title="Gradle" %}
<pre class="language-gradle"><code class="lang-gradle">dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
<strong>    repositories {
</strong>        mavenCentral()
        maven { url 'https://jitpack.io' }
    }
}

dependences {
    implementation 'de.ree6:Ree6:VERSION'
    annotationProcessor(compileOnly("org.pf4j:pf4j:3.13.0"))
}
</code></pre>
{% endtab %}
{% endtabs %}

## Let's get started!

To create a plugin you will need to first make a class that we will use as our "Main Class".\
This class needs to extend the class called `ReePlugin`.

Here is an example of how your main class might look!

```java
public class MyAwesomePlugin extends ReePlugin {

    public MyAwesomePlugin(ReePluginContext context) {
        super(context);
    }
}
```

After extending the `ReePlugin` class, we can go and implement all the new methods we have!\
To be exact we have 3 new methods, the first one will be `start` then comes `stop` and at the end, we have `delete`.

***

### Start Method

This method will be called when the plugin is being run by Ree6 and everything is successfully loaded.

### Stop Method

This one will be called when you stop the plugin this includes situations where you delete or unload it via the Plugin Manager.

### Delete Method

This will only be called when the Plugin Manager is asked to delete the given plugin, so you have a chance to give a goodbye message or something.

***

Once you implement the methods you want to use it should look something like this!

```java
public class MyAwesomePlugin extends ReePlugin {

    public MyAwesomePlugin(ReePluginContext context) {
        super(context);
    }

    @Override
    public void start() {
        super.start();
        context.getLogger().info("Start!");
    }

    @Override
    public void stop() {
        super.stop();
        context.getLogger().info("Stop!");
    }

    @Override
    public void delete() {
        super.delete();
        context.getLogger().info("You want to delete me :C ?");
    }
}
```

## Creating a command!

To create a command we need to first understand the concept behind the Ree6 Command System.\
We have a `CommandManager` which is handling all the internal works like command parameter parsing and more!\
For a command, we need to create a class that implements the `ICommand` class and has the `Command` Annunciation.

Let's make a command together called `PongCommand`:

```java
@Extension
@Command(name = "pong", description = "Answer with Pong!", category = Category.FUN)
public class PongCommand implements ICommand {

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
I will give you a `CommandEvent` parameter which will contain information like:

* Has this Command been executed as SlashCommand?
* Who executed this Command?
* In which Guild has this Command been executed?

Now, let's continue with our work!\
Since we want the Bot to respond with `Pong!` when someone writes `/ping` or `ree!ping`\
We need to go into the `onPerform` method and respond to it!\
For this, we can use the internal reply method, just like this!

```java
@Override
public void onPerform(CommandEvent commandEvent) {
    commandEvent.reply("Pong!");
}
```

## Register the command.

Well now that we finished our great `PongCommand` we will need to register it!

### Automatic

Commands have to be marked with `@Extension`  annotation to be automatically registered.

### Manual

You can easily call the `CommandManager.addCommand` method via the Ree6 Main class for the manual registration.

Example:

```java
Main.getInstance().getCommandManager().addCommand(new PongCommand());
```



Unlike the old Addon system, we don't need to manually register it!\
The new plugin system will automatically detect that the plugin has a few classes that implement the interface and register them!

## The missing plugin.yml

To let Ree6 know where to look you will need to create a `plugin.yml`!\
In this, you will need to add the name of the plugin, the author's name, the path to the main class, the version of the plugin, and the version of Ree6 it has been made for!\
For example, a correct `plugin.yml` would look like this:

<pre class="language-yaml"><code class="lang-yaml">id: Pong Command
description: Very cool pong command!
version: 1.0.0
<strong>requires: 4.0.0
</strong>provider: Presti
class: de.presti.cooladdon.MyAwesomePlugin
license: MIT
dependencies: []
</code></pre>

## Finishing up!

You should be ready to go with your plugin!\
Now you will need to export it either via Maven, Gradle, or any desired way you have!

On how to load the plugins refer to [installing-plugins.md](installing-plugins.md "mention")
