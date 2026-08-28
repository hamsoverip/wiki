# Configuring an asterisk SIP Trunk for HOIP

The Hams Over IP service offers the ability to connect your home asterisk PBX System to our system. This allows you to use any number of phones on your extension, control your own voicemail and many other things. THe guide assumes a tested setup of asterisk PBX ready as well as a Linux based system.

## Configuring the Trunk

### Preparation

- Asterisk configuration files can be found in `/etc/asterisk/`.
- All fields with angle brackets are provided in the documentation sent to you in your ticket.

### Create the Trunk

- To configure the pjsip trunk, you need to edit pjsip.conf.

``` ini title="pjsip.conf snippet"
; This is an example config of asterisk pbx
; for ham over ip using a pjsip trunk
; extension_num will be supplied by hams over ip
; change address to one closest to you
; name schemes are my own and can be different or
; all the same

[transport-udp]
type = transport
protocol = udp
bind = 0.0.0.0

[hoip-registration]
type = registration
transport = transport-udp
outbound_auth = hoip-auth
client_uri = sip:<exten_num>@<hoip_hostname:port>
server_uri = sip:<hoip_hostname:port>
contact_user = <exten_num>

[hoip-auth]
type = auth
auth_type = userpass
username = <exten_num>
password = <password>

[hoip-aor]
type = aor
contact = sip:<exten_num>@<hoip_hostname:port>
qualify_frequency = 60

[hoip-endpoint]
type = endpoint
transport = transport-udp
context = hoip-personal ; defined in extensions.conf
disallow = all
allow = ulaw
allow = alaw
from_user = <exten_num>
auth = hoip-auth
from_domain = <hoip_hostname:port>
contact_user = <exten_num>
outbound_auth = hoip-auth
aors = hoip-aor

[hoip-identify]
type = identify
endpoint = hoip-endpoint
match = <hoip_hostname:port>

; this ends the section for your connection to hoip
; below is an example that would work with a softphone
; such as microsip, which allows you to place calls
; over the network

[sphone-endpoint]
type = endpoint
transport = transport-udp
context = hoip ; another one defined in extensions.conf
disallow = all
allow = ulaw
auth = sphone-auth
aors = sphone-aor
allow_subscribe = yes

[sphone-auth]
type = auth
username = <expected_extension_local>
password = <password_for_local>

[sphone-aor]
type = aor
max_contacts = 2

[sphone-identify]
type = identify
endpoint = sphone-endpoint
match = <ip_of_phone> ; can be a softphone on your pc or hardphone
```

### Create Outbound Route

Once you have the trunk created, you will need to configure an outgoing route in order to make outgoing calls on your trunk.

- To add inbound and outbound configuration, you need to edit `extensions.conf`.
- In your context configuring the dialplan, add the following section:

``` ini title="extensions.conf snippet"
[hoip]
; out to hoip network from pbx phones
exten => _79.,1,Dial(PJSIP/${EXTEN:2}@hoip-endpoint, 20) ; 79 can be anything, just tells the system you are dialing out. :2 is stripping those digits
same => n,Hangup() ; optional, but also optimal
```

To contact the Hams Over IP number 123456, dial 79123456. The 79 will be dropped and the remaining number passed to HamsOverIP to make the call

### Create the Inbound Route

- Still editing in `extensions.conf`

``` ini title="extensions.conf snippet"
[hoip-personal]
exten => _X.,1,Dial(PJSIP/<expected_extension_local>, 20) ; rings for 20 seconds
same => n,Hangup()
```

This concludes a very basic config of asterisk using a pjsip trunk and you can expand on it with voicemail, ringing out to multiple phones, and more, all beyond the scope of this guide.

You should now be able to make and recieve calls across your HOIP Trunk. I recommend making a call to a test numbers while running the asterisk CLI so you can confirm everything is working.
----

!!! info "Last Updated 2026-01-10 By Ada, KQ4IDU"
