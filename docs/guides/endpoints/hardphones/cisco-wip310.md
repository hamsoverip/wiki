# Configure Cisco WIP 310 for HOIP

The Cisco WIP 310 is a cordless SIP (Session Initiation Protocol) phone designed for business use on a Wi-Fi network. It operates on the 2.4-GHz band, supporting the 802.11b/g standard. The phone features a 1.8-inch color LCD, and its security protocols include WEP, WPA, and WPA2.

## Connecting the phone to your home WIFI network

1. Press the “Select” button on your phones keypad.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button](./images/cisco-wip310-network-01.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button")

2. The Settings screen should appear. Press the “Select” button again.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing Settings on the screen](./images/cisco-wip310-network-02.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing Settings on the screen")

3. Use the “Down Arrow” key and select the Wireless Setup option and press the “Select” button.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the Wireless Setup menu option being highlighted](./images/cisco-wip310-network-03.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the Wireless Setup menu option being highlighted")

4. Select the “Manual Setup” option and press the “Select” button.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the Manual Setup menu option being highlighted](./images/cisco-wip310-network-04.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the Manual Setup menu option being highlighted")

5. Next press the “Options” button.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Options button](./images/cisco-wip310-network-05.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Options button")

6. Use the Down Arrow to highlight the “Scan Networks” option and press the “Select” button.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the Scan Networks menu option being highlighted](./images/cisco-wip310-network-06.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the Scan Networks menu option being highlighted")

7. Use the Arrow key to highlight the wireless network you wish to connect to and press the “Select” button.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the Select a network screen with a blurred-out list of wireless networks](./images/cisco-wip310-network-07.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the Select a network screen with a blurred-out list of wireless networks")

8. Once the phone has connected to your wireless network you will receive the message “Connected to router successfully”.

    ![Picture of the Cisco WIP310 cordless phone showing the Wi-Fi Connection Status screen, and the message 'Connected to router successfully'](./images/cisco-wip310-network-08.jpg "Picture of the Cisco WIP310 cordless phone showing the Wi-Fi Connection Status screen, and the message 'Connected to router successfully'")

9. Within a few seconds and you should see your network SSID displayed along with a bar graph showing the signal strength of the connection. Next, press the “Back” button a few times to return to the home screen.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Back button, with another circle highlighting the Wi-Fi signal strength indicator](./images/cisco-wip310-network-09.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Back button, with another circle highlighting the Wi-Fi signal strength indicator")

10. From the home screen, press the “Select” button twice.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the message 'Voice not configured'](./images/cisco-wip310-network-10.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also showing the message 'Voice not configured'")

11. The follow screen should appear. With the Phone Info option highlighted, press the “Select” button.

    ![Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also highlighting the menu item Phone Info](./images/cisco-wip310-network-11.jpg "Picture of the Cisco WIP310 cordless phone with a circle highlighting the Select button, but also highlighting the menu item Phone Info")

12. Note the IP address assigned to the phone. You will need it for the next step.

    ![Picture of the Cisco WIP310 cordless phone in the Phone Info screen, showing an IP address which has been partially obfuscated](./images/cisco-wip310-network-12.jpg "Picture of the Cisco WIP310 cordless phone in the Phone Info screen, showing an IP address which has been partially obfuscated")

## Configuring the phone to connect to HOIP

1. Open a Browser window on your computer and in to URL line and type your phone’s IP address. The following screen should appear. Click on the “Admin Login” option in the upper righthand corner.

    ![Screenshot of the top part of the Cisco WIP 310 web interface, with a red circle highlighting the 'Admin Login' link](./images/cisco-wip310-config-1.jpg "Screenshot of the top part of the Cisco WIP 310 web interface, with a red circle highlighting the 'Admin Login' link")

2. Under the **Ext 1** Tab your settings should look like this:

    ![Part one of two of a screenshot of the Ext 1 tab in the Cisco WIP 310 web interface, with red wording placed to show where specific settings need to be populated](./images/cisco-wip310-config-2.jpg "Part one of two of a screenshot of the Ext 1 tab in the Cisco WIP 310 web interface, with red wording placed to show where specific settings need to be populated")
    ![Part two of two of a screenshot of the Ext 1 tab in the Cisco WIP 310 web interface, with red wording placed to show where specific settings need to be populated](./images/cisco-wip310-config-3.jpg "Part two of two of a screenshot of the Ext 1 tab in the Cisco WIP 310 web interface, with red wording placed to show where specific settings need to be populated")

    !!! tip "Heads up"

        You need to enter the details as shown in the email containing your HOIP credentials.  
        In particular, the Proxy will be different if you've been provisioned on the EU or AP servers.

    Remember to submit your changes.

3. Under the **Phone** tab, your settings should look like this:

    ![Screenshot of the Phone tab in the Cisco WIP 310 web interface, with red wording placed to show where specific settings need to be populated](./images/cisco-wip310-config-4.jpg "Screenshot of the Phone tab in the Cisco WIP 310 web interface, with red wording placed to show where specific settings need to be populated")

    Remember to submit your changes.

**At this point your phone should be working!**

---

!!! note "Written by Brad N8PC, last updated 2025-08-07"
