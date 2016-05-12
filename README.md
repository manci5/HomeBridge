# HomeBridge

![alt tag](http://i.imgur.com/6aprujn.png)

HomeBridge is a Java app which allows you to create virtual HomeKit accessories that you can pair with your iPhone or iPad and use them to execute CommandPrompt/Terminal commands. Currently supported accessories are Switch, Lightbulb and Thermostat. When adding a new accessory, you specify command for each event (like turn on event, or changing brightness event).

>Say "Turn on my bedroom radio" to Siri

>  HomeBridge executes this (terminal) line: "open -a iTunes"

You can make an applescript or a windows batch file and then have HomeBridge run that for you:

>Say "Turn off computer"

>  HomeBridge executes this (Command prompt) line: "C:/mybats/turnoff.bat"

# Raspberry Pi

Instead of just running some programs, you can make your own Java program that will take arguments and do something with them. For example, you can make a Java app called "Bulby.jar" which will execute gpio commands on Raspberry Pi such as "gpio pwm pin value" to adjust the brightness of an LED pin.

To do so, click "New Accessory", enter new accessory name and type, and then for the brighness command enter this:

![alt tag](http://i.imgur.com/ci4NLNh.png)

For a thermostat, use #TEMPERATURE# instead of #BRIGHTNESS#. This is of course just an example. You could make Bulby accept just the number (without "-updateTemperature" argument before), if it always deals with just brightness.

# Reporting back

So you use Bulby.jar to set the brighntess of the LED on your Raspberry Pi... But you will also need to make another Java app that will run in the background and watch the power state of that LED (and maybe even change it sometimes). When power state changes, you will need to have your background app report that to HomeBridge and Siri. To do so, simply execute a Terminal/CommandPrompt command like this to let HomeBridge (and Siri) know what changed.

Thermostat:
>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 123423 temperature 24 
Switch:
>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 789778 on
>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 789778 off
Lightbulb:
>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 789778 brightness 90
>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 789778 on
>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 789778 off

The number after "update" is the ID of the accessory. For Mac, the location of HomeUpdater.jar is inside HomeBridge.app/Contents.

Notice: I don't know how to send arguments to an app that is already running. For me Bulby.jar would be just a simple app which takes the arguments such as "update temperature 25", does the work with it and then quits. Then I would make another app that would be running in background all the time checking on sensors and reporting back to HomeUpdater when needed.


