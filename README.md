# HomeBridge

HomeBridge is a Java app which allows you to create virtual HomeKit accessories that you can pair with your iPhone or iPad and use them to execute CommandPrompt/Terminal commands. Currently supported accessories are Switch, Lightbulb and Thermostat. When adding a new accessory, you specify command for each event (like turn on event, or changing brightness event).

>Say "Turn on my bedroom radio" to Siri

>  HomeBridge executes this (terminal) line: "open -a iTunes"

You can make an applescript or a windows batch file and then have HomeBridge run that for you:

>Say "Turn off computer"

>  HomeBridge executes this (Command prompt) line: "C:/mybats/turnoff.bat"

# Raspberry Pi

Instead of just running some programs, you can make your own Java program that will take arguments and do something with them. For example, you can make a Java app called "Bulby.jar" which will use gpio commands such as "gpio pwm pin value" to adjust the brightness of an LED pin.

For example,when creating a new accessory and setting the command which will be executed when user changes brightness, you type this:

![alt tag](http://i.imgur.com/ci4NLNh.png)

# Updating HomeBridge

When
