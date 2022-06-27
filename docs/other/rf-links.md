# HOIP RF Linking
HOIP allows extensions to be tied to an RF connection to allow others to dial in and use the RF link.

Note that this does not enable Autopatch from the RF connection. This is a one way connection from HOIP to your RF system, basically a reverse autopatch if you will.

All RF-Link Extensions will be in the format of ```15XXX```, ```25XXX``` or ```35000```.

## Creating an RF Connection
To create a connection , you first need to have a properly configured AllStar Node. Asterisk is needed to connect to the HOIP system as the HOIP system is based on Asterisk (FreePBX is the GUI front End to Asterisk) as well. There is plenty of documentation online on configuring an Allstar Node, so that is outside the scope of this document.

It is recommended, but not required, that you configure a private node on your AllStar Node when configuring the node to have the phone connection tie to. This will allow you to disconnect the phone connection from your AllStar node in case there is a problem.

Also, we ask that you check to make sure your PTT command is setup to be *99 and release to be # in your rpt.conf file if you do not already have this setup. This will make sure that once someone dials in that they do not cause interference or problems on accident. This will also make all PTT commands uniform for the system. This should be already set by default, but if you made changes at some point, this may have been changed.

### On your Allstar Node

You will need to edit the ```IAX.conf``` and ```extensions.conf``` files.

In your ```iax.conf``` you will need to configure a stanza similar to this:

[stanza-must-match-username]
username=<username-must-match-stanza> 
type=user
context=hoipphone
host=dynamic
auth=md5
secret=<choose a password> 
disallow=all
allow=ulaw
allow=g726aal2
allow=gsm
codecpriority=host
transfer=no 

In your ```extensions.conf``` you need to configure a stanza similar to below. 
* ***Note***: you need to change the node numbers shown below to the node that you are having the connection dial into. So, if you configured a private node and if, for example, that node number is 1999, then you would use 1999 in place of 47374 below:

[hoipphone]
exten => 47374,1,answer()
exten => 47374,n,Playback(rpt/node) 
exten => 47374,n,Playback(digits/4)
exten => 47374,n,Playback(digits/7)
exten => 47374,n,Playback(digits/3)
exten => 47374,n,Playback(digits/7)
exten => 47374,n,Playback(digits/4)
exten => 47374,n,Playback(rpt/connected)
exten => 47374,n,Set(CALLSIGN=HOIP-${CALLERID(name)})
exten => 47374,n,rpt(47374|P|${CALLSIGN}) 
exten => 47374,n,rpt(47374|P)

### Connecting to Ham's Over IP

Please be sure you have an FQDN for your network.  If you don't know what an FQDN is, please google it.  NO IP ADDRESS WILL BE ACCEPTED, as they can change dynamically.

Once you have your node configured, you will need to request an RF-Link Extension on the HOIP system through the HOIP ticketing system. 

* Go to [https://hamsoverip.com/](https://hamsoverip.com/) and click "Request a Line". 
* If you have an account, sign in and then select ```Open a New Ticket```.
* If you do not have an account, then just select ```Open a New Ticket```.
* Fill out the Contact Information Part of the Ticket.
* Select the ```RF-Link Request``` Help Topic.
* Just note in the ```Issue Summary``` part that this is a request for a RF-Link
* You will need to make sure to include an IAX2 Dial string that includes the stanza information you setup for your node’s connections in the details part of the ```Issue Summary``` box. Make sure to modify this example IAX Dial String to match your system correctly.
  
  - The IAX2 Dial String is formatted like this:
  
  IAX2/username:password@fqdn:port/node-number

  
  * So for an example:

  IAX2/username:password@fqdn:4569/1999


  * This is the most important part. Without this, we are not able to connect to your system.
  
* Finally fill out the rest of the requested information in the ```RF-Link Request``` area.

Once your extension is provisioned, you will be contacted with your extension number (which will be the next sequential number in the list) to test and make sure that you can connect to your node.

Now Profit.

Last Updated: 05/23/2022
