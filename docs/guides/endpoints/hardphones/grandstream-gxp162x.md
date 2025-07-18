# Grandstream GXP1620/25

Grandstream GXP1620/25 on the HOIP network, how I got it to work.

So, you found this voip phone on a garage sale, or could pick one up for free since no one needs it? Thought it might work on the HOIP network? The good news, it works. The bad news, it takes some effort.

## Before you connect to HOIP

1. You can easily find the manual on the Grandstream webpage. Read the manual of the phone and know all the buttons and menus. Know where to plug in what connector (is confusing). Below the LCD display are 3 soft(ware defined) buttons. Understand how to correctly use those buttons. Note: only use the phone as a standalone device to connect to your router/modem. It may seem tempting to plug in your PC to the other UTP port of the phone, but this might cause issues.
2. Have the HOIP email handy with the required settings (like phone number, password, server name).
3. This phone must have the power adapter. It does not support Power Over Ethernet.
4. Make sure you have the admin password to log on the user interface. You can reset it to factory settings using the softbuttons.
5. If you have a home router:
    1. Find the mac address of the phone, sticker on the bottom
    2. Find the ip address on the phone display, use the “More” softbutton. The ip address is shown on the display (for example 192.168.1.150).
    3. On your router assign a fixed ip address to the mac address of your phone.
    4. On the phone, do not set a static ip address, but keep it on DHCP (default settings). I'll show you how later.
    5. Check firewall filters that might block voip udp traffic.
6. If the phone “sees” the router/modem, a solid box will appear top left of the lcd display. An open box icon means it has no network connection.
7. If you see a year like 1970 on the display, it means the phone has not “found” a working internet connection. Otherwise, it will pick up a date and time from a time server on the internet. It might be on a different timezone, we'll change that later.

## Setting up the phone for the HOIP network

1. Use a browser and go to the ip address you found earlier (for example [192.168.1.150](http://192.168.1.150/)). Note: you must be on the same network, it won't work if you are “outside” the network.
2. Login with the admin username and password (default: admin/admin. If so, change it asap!).
3. You are greeted with an “account status” webpage. You will see two “accounts” listed with details if they are configured (like a telephone number). Find the “empty” account.  On my phone it's account 2 so I'll continue with account 2.
4. Navigate to “accounts”, “account 2”, “general settings”.
    1. At “Account Active”, set to “no”. Note: first configurate everything than turn it on when you are finished.
    2. At “Account Name” fill in whatever is convenient for you (like “HOIP”).
    3. At “Sip server” fill in the server address you were given, followed by a semicolon and “5160”. On my phone it's “pbx-eu.hamsoverip.com:5160”.
    4. At “Sip User ID” fill in your given phone number, example “200123”.
    5. At “Authentication ID” fill in the same phone number.
    6. At “Authenticate Password” fill in that long random character issued password. Note: click on the “show password” button at the right side of the input field. Make sure it only contains the password, not spaces for example. WARNING: password field will appear empty after saving or setting it, so it might look you did not set it.
    7. At “name” fill in your desired caller id name. Usually callsign and first name, like “AB1DEF John” for example.
    8. At “Voice Mail Access Number” fill in “*97”.
    9. At “Account Display" select whatever option you would like to see on the LCD display.
    10. Other fields are empty.
    11. Click on “Save And Apply”.
5. On the main page, select “Accounts”, “Account 2”, “SIP settings”, “Basic Settings”.
    1. At “Unregister At Reboot” select “Instance”.
    2. At “Register Expiration” fill in “60”. Note: time in minutes. Admins will give you this time in seconds so use the correct value.
    3. At “Subscribe Expiration” fill in “60”. Note: time in minutes.
    4. At “Options Keep Alive Interval” fill in “30”. Note: time in seconds.
    5. At “Local SIP Port” fill in “5160”.
    6. At “SIP Transport” select “UDP”.
    7. All other fields should be at the default value/selections.
    8. Click on the “Save and apply” button.
6. On the main menu webpage, select “Settings”, “Preferences”, “Date and Time”.
    1. At “Timezone” select your timezone.
    2. Click on “Save and Apply”.
7. On the main menu webpage, select “Network”, “Basic Settings”. For my simple home internet router this worked for me:
    1. At “Internet protocol” select “IPV4 only”.
    2. At “IP Address” toggle the “DHCP” switch.
    3. Click on the “Save and Apply” button.
    4. NOTE: your ISP or home router might demand a static IP address or, use IPV6, different subnet mask etc. If so, find your network settings and fill in the required fields.
    5. Note for DHCP users: next time you visit this menu some fields might be filled with the values grabbed from the router (“IP Address”, “Gateway”, “Subnet Mask”, “DNS Server” etc).
8. On “Accounts”, “Account 2”, “General Settings”, toggle the “Account Active” switch to “ON”.
9. Wait at least half an hour to let the phone register on the HOIP network. Note: leave the phone alone. You might see the lcd screen flashing on and off if it receives or sends data. Just let is finish.

## Testing the phone/set up voicemail/finding numbers to call

1. Be sure that the “Account Status” page shows your HOIP extension is registered (Sip Registration must be “YES”).
2. Call your own number, the phone should ring, the line icon should flash. End the call.
3. Press the “Voicemail” button on the phone (looks like an envelope symbol). Use the arrow keys and the conformation key (rond button in the middle of the arrow keys) to navigate to your account and initiate the call. First time use you will be greeted by the voice mail server prompting you to set it up (your away message, pin code etc). Note: your pin code is your phone number. Change it to something different. After your voicemail is correctly set up, pressing the “voicemail” button on your phone will show you how many waiting voicemail messages you have in the lcd display. The “voicemail” button will also light up if there is a waiting voicemail.
4. The HOIP phonebook can be found here: [hamsoverip.com/phonebook](https://hamsoverip.com/phonebook)

## Make a backup of the phone configuration

Your phone's battery might be worn, and you may need to restore the saved configuration if you power off the phone.

1. On the main webpage select “Maintenance”, “Upgrade and Provisioning”.
2. Click on the “Download” button and save the file to a location you can easily find it.
3. If something goes wroing you can click on the “Upload” button and follow the prompt. Note: you may need to enter the SIP account password manually afterwards.

## Troubleshooting

_Before_ you call the admins for help

1. The admins will ask for your public ip address to diagnose the issue. You can find it at may websites, for example [helpdesk.hamsoverip.com/diy](https://helpdesk.hamsoverip.com/diy/)
2. Make screenshots of the phone's settings webpages and have them handy to send them.
3. You can file a help ticket or ask in the “Support” channel of the HOIP discord server. Usually, they will respond in a few hours.
4. Note: this phone can be tweaked to one's heart desire, like even the frequency of the dialtone. However, it also means you can easy screw things up and it can be a painful task to test all dozens of settings.

!!! note "Last updated 2025-07-18 by Peter PE1NUL"
