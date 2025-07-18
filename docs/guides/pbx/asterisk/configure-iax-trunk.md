# Configuring an asterisk IAX Trunk for HOIP

The Ham's Over IP service offers the ability to connect your home asterisk PBX System to our system. This allows you to use any number of phones on your extension, control your own voicemail and many other things. In many ways, it's easier to run your own PBX then it is to try to connect multiple phones to our system. The more people who can use a their own PBX is the less number of phones trying to register to our network and helps keep resources free.

It does take a bit of work to get your own PBX configured and setup, but it in the end, the rewards are nice.

This guide assumes that you already have an asterisk PBX setup and ready. There are many other guides on the Internet explaining how to do this, so that is outside the scope of this document.

This guide also assumes you have a Linux based system. If you are setting this up in another operating system, please confirm the documentation for location of configuration files etc.

## Configuring the Trunk

### Preparation

- The asterisk configuration files are found in /etc/asterisk/.
- By default, the iax2 channel driver is not loaded. Check in modules.conf for the line

``` ini title="modules.conf snippet"
load = chan_iax2.so
```

If it is not there, add this line with the other Channel Drivers

### Create the Trunk

- To configure the IAX2 trunk, you need to edit iax.conf.
- Contents of iax.conf:

``` ini title="iax.conf snippet"
[general]
bandwidth=high
autokill=yes

;..... receive calls
register => <USER/EXTENSION>:<PASSWORD>@<SERVER ADDRESS>

;..... make calls
[HoIPContext]
username=<USER/EXTENSION>
secret=<PASSWORD>
type=friend
host=<SERVER ADDRESS>
context=HoIPContext
trunk=true
```

Note:

- The fields in angled brackets are provided in the confirmation email when you apply for your HOIP IAX2 trunk line.
- SERVER IAX2 PORT defaults to 4569, so you don't need to specify this in the configuration.
- If you find you can receive but not make calls (or vice versa), check carefully for typos. It is easy to make a mistake!

### Create the Outbound Route

Once you have the trunk created, you will need to configure an Outgoing Route in order to make outgoing calls on your trunk.

- To add the inbound and outbound configuration, you need to edit `extensions.conf`.
- In your context configuring the dialplan, add the following section:

``` ini title="extensions.conf snippet"
; Make calls to HoIP
exten = _47X.,1,Dial(IAX2/HoIPContext/${EXTEN:2})  ; 47 is prefix for HamsOverIP numbers
 same = n, Hangup()                                ; This line is not strictly necessary, but recommended practice
```

To contact the HamsOverIP number 123456, dial 47123456. The 47 will be dropped, and the remaining number passed to HamsOverIP to make the call.

### Create the Inbound Route

- Still editing in `extensions.conf`
- Assuming you are using `pjsip` to define your extensions, and you want to pass HOIP calls to extension 123, add the following section:

``` ini title="extensions.conf snippet"
; Receive calls from HoIP
[HoIPContext]
exten = s,1,Dial(PJSIP/123)
```

Of course you can do much more with asterisk, such as falling through to voicemail and ringing on more than one phone. How to do this is beyond the scope of this guide.

For the new rules to take effect, you will need to reload asterisk.

You should now be able to make and receive calls across your HOIP Trunk. I recommend making a call to one of the test numbers while running the asterisk CLI so you can see the messages related to the call, and confirm everything is OK.

Thanks to **Christopher, M0YNG** for working out the details to make this work, and for taking the time to help me (Paul) debug my setup. I would be nowhere without his support. Any errors here are mine, not his!

----

!!! info "Last Updated 2024-07-11 by Paul, MW7PAJ"
