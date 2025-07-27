# Configure Busy Lamp Field (BLF)

!!! success "You can now get to this page using a shorter URL: [hamsoverip.github.io/blf](https://hamsoverip.github.io/blf)"

The Busy Lamp Field (BLF) is a function of Asterisk and some phones that allows the end user to program a speedial button on their phone to light based on the status of the line that the speeddial is set to connect to. If the line is busy - in other words, someone is using the line - it will glow red, otherwise it will glow green. This works for normal extensions and conference bridges. If someone is dialed into a conference, the light will be red, indicating someone is in the conference, otherwise it will glow green.

!!! warning "Cross-server BLF"
    In July 2025 we introduced cross-server BLF, meaning if you're on one particular server, say US1 (extension beginning with `1`), you can now use BLF to monitor lines on any of the other servers.  Please bear in mind though, that whilst you can use BLF to monitor extensions, trunks, and conferences on your home server, cross-server BLF only supports extensions and trunks.

Of course, we also have BLF capability on the [Hams Over IP Phonebook](https://hamsoverip.com/phonebook).

This Guide describes how to configure the feature on specific phones.  We will add to this Guide as and when we get information relating to other phones and apps.

## Cisco

??? note "Cisco SPA-series phones and sidecars"

    Cisco SPA-series phones and sidecars have the capability to utilise the speed dial buttons as BLF indicators.

    In order to do this, you will need to access the Web Configuration of the phone.  If you open a web browser and go to the IP address of the phone, you should be able to access the Web Configuration Interface.

    From there, you will need to navigate to the key you want to edit, be it a button on the phone or on the sidecar.

    When you are at the key you want to edit, you will need to look for the `Extended Function` field for that line and in that you will place something similiar to the following:

    ``` text
    fnc=sd+blf;ext=<extension to speeddial>@$PROXY;sub=<extension to monitor>@$PROXY;nme=<Friendly Name>;vid=<line ext in config>
    ```

    Where:

    * `fnc=sd+blf;` - This sets the function of the button for both a speedial and BLF for that button
    * `ext=<extension to speeddial>@$PROXY;` - this corresponds to the `sd` part of the function, and is the extension you want to speeddial. `$PROXY` is a variable that is taken from another part of the phone configuration. Leave that alone. That just basically sets the server.
    * `sub=<extension to monitor>@$PROXY;` - this corresponds to the `blf` part of the function, and is the extension you want to monitor. This is essentially the same as the `ext` section above.
    * `name=<Friendly Name>;` This sets the name of the button that is displayed on the phone screen or the sidecar screen (if it has one). If you are using a sidecar without a screen, this can be omitted or left in as a reminder within the Web Interface.
    * `vid=N` where N is the number of the Ext you want to send the call out. In other words, let's say you have a Home VOIP number on Ext 1 and HOIP on Ext 2 and you want this button to speedial an extension on HOIP, you would set it to look like `vid=2`. Otherwise it will default to line 1 of the phone.

    So an example function string would be:

    ``` text
    fnc=sd+blf;ext=1234@$PROXY;sub=1234@$PROXY;nme=Joe, WA1ABC;vid=2
    ```

    !!! info "Last Updated 2025-07-17 Dave M7TLB"

----

This is by no means an exhaustive list... you can help us by [contributing](../../wiki/contributing.md) a Guide where one doesn't already exist.
