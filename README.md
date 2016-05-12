# HomeBridge

![alt tag](http://i.imgur.com/6aprujn.png)

HomeBridge is a Java app which allows you to create virtual HomeKit accessories that you can pair with your iPhone or iPad and use them to execute CommandPrompt/Terminal commands. Currently supported accessories are Switch, Lightbulb and Thermostat. When adding a new accessory, you specify command for each event (like turn on event, or changing brightness event).

>Say "Turn on my bedroom radio" to Siri

>  HomeBridge executes this (terminal) line: "open -a iTunes"

You can make an applescript or a windows batch file and then have HomeBridge run that for you:

>Say "Turn off computer"

>  HomeBridge executes this (Command prompt) line: "C:/mybats/turnoff.bat"

# Raspberry Pi

Instead of just running some programs, you can make your own Java program that will take arguments and do something with them. For example, you can make a Java app called "Bulby.jar" which will execute gpio commands such as "gpio pwm pin value" to adjust the brightness of an LED pin.

To do so, click "New Accessory", enter new accessory name and type, and then for the brighness command enter this:

![alt tag](http://i.imgur.com/ci4NLNh.png)

For a thermostat, use #TEMPERATURE# instead of #BRIGHTNESS#.

# Reporting back

So you use Bulby.jar to set the brighntess of the LED on your Raspberry Pi. But you will also need to make another Java app that will run in the background and watch the power state of that LED (and maybe even change it sometimes). When power state changes, you will need to have your background app report that to HomeBridge and Siri. To do so, simply execute a Terminal/CommandPrompt command like this to let HomeBridge (and Siri) know what changed.

>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 123423 temperature 24 (thermostat)

>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 789778 on (switch or lightbulb)

>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 789778 off (switch or lightbulb)

>java -jar /Applications/HomeBridge.app/Contents/HomeUpdater.jar update 789778 brightness 90 (lightbulb)

The number after "update" is the ID of the accessory. For Mac, the location of HomeUpdater.jar is inside HomeBridge.app/Contents.



