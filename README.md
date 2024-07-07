# Ascord
Ascord is a powerful discord bot framework written completely in ASPL.
<br>This library was one of the very first projects written in the language.

> [!IMPORTANT]  
> Ascord is WIP and should not be used in production at the time, as not all features are implemented and the gateway connection is not 100% stable yet.

## Example usage
```aspl
import ascord
import ascord.message
import io

var bot = new Bot()
bot.onReady = callback(){
    print("Starting up...")
    bot.setStatus("Hello ASPL 🧑‍💻")
}
bot.commandPrefix = "!"
bot.onMessage = callback(Message message){
    print("Message from " + message.sender.name + "#" + message.sender.discriminator + ": " + message.content)
}
bot.onCommand = callback(CommandMessage command){
    print("Command from " + command.sender.name + "#" + command.sender.discriminator + ": " + command.content)
    if(command.command == "ping"){
        bot.postMessage("Pong! 🏓", command.channel)
    }elseif(command.command == "say"){
        bot.postMessage(command.args.join(" "), command.channel)
    }elseif(command.command == "status"){
        bot.setStatus(command.args.join(" "))
    }elseif(command.command == "shutdown"){
        print("Shutting down...")
        bot.postMessage("Shutting down...", command.channel)
        exit(0)
    }
}
bot.start(io.read_file("client.token"))
```

## Implemented features
Ascord does not implement the whole Discord API yet; these are the main features that are implemented, but others might already work as well:
* Message sending and receiving
* Heartbeating (not 100% reliable yet though)
* Simple command handling (either via a prefix or as slash commands)
* Embeds (only title and description)
* Setting the bot's status
* Getting a user by their id

## Documentation
A documentation will be added soon.