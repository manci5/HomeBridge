# HomeBridge
Java made application for setting up virtual HomeKit accessories to be able to control them like any real HomeKit device.

Currently it can only perform a command line such as:

>Say "Turn on my bedroom radio" to Siri

>  HomeBridge executes this line (Mac): "open -a iTunes"

You can make an applescript or a windows batch file and then have HomeBridge run that for you:

>Say "Turn off computer"

>  HomeBridge executes this line (Windows): "C:/mybats/turnoff.bat"

# Raspberry Pi

Instead of just running some programs, you can make your own Java program that will take arguments and do something with them. For example, you can make a Java app called "Bulby.jar" which will use gpio commands such as "gpio pwm <pin> <value>" to adjust the brightness of an LED pin.

To pass arguments to your Bulby app, you need to use #BRIGHTNESS# in your command line when creating the accessory, like this:
![alt tag](http://i.imgur.com/osurTZ6.png)
