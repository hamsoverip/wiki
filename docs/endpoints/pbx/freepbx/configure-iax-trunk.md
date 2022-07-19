# Configuring a FreePBX IAX Trunk for HOIP

The Ham's Over IP service offers the ability to connect your home FreePBX PBX System to our system. This allows you to use any number of phones on your extension, control your own voicemail and many other things. In many ways, it's easier to run your own PBX then it is to try to connect multiple phones to our system. The more people who can use a their own PBX is the less number of phones trying to register to our network and helps keep resources free. 

It does take a bit of work to get your own PBX configured and setup, but it in the end, the rewards are nice.

This guide assumes that you already have a FreePBX setup and ready. There are many other guides on the Internet explaining how to do this, so that is outside the scope of this document.

## Configuring the Trunk

### Create the Trunk

* Log into your PBX admin screen
* Click ```Conectivity``` and then ```Trunks```
* Click ```Add Trunk``` on the next screen.
* You should now be in the ```Edit Trunk``` screen. Fill in the fields as such:
    * ```Trunk Name``` - Name of the Trunk. Suggested: HOIP
    * ```Hide CallerID``` - Make sure this is set to ```No```.
    * ```Outbound CallerID``` - Your actual extension. This would be the extension for the Trunk that was sent to you in the email.
    * ```CID Options``` - Make sure this is set for ```Allow Any CID```.
    * ```Disable Trunk``` - Make sure this is set for ```No```.
    * Leave the Defaults for everything else.
* Next Click the ```Iax Settings``` tab.
* On that screen edit the following:
    * On the ```Outgoing``` Tab:
        * ```Name``` - Suggested HOIP
        * ```Peer Details``` - This is where you will set all the login and peer details. You will need to include the following:
            ```bash 
            username=< Your Extension >
            type=friend
            secret=< Your Password >
            requirecalltoken=no
            host=< the domain of the pbx server in your email >
            ```
        * ```Username``` - This is the extension of your trunk line from the email
        * ```secret``` - This is the password of our trunk line from the email.
        * ```host``` - this is the domain of the PBX server from your email. ex. ```pbx-us1.hamsoverip.com```

    * Once that is filled out go to the Incoming tab and fill out the following:
        * ```User Context``` - This should be ```from-<your extension>``` where < your extension > is the extension of your trunk line from the email.
        * Under ```User Details``` use the following. Just opy and paste this. There is nothing else to configure in the ```User Details``` section.
            ```bash
            type=friend
            qualify=yes
            forceencryption=no
            disallow=all
            context=from-pstn
            canreinvite=no
            allow=ulaw
            ```
        * ```Register String``` - should be something like the following:
        ```bash
        yourextension:password@domain
        ```
        Example: ```1234:fgn*%^2fb&bfk5437H@pbx-us1.hamsoverip.com```
    * Click ```Submit``` and then ```Apply Changes``` at the top right.

### Create Outbound Route

Once you have the trunk created, you will need to configure an Outgoing Route in order to make outgoing calls on your trunk.

* Click ```Conectivity``` and then ```Outbound Routes```
* Click ```Add Route```.
* You should now be in the ```Edit Route``` Screen. You will need to fill in the fields as follows:
    * ```Route Name``` - This is the name you want to call your outgoing route. Suggested: HOIP
    * Skip down to ```Trunk Sequence for Matched Routes``` and select the ```HOIP Trunk``` you created earlier.
* Click ```Submit``` and then Click the red ```Apply Changes``` in the upper right corner of the screen.

As long as this is the only route/trunk on your PBX system, you are good to move on. Otherwise, if this is not the only trunk on your system, you may want to setup a prefix to dial to get this trunk. (Very Similiar to the old "Dial 9 to get an outside line" thing back in the day.)

If you want to set this up, click the ```Dial Patterns``` tab and then add a number for the prefix to dial, usually a single digit, in the prefix field for one of the dial patterns. Then add a ```.``` in the ```match pattern``` field next to it. Then ```Submit``` and ```Apply Changes```.

Now to select that line, all you need to do is dial the prefix and then the number you want to call. Otherwise, if you do not set this up, all you will need to do is dial the HOIP number you want to call.

### Create Inbound Route

Now you will need to create an Inbound Route in order to receive calls on your phone. In order to do this:

* Click ```Conectivity``` and then ```Inbound Routes```
* Click ```Add Route```.
* You should now be in the ```Edit Route``` Screen. You will need to fill in the fields as follows:
    * ```Description``` - This is the name of the Route. Suggested - HOIP
    * ```Set Destination``` - This is where you want the incoming call to go to. This can be set to anywhere you want to send the call, for example, a specific extension, a ring group, a specific voicemail box, an IVR or even to a Time Condition.
* Click ```Submit``` and then Click the red ```Apply Changes``` in the upper right corner of the screen.

You should now be able to make and receive calls across your HOIP Trunk.

Last Updated: 07/18/2022