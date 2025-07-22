# How to remove SMS from ASL versions of AllStar

Courtesy Brad, N8PC

To remove SMS beacons from an AllStar node that uses the “ASL 1 & 2” software version, you need to create a private node and connect to HamsOverIP via your private node, not your public node.

To create a private node, you will need to choose a new node number between 1000 and 1999.

For demonstration purposes here, we will use node # 1995 as our private node, and also for demonstration purposes, we will use # 12345 as our public node number.

Please remember to replace node # 12345 with your actual public node number.

In your `rpt.conf` file, place this into it:

```ini
[1995] ; private node for HamsoverIP
rxchannel=dahdi/pseudo
duplex=0
link2link=yes
;connpgm=/usr/local/sbin/supermon/smlogger 1 ; only needed if you use them.
;discpgm=/usr/local/sbin/supermon/smlogger 0 ; only needed if you use them.
controlstates=controlstates
scheduler=schedule
morse=morse
macro=macro
functions=functions
phone_functions=functions
link_functions=functions
telemetry=telemetry
wait_times=wait-times
telemnomdb=0
telemduckdb=-9
holdofftelem=1
telemdefault=1
```

Now, add the following to nodes list at the end of your `rpt.conf`

```ini
[nodes]
1995 = radio@127.0.0.1/1995,NONE
```

Next, locate this line in your `rpt.conf` file

```ini
;startup_macro=
```

Change that line to now read like this:

```ini
startup_macro=*31995
```

Now, in your `extensions.conf` file place the following:

```ini
[radio-secure]
exten => 1995,1,rpt,1995

[radio-iaxrpt]
exten=1995,1,Rpt,1995|X
```

Then in your `extensions.conf` file, modify your hoipphone Stanza (or add if you don't have an existing hoipphone Stanza yet) to no longer use your public node number, but rather now use your private node number.

```ini
[hoipphone]
exten => 1995,1,answer()
exten => 1995,n,Playback(rpt/node)
exten => 1995,n,Playback(digits/4)
exten => 1995,n,Playback(digits/7)
exten => 1995,n,Playback(digits/3)
exten => 1995,n,Playback(digits/7)
exten => 1995,n,Playback(digits/4)
exten => 1995,n,Playback(rpt/connected)
;exten => 1995,n,Set(CALLSIGN=HOIP-${CALLERID(name)})
;exten => 1995,n,rpt(1995|P|${CALLSIGN})
exten => 1995,n,rpt,1995|P
```

Then after modifying these files and saving them, restart your node.

Please note: You will have to send a ticket in to HOIP to adjust your IAX2 String to now match to your new private node number. If you require guidance on the format of the IAX2 string, then please check our [configuration guide](./configure-rf-links.md).  Once that's done, test to confirm the SMS beacons are gone.

Please note: You will NOT see who is connected or hear the connection. This is normal.

!!! note "Last updated 2025-07-22 Brad N8PC"
