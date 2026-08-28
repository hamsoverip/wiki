# Grandstream GXP14xx-series

Configuring the Grandstream GXP1400-series on the HOIP network and how I got it to work.  These instructions are based heavily on referencing the GXP16xx-series guide on this site; however, there are some differences. I will also quote his guide directly at times as he did a good job describing a lot of things.

The phone was a little stubborn at first, but getting it up and running really wasn't that bad so don't be intimidated by it.  Keep in mind that this phone has reached "End-Of-Life" from the manufacturer.  That can make it more difficult to find documentation and updated firmware.  In fact, I'm still searching for updated firmware that I trust!  I have reached out to the manufacturer as the link to the "last known good" firmare is broken.  I will update this page based on their response.

## Before you connect to HOIP

1. You can easily find the manual on the Grandstream webpage. Read the manual of the phone and know all the buttons and menus. Plug the network cable into the LAN port.  You may optionally plug your computer into the PC port, although I did not test this.  The author of the GXP16xx-series article said to only use the phone as a standalone device to connect to your router/modem. He said it may seem tempting to plug in your PC to the other UTP port of the phone, but this might cause issues. Below the LCD display are three soft(ware defined) buttons. Understand how to correctly use those buttons. Finally, while not required, it may be advantagous to perform a factory reset on the phone to clear out old settings and reset the passwords.
2. Have the HOIP email handy with the required settings like: server name, port, transport type (e.g. UDP), username/extension (i.e. phone number), and password.
3. The GXP1400 and GXP1405 phones must have the power adapter. They do not support Power Over Ethernet.
4. Make sure you have the admin password to log on the user interface. You can reset it to factory settings using the softbuttons.
5. If you have a home router:
    1. Find the MAC address of the phone. There should be a sticker on the back of the phone.
    2. Find the IP address on the phone display.  Press the “NextScr” softbutton and the IP address is shown on the display (for example 192.168.1.150).
    3. On your router, assign a fixed IP address to the MAC address of your phone.
    4. On the phone, do not set a static IP address, but keep it on DHCP (default settings). This is the factory default.
    5. Check firewall filters that might block VOIP UDP traffic.
6. If the phone “sees” the router/modem, a symbol that looks like an Ethernet port that is "solid/dark" inside will appear top left of the lcd display. If it is not solid/dark then it means it has no network connection.
7. If you see a year like 1970 on the display, it means the phone has not “found” a working internet connection. Otherwise, it will pick up a date and time from a time server on the internet. It might be on a different timezone, but that can be changed later.

## Setting up the phone for the HOIP network

