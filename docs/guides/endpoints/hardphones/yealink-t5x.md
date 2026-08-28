# Yealink T5X Series of Phones

[![T54](https://charliemckinley.com/images/T54W-Front-1.jpg "T54")](https://charliemckinley.com/images/T54W-Front-1.jpg "T54")[![T58](https://charliemckinley.com/images/yealink-SIP-T58W.jpg "T58")](https://charliemckinley.com/images/yealink-SIP-T58W.jpg "T58")

## Find Phone IP

On the T54, press the **OK** button for the status screen.

On the T56 or T58 swipe down from the top of the screen and select **Settings** and then **General** in the Status box.

[![T58](https://charliemckinley.com/images/T58Status.jpg "T58")](https://charliemckinley.com/images/T58Status.jpg "T58")

## Factory Reset

There are three ways to **Factory Reset** your T54W phone.

1. Press the **OK** button, enter the IPv4 address into your web browser.  Enter **Username** and **Password** (Default is **admin** and **admin**).  Navigate to the **Settings** tab, then to **Upgrade** on the side menu, and press the **Reset to Factory** button and follow the prompts.
2. Press the **Menu** button on the screen, arrow to **Advanced** and press **OK**. Enter the password using the number pad. (1 press of the 2 key is "a", two presses is "b", etc.) Once into the Advanced menu press **5**, then press **1**, then confirm the reset.
3. Press and hold the **OK** button until the **Reset to Factory Setting?** pop up shows, then select the **OK** button on the screen and follow the prompts.

## Programming For HOIP

1. Enter the web gui by entering the IPv4 address into your web browser. (See Find Phone IP above for directions)
2. Navigate to the **Account** tab.  In the **Register** page choose the **account** number you want to set up.
3. Change **Line Active** to **ON**.
4. Enter in a name in **Label**, like **HOIP**
5. Enter in a **Display** name, like **HOIP *Your Extension Number***.
6. Enter your extension number in **Register Name**.
7. Enter your extension number in **User Name**.
8. Enter your HOIP password in **Password**.
9. Enter your HOIP Server in **Server Host** and **port** number.  like **pbx-us1.hamsoverip.com** in Server Host and **5160** in Port.
10. Make sure Transport is **UDP**, Server Expires is **3600**, Server Retry Counts is **3**.  No entries in SIP Server 2 and Enable Outbound Proxy Server is **Disabled**.  NAT to **Disabled**.
11. Click on **Confirm** to save the settings.
12. Click on the **Dsskey** tab.
13. On Line Key 1, select  **Line** for Type, **Default** for Value, Enter your Extension in Label, make the Line match the account number from the Account tab.
14. Click on **Confirm** to save the settings.
[![T58](https://charliemckinley.com/images/T58AccountRegister.png "T58")](https://charliemckinley.com/images/T58AccountRegister.png "T58")

## BLF Set Up

Under the **Dsskey** tab, select the **Line Key** area that you want to program, on the desired **Line Key** select **BLF** from the dropdown, enter the extension you want to monitor in the **Value** field, give it the appropriate label in the **Label** field and select the **line number** the BLF is associated with (the **Line** number corresponds directly the **Account** you set up on the **Account** tab.)

[![T58](https://charliemckinley.com/images/T58LineKey.png "T58")](https://charliemckinley.com/images/T58LineKey.png "T58")

## Tips and Tricks

### Verizon Models

If you find a Verizon OneTalk version, you can convert it to work with any other SIP provider by following these directions: https://vwdmi.com/setting-a-verizon-onetalk-phone-back-to-yealink-firmware/

### Screen Capture

In the Web GUI, click on the **Features** tab, then on **Remote Control**, in the **Action URI Allow IP List** field enter in the IP address of the device you want to allow to capture the screenshots or the word **any** to allow all devices to capture.  Then go to http://xxx.xxx.xxx.xxx/screencapture (where xxx.xxx.xxx.xxx is the IP address of your phone)

[![T58](https://charliemckinley.com/images/T58ScreenCapture.png "T58")](https://charliemckinley.com/images/T58ScreenCapture.png "T58")

### Power LED

There are several settings that pertain to the red power LED statuses.  I prefer "all off".
[![T58](https://charliemckinley.com/images/T58PowerLED.png "T58")](https://charliemckinley.com/images/T58PowerLED.png "T58")

### Notification PopUps

You can enable or disable the popups on the screen.  I prefer "no popups".

[![T58](https://charliemckinley.com/images/T58NotificationPopUps.png "T58")](https://charliemckinley.com/images/T58NotificationPopUps.png "T58")

----

!!! info "Last updated 2026-2-21 by Charlie KE8QLV"
