# Configuring a FreePBX IAX Trunk for HOIP

The Ham's Over IP service offers the ability to connect your home 3CX PBX System to our system. This allows you to use any number of phones on your extension, control your own voicemail and many other things. In many ways, it's easier to run your own PBX then it is to try to connect multiple phones to our system. The more people who can use a their own PBX is the less number of phones trying to register to our network and helps keep resources free. 

3CX is only a SIP based PBX. Therefore, when requesting a new line for use with 3CX, you will just need to request a new extension. **DO NOT REQUEST A TRUNK.** If you request a trunk, it will be configured for an IAX connection for Asterisk/FreePBX. We do not want that.

Also, if you already have an extension on the HOIP Network, you do not need to have it converted or anything. All you would be doing is replacing your existing endpoint with 3CX and then connecting to that your existing endpoint to your new PBX. You don't have to configure Voicemail on 3CX if you do not want to and continue to use your existing voicemail box provided on the HOIP Network. If you want to use voicemail on the 3CX PBX, see the note at the end of this document on steps to take.

It does take a bit of work to get your own PBX configured and setup, but it in the end, the rewards are nice.

This guide assumes that you already have a 3CX PBX setup and ready and have also setup user extensions and voicemail boxes. There are many other guides on the Internet explaining how to do this, so that is outside the scope of this document.

## Configuring the Trunk

### Create the Trunk
* Log into your 3CX PBX Management Console.
* Click on ```SIP Trunks``` in the left hand column.
* Click ```Add SIP Trunk```.
* Select ```Generic``` in the ```Select Country``` dropdown.
* Then select ```Asterisk``` in the ```Select Provider in your Country``` dropdown.
* Enter the extension number/Username that you received in the email from the HOIP System in the ```Main Trunk No``` field. 
* Click ```Ok```. This should drop you into the edit screen for the trunk.
* Now give it a name in the ```Enter name for Trunk``` field (Suggested "HOIP")
* In the ```Registrar/Server/Gateway Hostname or IP``` field, enter the FQDN of of the PBX Server your extension is on. This will be in the email from the HOIP system. You will only need to put the FQDN in the first box. In the box at the end of that line, you will need to put the port in (5160).
    * Example FQDN: ```pbx-us1.hamsoverip.com```
* Scroll down to the ```Authentication``` section
* In the ```Type of Authentication``` drop down select ```Register/Account based```
* Put the extension (username) in the ```Authentication ID (aka SIP User ID)``` field. Again, this is from the email that you received from the HOIP System.
* Put the password from the email in the ```Authentication Password``` field.
* Leave the rest as default.
* Click ```OK``` at the top to save the settings. Wait a minute or two for the trunk to register. It should register, unless you entered something wrong. If it does not register, go back and check all your settings.

### Configure 3CX Outbound Rule

Once we have the Trunk setup and registered correctly, now we need an outbound route. This is so you can make calls out of your PBX.

* Click on ```Outbound Rules``` on the left hand menu.
* Click ```Add```.
* Give it a name in ```Rule Name``` (Suggested: "HOIP Outbound")
* In the ```Calls to numbers starting with prefix``` give it a prefix for dialing. This would be a number that the PBX would see at the beginning of the dialed number that it would know to use this new route. I used 8 for mine. If you know of or remember the old "Dial 9 for an outside line" thing in offices, this is the same thing. This way you don't accidently dial out of your HOIP trunk if you are trying to make a different call.
* Scroll Down to the ```Make outbound calls on``` Section.
* For ```Route 1``` select the HOIP Trunk we configured above. 
* In the ```Strip Digits``` dropdown, choose the number 1. This will strip off the prefix we defined above and then send the rest of the number dialed down the "trunk".
* Click ```OK``` at the top to save your settings.

Now whenever you want to dial someone on HOIP, you will dial ```8+<The Extension>``` (example: 8100070 for N8ACL). Any other house type calls will not go out this trunk. If you use this for a home PBX, you will need to make sure to dial 1-800 or 1-855 to make toll free calls on your home number, depending on the number you use for the prefix.

### Configure 3CX Inbound Rule

Once we have the Trunk setup and registered correctly, now we need an outbound route. 

* Click on ```Inbound Rules``` on the left hand menu.
* Click ```Add DID Rule```.
* Give it a name in ```Name``` (Suggested: "HOIP Inbound")
* In the ```DID/DDI ``` give it your extension number on HOIP.
* In the ```Route calls to``` Section, this is where you set the routing for the incoming calls for HOIP. You can route both (internal and external) to a specific extension or to a ring group if you have one setup. You could also route the calls to a voicemail box directly if you wanted to.
* Click ```OK``` at the top to save your settings.

### Now Test

Now pickup a phone and call an extension on HOIP to test it and also see if you can have someone call you. Everything should flow correctly.

### Voicemail Options

The nice thing about 3CX is you can have the PBX handle your voicemail, or you can have HOIP handle the voicemail.
* If you want HOIP to handle voicemail, just disable the voicemail options for the extension that incoming HOIP calls are being routed to on 3CX.
* If you want to handle voicemail your self, you have two additional options for this:
    * You can have your HOIP Voicemail box disabled and have everything roll to your PBX
    * You can set your pickup time on voicemail to 10 seconds on your 3CX PBX voicemail. This will pickup your call and send it to voicemail before HOIP. This option allows you to keep your HOIP Voicemail Box as a backup in case your PBX goes off line for some reason, allowing you to continue to get voicemails to your extension.

Last Updated: 06/29/2022