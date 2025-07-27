# Cisco Linksys SPA942

Your Cisco IP Phone provides a web interface for the phone user that allows you to configure some features of your phone by using a web browser.

This article will guide you through the steps for basic configuration to make it work with HOIP

The Linksys SPA942 IP telephone can be configured as a two (2) line or, via a simple software upgrade, a four (4) line full featured business phone with pixel based graphical display, speakerphone and headset port. Stylish and functional in design, the SPA942 VoIP telephone is ideal for a residence or business using a hosted IP telephony service, an IP PBX, or a large scale IP Centrex deployment. The SPA942 leverages industry leading VoIP technology from Linksys to deliver an upgradeable high quality IP Phone that is unparalleled in features, value, and support.

## Step 1

* Press the Paper "button" and then press number 9 which will take you into the network settings.  Option 2 will show you the phone's IP address.

![An image showing where the settings button is on the SPA942](./images/cisco-linksys-spa942-step1.gif "An image showing where the settings button is on the SPA942")

## Step 2

Go to any browser equipped computer on your network and enter the address: `http://ip_address/`
(where _ip_address_ is replaced by the address that was given to you in STEP 1).

## Step 3

Click on the "Admin Login" button near the top right side of the screen, then click on the "Ext 1" tab.

![An image showing the menu bar on the SPA942. An arrow points to Ext 1](./images/cisco-linksys-spa942-step1.gif "An image showing the menu bar on the SPA942. An arrow points to Ext 1")

## Step 4

You need to modify only a few parameters from the factory default. They are listed here:

* **Proxy**: _the Server provided in your provisioning email: e.g. `pbx-us1.hamsoverip.com:5160`_
* **User ID**: _the Username/Extension provided in your provisioning email: e.g. `102263`_
* **Password**: _the Password provided in your provisioning email_
* **Preferred Codec**: G.721a or G.721u

The following screenshot is from a different set of instructions, so the values contained in the fields will be different/incorrect

![An image showing a specific section of the SPA942 web interface](./images/cisco-linksys-spa942-step1.gif "An image showing a specific section of the SPA942 web interface")

!!! note "Last updated 2025-07-27 Dave M7TLB"
