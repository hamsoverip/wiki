# Troubleshooting Guide

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
