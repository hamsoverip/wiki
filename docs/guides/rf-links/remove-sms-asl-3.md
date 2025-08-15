# How to remove SMS from ASL version 3.0

Courtesy Brad, N8PC

To create a private node for HamsOverIP on ASL3

1. SSH into your ASL3 Node make sure to use sudo for the following commands (unless you're in super user mode)
2. `sudo asl-menu`
3. select Menu option # 1 Node settings
4. select Menu option # 1 Allstar Node setup
5. select A to add a Node
6. type in a private node number (anything from 1000 to 1999) I like to use 1995
7. next select # 4 HUB w/no radio
8. enter Callsign of the node or repeater
9. now click on Update Node 1995
10. you will not need to enter a node password
11. you should have the following:

    - 1 Node number : 1995
    - 2 Node password :
    - 3 Node callsign : Your_Callsign
    - 4 Radio interface : No radio interface or HUB node
    - 5 Duplex type : 0 < this gets set to 0 and FULL duplex
    - 6 Post node status : No
    - 7 Node access list : Open
    - 8 Interface Tune CLI

12. select Back with arrow keys
13. select #2 Restart Asterisk
14. select #4 Update IAX port (make a note of it you will need it later)
15. select &lt;Back&gt;
16. select &lt;Exit Main Menu&gt; and Yes to exit

Now at the Bash shell prompt we will do the following:

```bash
cd /etc/asterisk
nano iax.conf
```

type in the following or copy and paste:

```ini
[stanza-must-match-username]
username=<username-must-match-stanza>
type=friend
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
requirecalltoken=no
```

CTRL-X to exit
Y to save and press Enter

```bash
nano extensions.conf
```

insert the following: We are still using 1995 as the node number

```ini
[global]
NODE2 = 1995  << add to the global stanza

[hoipphone]
exten => ${NODE2},1,Ringing()
same => n,Wait(1)
same => n,Answer()
same => n,Playback(rpt/node)
same => n,Playback(digits/4)
same => n,Playback(digits/5)
same => n,Playback(digits/7)
same => n,Playback(digits/4)
same => n,Playback(digits/3)
same => n,Playback(digits/2)
same => n,Playback(rpt/connected)
; same => n,Set(CALLSIGN=HOIP-${CALLERID(name)})
; same => n,rpt(${NODE2}|P|${CALLSIGN})
same => n,rpt(${NODE2}|P)
```

Change numbers after `digits/` to your Allstar node number

CTRL - X to exit
Y for Yes and press enter to save it
reboot for changes to take effect.

You have offically setup your private node with no text messaging for HamsOverIP.

Now follow the steps in our [configuration guide](./configure-rf-links.md) to create your Dial string, and then go to our [ticketing system :material-open-in-new:](https://helpdesk.hamsoverip.com/osticket/){ target="_blank" } and create a ticket for an RF Node number - Be Patient as this does take time.

Please note: You will have to send a ticket in to HOIP to adjust your IAX2 String to now match to your new private node number. If you require guidance on the format of the IAX2 string, then please check our [configuration guide](./configure-rf-links.md).  Once that's done, test to confirm the SMS beacons are gone.

Note: You will NOT see who is connected or hear the connection. This is normal.

You will see on your Allmon3 or Supermon dashboards when someone keys up on HamsOverIP when Connected to your node. With this setup you can drop the private node if a person is creating problems and reconnect it at a later time.

!!! note "Written by Brad N8PC, last updated 2025-08-16"
