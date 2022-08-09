# Frequently Asked Questions

Last Updated: 07/28/2022

This document is a place to put some of the more Frequently Asked Questions of the service that are quick, short answers. If an answer requires more indepth steps, a guide will be created and linked to from this document.

This is a long document, so to the right side of this page is a Table of Contents that will link you to the sections and within each section is a smaller Table of Contents that will link you to the question you have and the answer. You can also do a search by doing ```Ctrl``` + ```F``` on Windows and Linux or ```Cmd``` + ```F``` on Mac.

<hr />

## General

### How do I get started?

!!! note ""
    First you will need to get a phone. As long as your phone will allow or handle SIP, you are good to go.

    Then check out our [Getting Started Guide](https://hamsoverip.github.io/wiki/General/user_guides/getting-started/) to start the process.

    You can also look through the rest of the Wiki to get an idea on how to get started.

### Where can I go for more help?

!!! note ""
    You are already in the best place for getting more help! This Wiki. This is where alot of guides and information can be found about the service and things are added all the time.

    Next place you can go is one of our [Chat Services](https://hamsoverip.github.io/wiki/General/user_guides/chat-services/). Our main form of communication is Discord, but some other chat services are bridged into it. 

### Can I contribute to the Wiki?

!!! note ""
    Absolutely! We encourage our user community to contribute to the Wiki to help expand the knowledge here. To see how, check out our [Getting Started Guide](https://hamsoverip.github.io/wiki/General/user_guides/getting-started/)

### What Feature Codes can I use on the system?

!!! note ""
    All Feature Codes can be found in the [Feature Codes Guide](https://hamsoverip.github.io/wiki/endpoints/pbx/freepbx/feature-codes/)

<hr />

## Troubleshooting

### The light for my HOIP extension is not green (orange, ameber, yellow) and I have not changed anything on my end. What has happened or what do I do?

!!! note ""
    This is becoming a common issue on the service we are finding. This could be a Carrier Grade NAT situation. We might have to make some adjustments on the peer for your extension. 

    Some steps to take first (in order):

    * Reboot your modem
    * Reboot your router
    * Reboot your phone

    If these do not fix the issue, you will need to open a ticket to the helpdesk. We will need to make some adjustments. 

    In the ticket, please include he following information:

    * Your name, callsign
    * Your extension
    * Mention the fact that our light is orange
    * Include your IP Address

    To get your IP address, please go to [https://pb.hamsoverip.com/diy](https://pb.hamsoverip.com/diy) and copy and paste the IP address that is shown there into the ticket. 

    This will allow the admins to make the adjustments needed and then they will get back to you about the fix being implemented.

<hr />

## Phones

### What phones work with HOIP?

!!! note ""
    The nice thing about the Hams Over IP service is we are a BOYD (Bring Your Own Device) service. So any phone that you can configure for SIP connections can be used on the service, on any peer. We have people that use Cisco, Grandstream, Polycomm, Yealink, Fanvil, Softphones and many other types of phones. 

    As long as you can configure the phone to use SIP, you are good to go.

### How do I configure X phone to work with HOIP?

!!! note ""
    Take a look through the Configuration Guides in the Wiki and see if your phone has a configuration guide. If not, you can ask on any of our [chat services](https://hamsoverip.github.io/wiki/General/user_guides/chat-services/) to see if someone has configured it. 

    If there is not a configuration guide, you are also welcome to contribute to the Wiki and add a guide for your phone. That would help out others. To see how to contribute, look at the [Contributing Guide](https://hamsoverip.github.io/wiki/wiki/overview/).

### I had to reprovision my phone or factory reset my phone and I cannot find/lost my credientals. What do I do?

!!! note ""
    If you can't find your credentials, you can put a ticket into the [Helpdesk Ticketing](https://helpdesk.hamsoverip.com/osticket/) system and request your credentials be resent to you.


### I had to reprovision my phone (with HH) and now HOIP will not work. How do I fix this?

!!! note ""
    Hamshack Hotline provisions certain phones from their servers and take over line 1 of the phone. When a user needs to reprovision since HH does not care if other services could be running on the phone, there are alot of settings problems that are induced to the phone by them, which causes problems for end users.

    For those of you that have reprovisioned your phone due to Hamshack Hotline or a factory reset and then reprovisioning Hamshack Hotline to fix these issues and be able to use other services:

    * Goto your HOIP extension tab and change TCP to UDP.
    * In the ```SYSTEM``` tab, please fill in 
        * ```PRIMARY DNS``` with 8.8.8.8
        * ```SECONDARY DNS``` to 8.8.4.4
        * or you can use DNS servers of your choice (for example if you run a DNS source on your home network like Pi-Hole or if you don't want to use the Google servers above).  
    * Make sure you have your HOIP extension configured with the proper credentials.
    * Submit changes and reboot.

### How do I access my Voicemail?

!!!note ""
    Dial ```*97``` from your phone or hit the voicemail button. This will drop you into your mailbox. If this is the first time accessing your mailbox, the system will walk you through setting up your outgoing voicemail messages and make you change your pin. Once you have all this setup, all you need to do is dial ```*97``` from your phone, or hit the voicemail button and it will just drop you into your box to let you retreive messages.

<hr />

## PBXs

### What PBXs work with HOIP?

!!! note ""
    Good Question. As of right now, we know that FreePBX and 3CX both work with the service. Both can connect via SIP Trunks and FreePBX is able to use IAX. But otherwise, we don't really know of more. If you know of others that use SIP Trunks and can configure them, we would like to know more about it. In fact, if you can create a configuration guide, please submit it. 

    If you want to use FreePBX or 3CX, please check out the configuration guides for each here in the Wiki.


### How do I configure my PBX to work with HOIP?

!!! note ""
    Good question! If it's one we have a guide for, check out the configuration guides for the PBXs. If it's one that we don't have a guide for, please write one up and submit it. 

<hr />

## Website/Ticket System

### I am a new user and just created an account in OS Ticket, but I am not able to log in.

!!! note ""
    Chances are pretty good the verification email from the system was sent to your spam folder. There are some email providers that either block or mark the emails as spam. Check your spam folder. If it's not there, it might have been blocked. Reach out to an admin on Discord and see if they can activate your account. Once that is done, you should be able to log in and see your tickets.

### I put a ticket in to get a new extension, but I have not gotten my credentials email?

!!! note ""
    This could be a couple of things:
   
    * Remember we are all volunteers. We try to get to tickets as quick as we can, but we also have lives outside of this project. So it could take a day or two before we can get to the ticket
    * Possibly the same reason as above. Your email provider spam foldered it or blocked it. Again, reach out to an admin on Discord and they can DM you your credentials.