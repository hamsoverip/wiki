# Configuring a FreePBX SIP Trunk for HOIP

!!! note "IMPORTANT NOTE"
    If you are planning to setup a SIP trunk in FreePBX, you will need to request a regular user extension. ***DO NOT*** request a trunk. This will get you setup an IAX Trunk and that will not work with this method.

----

The Hams Over IP service offers the ability to connect your home FreePBX PBX System to our system. This allows you to use any number of phones on your extension, control your own voicemail and many other things. In many ways, it's easier to run your own PBX then it is to try to connect multiple phones to our system. The more people who can use a their own PBX is the less number of phones trying to register to our network and helps keep resources free.

It does take a bit of work to get your own PBX configured and setup, but it in the end, the rewards are nice.

This guide assumes that you already have a FreePBX setup and ready. There are many other guides on the Internet explaining how to do this, so that is outside the scope of this document.

If you already have an extension on the HOIP Network, you do not need to have it converted or anything. All you would be doing is replacing your existing endpoint with FreePBX and then connecting to that your existing endpoint to your new PBX. You don't have to configure Voicemail on FreePBX if you do not want to and continue to use your existing voicemail box provided on the HOIP Network. If you want to use voicemail on your FreePBX, see the note at the end of this document on steps to take.

Why would you want to configure a SIP trunk over an IAX trunk?

Let's take a look at a couple scenarios:

* You started out as just a phone and had it connected to HOIP via SIP, but decided you wanted a little more freedom by running your own PBX.
* You want to offer some audio services or other services on the same extension as your regular phone.
* You find out how much cooler it is to run a SIP trunk vs an IAX Trunk.

There are some additonal steps to setting up a SIP trunk, but in many ways it is still easier to set up a SIP trunk versus an IAX Trunk.

## Configuring the Trunk

### Create the Trunk

* Log into your PBX admin screen
* Click `Conectivity` and then `Trunks`
* Click `Add Trunk` on the next screen and then select `Add SIP (chan_pjsip) Trunk` in the drop down.
* You should now be in the `Add Trunk` screen. Fill in the fields as such:
  * `Trunk Name` - Name of the Trunk. Suggested: HOIP
  * `Hide CallerID` - Make sure this is set to `No`.
  * `Outbound CallerID``` - Your actual extension. This would be the extension for the Trunk that was sent to you in the email.
  * `CID Options` - Make sure this is set for `Allow Any CID`.
  * `Disable Trunk` - Make sure this is set for `No`.
* Leave the Defaults for everything else.
* Next Click the `pjsip Settings` tab.
* On that screen edit the following:
  * On the `General` Tab:
    * `Username` - This is your extension number from the email.
    * `Auth username` - This is your extension number from the email.
    * `secret` - This is the password of your extension from the email.
    * `SIP Server` - this is the domain of the PBX server from your email. ex. `pbx-us1.hamsoverip.com`
    * `SIP Server Port` - This is the port of the PBX server from your email. Typically this will always be `5160`.
    * Leave all other defaults

  * Once that is filled out go to the `Advanced` tab and find the following fields:
    * `Contact User` - This will be your extension from the email.
    * `From User` - This will also be your extension from the email.

  * Click `Submit` and then `Apply Changes` at the top right.

### Create Outbound Route

Once you have the trunk created, you will need to configure an Outgoing Route in order to make outgoing calls on your trunk.

* Click `Conectivity` and then `Outbound Routes`
* Click `Add Route`.
* You should now be in the `Edit Route` Screen. You will need to fill in the fields as follows:
  * `Route Name` - This is the name you want to call your outgoing route. Suggested: HOIP
  * Skip down to `Trunk Sequence for Matched Routes` and select the `HOIP Trunk` you created earlier.
* Click ```Submit``` and then Click the red ```Apply Changes``` in the upper right corner of the screen.

As long as this is the only route/trunk on your PBX system, you are good to move on. Otherwise, if this is not the only trunk on your system, you may want to setup a prefix to dial to get this trunk. (Very Similiar to the old "Dial 9 to get an outside line" thing back in the day.)

If you want to set this up, click the `Dial Patterns` tab and then add a number for the prefix to dial, usually a single digit, in the prefix field for one of the dial patterns. Then add a `.` in the `match pattern` field next to it. Then `Submit` and `Apply Changes`.

Now to select that line, all you need to do is dial the prefix and then the number you want to call. Otherwise, if you do not set this up, all you will need to do is dial the HOIP number you want to call.

### Create Inbound Route

Now you will need to create an Inbound Route in order to receive calls on your phone. In order to do this:

* Click `Conectivity` and then `Inbound Routes`
* Click `Add Route`.
* You should now be in the `Edit Route` Screen. You will need to fill in the fields as follows:
  * `Description` - This is the name of the Route. Suggested - HOIP
  * `Set Destination` - This is where you want the incoming call to go to. This can be set to anywhere you want to send the call, for example, a specific extension, a ring group, a specific voicemail box, an IVR or even to a Time Condition.
* Click `Submit` and then Click the red `Apply Changes` in the upper right corner of the screen.

You should now be able to make and receive calls across your HOIP Trunk.

### Voicemail Options

The nice thing about FreePBX is you can have the PBX handle your voicemail, or you can have HOIP handle the voicemail.

* If you want HOIP to handle voicemail, just disable the voicemail options for the extension that incoming HOIP calls are being routed to on your FreePBX.
* If you want to handle voicemail your self, you have two additional options for this:
  * You can have your HOIP Voicemail box disabled and have everything roll to your PBX
  * You can set your pickup time on voicemail to 10 seconds on your FreePBX voicemail. This will pickup your call and send it to voicemail before HOIP. This option allows you to keep your HOIP Voicemail Box as a backup in case your PBX goes off line for some reason, allowing you to continue to get voicemails to your extension. To do this in FreePBX:
    * Click on `Settings` at the top of the screen. This should put you into the `FreePBX Advanced Settings` screen.
    * Scroll down and find the `Ringtime Default`. The default setting is 15 seconds. Set this to 10. This will allow your extension to ring for 10 seconds and then your voicemail will pick up before the HOIP one does. If your PBX goes offline, the call will roll over to the HOIP voicemail system instead.
    * Then `Submit` and `Apply Changes`.

----

!!! info "Last Updated 2024-07-09"