1. Use a browser and go to the IP address you found earlier (for example [192.168.1.150](http://192.168.1.150/)). Note: you must be on the same network. It will not work if you are “outside” the network.

2. You will see a webpage prompting you for a password (default admin). This will take you to another page and you will be on the status tab. There are two passwords you need to change.  The first password is on the Basic Settings tab and can be set by entering it into the "End User Password" field.  You will need to confirm the password in the entry box below it and then scroll down to the bottom of the page and click the "Update" button.  It will only allow A-Z, a-z, and numerals 0-9 to be used.  The second password is on the Advanced Settings tab and can be set by entering it into the "Admin Password" field.  You will again need to confirm the Admin password in the entry box below it and then scroll down to the bottom of the page and click the "Update" button.  At this point, I suggest rebooting and then logging in with the new password.

3. You are greeted with an “account status” webpage. You will see two “accounts” listed with details if they are configured (like a telephone number). Find an “empty” account.  On my phone it was Account 1 so I'll continue with Account 1.

4. Navigate to the “Accounts” tab.  There should be two accounts available.  Use either one.  I used the first account.
    1. At “Account Active”, set to “No” at first. Note: first configure everything, and then turn it to "Yes" when you are finished.
    2. At “Account Name” fill in whatever is convenient for you (like “HOIP”).
    3. At “SIP server” fill in the server address you were given, followed by a semicolon and “5160”. On my phone it's “pbx-us1.hamsoverIP.com:5160”.
    4. At “SIP User ID” fill in your provided phone number, example “200123”.
    5. At “Authentication ID” fill in the same phone number.
    6. At “Authenticate Password” fill in that long random character issued password. Make sure it only contains the password, not trailing spaces for example. WARNING: the password field will appear empty after saving or setting it, so it might look you did not set it.
    7. At “name” fill in your desired caller id name. Usually, it is the callsign and first name, like “AB1DEF John” for example.
    8. I have not been able to find a “Voice Mail Access Number”, but if you do, fill in “*97”.
    9. Click on Update and Reboot.

5. On the main page, select the “Accounts” tab again.
    1. At “Unregister At Reboot”, I have this set to Yes now.
    2. At “Register Expiration” I recommend filling in “60”. Note: time in minutes.
    3. At “Reregister before Expiration” I left it as the default “0”. Note: time in minutes.
    4. At “Local SIP Port” fill in “5160”.
    5. At “SIP Transport” select “UDP”.
    6. All other fields should be at the default value/selections.
    7. Click on Update and Reboot.

6. On the main menu webpage, select the Settings tab, and the Basic Setting tab under that. Scroll down until you see "Time Zone."  
    1. You can set it to automatic, which worked fine for me, or you can select a time zone from the menu.
    2. Click on Update and then Reboot.

7. The struggle for the best audio codec. The GXP16xx-series author stated that it seems only three audio codecs are supported by both the HOIP PBX server and the phone. His other notes were "The G.722 codec sounds the best. Other codecs may cause audio issues (like half words being heard). WARNING FOR NEW MEMBERS USING NEW HARDWARE: never start a QSO on a radio link without verifying your voice quality. Use the echo test phone number or check on a safe VOIP-only channel first."
    1. On the main page select the “Accounts”, tab.
    2. At “Preferred Vocoder", here is what I chose (mostly based on the GXP16xx-series article and what the actual choices in my phone were) – Choice 1” select “G.722 (wideband)”. Set "Choice 2" to "PCMA" and "Choice 3" to "G.723.1". Set "Choice 4" to "G.729A/B" and "Choice 5" to "PCMU". Finally, set "Choice 6" to "ILBC" and "Choice 7" to "G.726-32". Note: “Choice 1” is the first codec the phone will offer to HOIP. If it fails, it tries “Choice 2”, “Choice 3” etc.
    3. Click on Update and then Reboot.
    4. Check your sound quality. Dial 3194 for echo test. You should hear your voice after you speak some words. Your voice should be clear without distortions.

8. On the main menu webpage, select the "Settings” and then "Basic Settings" tab.
    1. At “Internet protocol” select “Prefer IPv4”.
    2. At “IPv4 Address” click on the “DHCP” switch.
    3. Click on Update and then Reboot.
    4. NOTE: your ISP or home router might demand a static IP address or, use IPV6, different subnet mask etc. If so, find your network settings and fill in the required fields.

9. Click on the  “Accounts” tab.
    1. Change the “Account Active” switch for the account you have configured to “ON”.

10. Wait for a while (some say at least half an hour) to let the phone register on the HOIP network. Note: leave the phone alone.

## Testing the phone/set up voicemail/finding numbers to call

1. Go to the "Status tab. Be sure that the “Registered” section under the account you are using says "Account #: Registered.

2. Call your own number, the phone should ring, the line icon should flash. End the call.

3. There is no “Voicemail” button on the phone. Dial *97 to set it up and also to retrieve voicemails.  It will walk you through it.First time use you will be greeted by the voice mail server prompting you to set it up (your away message, pin code etc). Note: your pin code is your phone number. Change it to something different.

4. The HOIP phonebook can be found here: [hamsoverip.com/phonebook](https://hamsoverip.com/phonebook)

## Making a backup of the phone configuration

There isn't really a good way to back up the phone configuration that I've found.  You might consider taking some screenshots with the clipping tool and save them in a word document.  If you find a better way, let me know or edit this page.

## Troubleshooting

_Before_ you call the admins for help

1. The admins will ask for your public IP address to diagnose the issue. You can find it at [helpdesk.hamsoverip.com/diy](https://helpdesk.hamsoverip.com/diy/)

2. Make screenshots of the phone's settings webpages and have them handy to send them.

3. You can file a help ticket or ask in the “Support” channel of the HOIP discord server. Usually, they will respond in a few hours.

4. Note: this phone can be tweaked further, but do so with caution.  Take those screenshots I mentioned earlier so you have a reference of what worked.

_Hope this helps! Thanks to Peter PE1NUL for the article on the GXP16xx-series phones I used as a starting point._

!!! note "Last updated 2025-09-14 by Stephen KY4G"
