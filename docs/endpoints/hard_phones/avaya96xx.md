# Avaya 96xx Series Phones

!!!note Advanced Setup
    Note that this is an advanced setup and will require some advanced DHCP routing capabilites to configure this

!!!note When Requesting a new Line
    When requesting a new line in the ticket system, please make sure to put a comment on your ticket that you are using an Avaya Phone for the line and that you will need to have your Password generated with 13 characters max. If you already requested the line, put a ticket in to have the password regenerated to only be 13 characters max.

For this to work, the Avaya 96xx series need a SIP firmware update flashed. To do this:

* You must have a webserver and DHCP Server running on your network. (These are outside the scope of this document).
* Download the file ```96x1-IPT-SIP-R7_1_9_0-032720.zip``` from the [Avaya Support Site](https://support.avaya.com/downloads/download-details.action?contentId=C20204710122730_1&productId=P0553) and unzip it to the root folder of your webserver.
* Set option 242 on your DHCP server to “HTTPSRV=(your-http-server-ip)” ie HTTPSRVR=10.0.0.8 (This applies if you are able to. This it the advanced part of the setup that you need to be able to do.)

Next we need to create a file called ```46xxsettings.txt``` in the root of your webserver folder:

* You can [download the txt file from here](https://hamsoverip.github.io/wiki/files/46xxsettings.txt) and place it in the web root folder of the webserver (where you placed the SIP Firmware files).
* Open the txt file and change the following settings:
    * Set the following to the domain name of the peer sent in your email (ex. ```pbx-us1.hamsoverip.com```)
        * ```SET DOMAIN``` 
        * ```SET SIPDOMAIN```
        * ```SET MWISRVR```
        * ```SET SIPPROXYSRVR```
    * ```SET SIP_CONTROLLER_LIST```: this needs to be the IP address of the peer you are connecting to. Change where it says ```<IPv4 ADDRESS OF THE PEER>```
        * To find the IP Address of the peers, use the ```nslookup``` command (instead of the ping command. Ping can get your IP address blocked by FAIL2BAN). Works on all platforms (Windows, MacOS and Linux). This should return information about the IP Address of the peer. You want the IPv4 address. This should be in the format of ```XXX.XXX.XXX.XXX```
            * Example:
                * ```nslookup pbx-us1.hamsoverip.com```
                * For Linux users: if you get an error ```-bash: nslookup: command not found```, run the command ```sudo apt-get install -y dnsutils``` and then try the ```nslookup``` command again.
    * ```SET DNSSRVR```: Set this to the IP Address of your router if you are not already running a local DNS server, like PI-Hole or BIND9 or something similiar.
    * ```SET TIMEZONE```: Set this to your timezone in TZDATA format (ex. ```America/New_York```)
    * OPTIONAL: ```SET DATEFORMAT```: Set this to the date format you prefer (ex. ```%m/%d/%y``` for 2 digit month/2 digit day/2 digit year)
    * OPTIONAL: ```SET FORCE_SIP_USERNAME``` and ```SET FORCE_SIP_EXTENSION```: Set this to the extension you received.
    * OPTIONAL: ```SET FORCE_SIP_PASSWORD```: Set this to the password you received.
  
Next we need to reset the phone to clear out any existing extension information:

* Boot the phone and hit the ```*``` key when the logo appears
* Enter the password: ```27238``` (CRAFT) and hit the ```#``` key.
* Scroll down to ```Clear``` and then select ```Clear Phone```

Now, verify that the phone is in SIP mode and change if it is not (it is probably in H.323):

* Boot the phone and hit the ```*``` key when the logo appears
* Enter the password: ```27238``` (CRAFT) and hit the ```#``` key.
* Scroll down to ```SIG``` and tap the right arrow until it says ```SIP```
* Tap the ```Save``` button
* Phone will reboot

Once this is all completed, you will need to enter your username and password from your credentials email for the HOIP system after the reboot.

* If the phone is configured correctly, a screen will pop up asking for login information. Type in extension number into the user and userid field and press the Enter key.
* It will prompt you for your password. This should be 13 Characters Max.
* If entered correctly, your phone should populate with your extension.

Now try to make a call.

Contributed by Michael, N5ZR

Last Updated: 08/02/2022
