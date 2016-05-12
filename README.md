# HomeBridge
Java made application for setting up virtual HomeKit accessories to be able to control them like any real HomeKit device.

Currently it can only perform a command line such as:

>Say "Turn on my bedroom radio" to Siri

>  HomeBridge executes this line (Mac): "open -a iTunes"

You can make an applescript or a windows batch file and then have HomeBridge run that for you:

>Say "Turn off computer"

>  HomeBridge executes this line (Windows): "C:/mybats/turnoff.bat"

You can even make a Java app which will then take arguments like #BRIGHTNESS# or #TEMPERATURE#

>Say "Set temperature in living room to 25 degrees"

>  HomeBridge executes: "java -jar /Applications/thermostat.jar updatetemperature #TEMPERATURE#"
