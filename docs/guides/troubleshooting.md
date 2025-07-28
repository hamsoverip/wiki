# Troubleshooting Guide

<style>.tabbed-labels.tabbed-labels--linked { display: none; } </style>

!!! tip "Troubleshooting Wizard"

    === "Start"

        <h2>Welcome to the Troubleshooting Wizard</h2>

        **If you are finding that your device isn't registering properly with Hams Over IP, particularly if it's the first time you're attempting to register this device, step through this Wizard and follow the instructions on each step, as it may help you.**  
        
        ---

        First, let's check some things on your device.

        <div style="float:right">[Continue](#__tabbed_1_2){ .md-button .md-button--primary }</div>

    === "Device - 1"

        <h2>Device - step 1</h2>

        **Make sure that the information from the email you received is entered correctly into your phone.**

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_3){ .md-button .md-button--primary }</div>

    === "Device - 2"

        <h2>Device - step 2</h2>

        **If you copy/pasted the information from your email, try typing it out instead.**

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_4){ .md-button .md-button--primary }</div>
      
    === "Device - 3"

        <h2>Device - step 3</h2>

        **Make sure that the server/proxy address doesn't start with `http://` or have trailing `/` characters.**  
        
        Email clients are usually "helpful" in this regard.

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_5){ .md-button .md-button--primary }</div>

    === "Device - 4"

        <h2>Device - step 4</h2>

        **Make sure that if your device has a separate field for SIP Port (like the Polycoms do, for example), do not include the `:5160` in the server/proxy field, but put `5160` in the port field.**

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_6){ .md-button .md-button--primary }</div>

    === "Device - 5"

        <h2>Device - step 5</h2>

        **Make sure that the SIP Transport is set to UDP or UDPOnly, and not TCP or any other value.**

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_7){ .md-button .md-button--primary }</div>

    === "Device - 6"

        <h2>Device - step 6</h2>

        **Remember that the maximum password length for a Polycom/Yealink phone is 10 characters, and for an Escene phone it's 16 characters.**
        
        If you've been issued our standard 32 character password, please raise a ticket and let us know and we'll issue a shorter one for you.

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_8){ .md-button .md-button--primary }</div>

    === "Device - 7"

        <h2>Device - step 7</h2>

        **Reboot your device, this may help and "settle in" your configuration changes.**

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_9){ .md-button .md-button--primary }</div>

    === "Mid-point"

        <h2>Possibly not the device, then?</h2>

        **Ok, so it doesn't look like it is related to your device.**  
        
        ---

        Let's have a look now at some elements of your network.

        <div style="float:right">[Continue](#__tabbed_1_10){ .md-button .md-button--primary }</div>

    === "Network - 1"

        <h2>Network - step 1</h2>

        **Make sure that SIP ALG and UPNP has been disabled on your router.**

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_11){ .md-button .md-button--primary }</div>

    === "Network - 2"

        <h2>Network - step 2</h2>

        **It's possible that your IP address may have been blocked by the server.  You can verify this [here (link to blocked IP page)](#).**
        
        You can wait for 30 minutes and try again to see if it works... otherwise you may need an admin to check the server logs to help understand what's going on.

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_12){ .md-button .md-button--primary }</div>

    === "Network - 3"

        <h2>Network - step 3</h2>

        **Reboot your router, this has been known to resolve some local network issues.**

        ---

        Is your device now successfully registered?

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div><div style="float:right">[Yes](#__tabbed_1_14){ .md-button .md-button--primary }&nbsp;&nbsp;&nbsp;&nbsp;[No](#__tabbed_1_13){ .md-button .md-button--primary }</div>

    === "Oh dear"

        <h2>Oh dear. :disappointed:</h2>

        **I'm sorry we weren't able to assist you.**
        
        Please raise a ticket, detailing your problem and also mention that you've been through the Troubleshooting Wizard, and we'll see what we can do to help you.

        ---

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div>

    === "Yay"

        <h2>Great news! :star_struck:</h2>

        **I'm so pleased that we were able to assist you on this occasion!**

        Whatever it was that caused your device to start working again, if you feel that it would be useful to share with others and it _wasn't_ already in one of our Configuration Guides, please do let us know so that we can update the Wiki!

        ---

        <div style="float:left">[Start over](#__tabbed_1_1){ .md-button }</div>

??? alert "Collapsed data"

    If you are finding that your device isn't registering with the network, particularly if it's the first time you're attempting to register this device, then have a look through the following steps, which may help.

    - Make sure that the information from the email you received is entered correctly into your phone.
    - If you copy/pasted the information from your email, try typing it out instead.
    - Make sure that the server/proxy address doesn't start with `http://` or have trailing `/` characters.  Email clients are usually "helpful" in this regard.
    - Make sure that if your device has a separate field for SIP Port (like the Polycoms do, for example), do not include the `:5160` in the server/proxy field, but put `5160` in the port field.
    - Make sure that the SIP Transport is set to UDP or UDPOnly, and not TCP or any other value.
    - Remember that the maximum password length for a Polycom/Yealink phone is 10 characters, and for an Escene phone it's 16 characters.  If you've been issued our standard 32 character password, please raise a ticket and let us know and we'll issue a shorter one for you.

    Also, check to see if there is a [Configuration Guide](./index.md) for your device, and check through that first.

    If you're absolutely certain that the device is configured correctly, try out the following:

    - Reboot your device, this may help and "settle in" your configuration changes.
    - Make sure that SIP ALG has been disabled on your router.
    - Make sure that UPNP has been disabled on your router.
    - It's possible that your IP address may have been blocked by the server.  You can wait for 30 minutes and try again to see if it works... otherwise you may need an admin to check the server logs to help understand what's going on.
    - Reboot your router, this has been known to resolve some local network issues.
