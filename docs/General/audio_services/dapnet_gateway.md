# DAPNET Paging Gateway

Developed by: Jeff, N8ACL [https://github.com/n8acl/dapnet_paging_gateway](https://github.com/n8acl/dapnet_paging_gateway)
Hosted by:

Remember the days of calling a pager number, entering your callback number or leaving a voicemail and that message being sent to the end user? Well those days are kind of back... at least for hams. This is what the kids are calling "Retro-tech" today.

The Decentralized Amateur Paging Network (DAPNET) is a paging network that was setup by some hams in Germany and has slowly been moving around the world in popularity. While it has a large user base outside the US, it is gaining some traction in the US as well. It utilizes the old POCSAG protocol to send Alpha-Numeric messages to old Alpha-Numeric text pagers.

It can breathe new life into those old Alpha-Numberic Pagers that we used to all carry around. It can use your Pi-Star hotspot to send a page or a high profile repeater. More information about DAPNET can be found at [https://hampager.de](https://hampager.de). The site is in German, so you will need to translate it to your language, or be able to read German.

The DAPNET Paging Gateway provides the ability to simulate the old paging gateway callback system from HOIP to DAPNET.

Questions about the DAPNET Paging Gateway can be directed to at extension or on Discord or via email

## Accessing the DAPNET Paging Gateway

The DAPNET Paging Gateway is accessible from any of the linked services to HOIP (HOIP, AmateurWire, OARC and Meshphone) using the correct access code from the linked services of course.

- From West of the Rockies, call extension `90004`
- From East of the Rockies, call extension `90004`

In either case, press `2` at the menu voice prompts.

## Using the DAPNET Paging Gateway

After pressing `2` your call will be directed to the gateway.

Dialing a person is accomplished by DMR ID. This was the most universally accessible way to make this work (more on that below, see the FAQ's).

Follow the voice prompts given to use the gateway:

- `At the Beep, enter the DMR ID of the person you wish to contact and then press the pound key` - At the beep, dial the DMR ID of the person.
- `At the beep, please enter your callback number and then press the pound key.` - at the beep, enter the number you want the person to call you back at. This can be your Ham VOIP extension (any of the services) or an actual PSTN number.

A page will then be sent to the person and be formatted as `Yourcallsign: Call me at YourCallbackNumber #HOIP_DAPNET_GATEWAY`

- Example: `N8ACL: Call me at 8675309 #HOIP_DAPNET_GATEWAY`

At the end, the call will automatically hangup.

## Thanks

I did want to say thanks to the people who, behind the scenes, helped me with research, testing, encouragement and even gave me the idea to do this. You know who you are.

## Availability

The gateway is available subject to all the usual things that effect downtime at a residence. Power, Network, Internet, etc.

## Frequently Asked Questions (FAQ)

### How does this work?

!!! note ""
There is alot of technical mumbo jumbo I can get into, but simply just know that there is alot of Python and Asterisk Magic going on in the background. There is alot of data being pulled, messaged and loaded from various sources to make it all work.

### Why DMR ID for dailing a person instead of RIC or HOIP Extension?

!!! note ""
DMR ID is a universal number that any ham can have. That is why this was chosen. There is not a way to cross reference Pager RICS to Callsigns from DAPNET and not every DAPNET Subscriber will have a HOIP/AW/OARC/MP extension. Plus DAPNET uses a modified version of a persons DMR ID as the Pager RIC, if they do not provide one from the pager they have. So using this method, a user can send a page to any DAPNET Subscriber. The script that is used will convert the DMR ID to a callsign to send the page to them via the DAPNET API.

### How do I know or how do I find out if the person I want to page is a DAPNET Subscriber?

!!! note ""
Yeah. This is a tricky question as there really is no straight answer. There are some ways to do this:

      * First off, the easiest way is to ask the person you are wanting to send pages to.
      * If you are a DAPNET Subscriber yourself, you can login to the DAPNET website and do a search for the person. If they come up, they are a subscriber. However, they need to have everything setup and configured for it to go through.

    Otherwise, there really isn't a straight forward way

### So how do I find a person's DMR ID?

!!! note ""
Once you know if a person is a DAPNET subscriber, you can go to [RadioID.Net](https://radioid.net) and use the online database search to get their DMR ID. You can also look in the HOIP/AW/OARC phonebook and see if it is there. And of course, you can always ask the person you want to page for their DMR ID.

### What if they don't have a DMR ID?

!!! note ""
Then you are not able to use this system to page them. Sorry. There is nothing I can do about that.

### How do I know if the page went through?

!!! note ""
Just like in the old days, the only way you know it went through and if they got it is if they call you back. You just have to cross your fingers and hope for the best.

### What happens if I try to page someone who is not a DAPNET subscriber?

!!! note ""
Absolutly nothing. No message will go through to anyone. As the old saying goes, it will just drift in CyberSpace for all eternity. Unfortunatly, just like the old days, there will also be no prompt on the phone either. You just have to cross your fingers and hope for the best.

### What if I want to send a text page to someone?

!!! note ""
You can use the Discord DAPNET bot in the HOIP Discord Server. Please see [https://github.com/n8acl/dapnet_discord_bot#bot-commands](https://github.com/n8acl/dapnet_discord_bot#bot-commands) or type `/help` in a HOIP Discord channel and make sure to select the one for the DAPNET Bot on how to make this work (note that you must be a DAPNET subscriber to use this).

    One other option, if you are a DAPNET Subscriber and have configured Pi-Star to use DAPNET, is to use the API built into Pi-Star. There are other guides online to do that.

    Another option is to use the DAPNET App that is available on the iOS and Google Play app stores.

Last Updated: 09/12/2022
