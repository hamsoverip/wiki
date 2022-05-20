# Configure Busy Light Function (BLF) on Cisco Phones

The Busy Light Function (BLF) is a function of Asterisk and some phones that allows the end user to program a speedial button on their phone to light based on the status of the line that the speeddial is set to connect to. If the line is busy, in other words, someone is using the line, it will glow red, otherwise it will glow green. This works for normal extensions and conference bridges as well as the RF-Links Extensions. If someone is dialed into a conference, the light will be red, indicating someone is in the conference, otherwise it will glow green.

This Guide describes how to configure the feature on Cisco Phones and Cisco Sidecars. Other phones will probably have a different function string to make this work.

In order to do this, you will need to access the Web Configuration of the phone. How this is done varies from phone model to phone model, but for most, if you open a web browser and go to the IP address of the phone, you should be able to access the Web Configuration Interface.

From there, you will need to navigate to the extension you want to edit, be it a button on the phone or on the sidecar.

When you are at the extension you want to edit, you will need to look for the ```Extended Function``` Field for that line and in that you will place something similiar to the following:

```bash
fnc=sd+blf;ext=<extension to Monitor>@$PROXY;nme=<Friendly Name>;
```

Where:

* ```fnc=sd+blf;``` - This sets the function of the button for both a speedial and BLF for that button
* ```ext=<extension to monitor>@$PROXY;``` - This is the extension you want to Speedial/monitor. ```$PROXY``` is a variable that is taken from another part of the phone configuration. Leave that alone. That just basically sets the server.
* ```name=<Friendly Name>;``` This sets the name of the button that is displayed on the phone screen or the sidecar screen (if it has one). If you are using a sidecar without a screen, this can be omitted for that.
* ***OPTIONAL:*** if you are using a sidecar, you can add ```vid=N``` where N is the number of the line you want to send the call out. In other words, let's say you have a Home VOIP number on line 1 and HOIP on line 2 and you want this button to speedial an extension on HOIP, you would set it to look like ```vid=2```. Otherwise it will default to line 1 of the phone.

So an example function string would be:

```bash
fnc=sd+blf;ext=1234@$PROXY;nme=Joe, WA1ABC;vid=2
```

