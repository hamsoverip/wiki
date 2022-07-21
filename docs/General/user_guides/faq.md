# Frequently Asked Questions

Last Updated: 07/21/2022

This document is a place to put some of the more Frequently Asked Questions of the service that are quick, short answers. If an answer requires more indepth steps, a guide will be created in the Troubleshooting section and linked to from this document.

This is a long document, so to the right side of this page is a Table of Contents that will link you to the sections and within each section is a smaller Table of Contents that will like you to the question you have and the answer. You can also do a search by doing ```Ctrl``` + ```F``` on Windows and Linux or ```Cmd``` + ```F``` on Mac.

<hr />

## General

* How do I get started?
* Where can I go for more help?
* Can I contribute to the Wiki?

<hr />

## Phones

* What phones work with HOIP?
* How do I configure X phone to work with HOIP?
* I had to reprovision my phone or factory reset my phone and I cannot find/lost my credientals. What do I do?
* I had to reprovision my phone (with HH) and now HOIP (or other services) will not work. How do I fix this?

### What phones work with HOIP?

!!! note ""
    The nice thing about the Hams Over IP service is we are a BOYD (Bring Your Own Device) service. So any phone that you can configure for SIP connections can be used on the service, on any peer. We have people that use Cisco, Grandstream, Polycomm, Yealink, Fanvil, Softphones and many other types of phones. 

    As long as you can configure the phone to use SIP, you are good to go.

### How do I configure X phone to work with HOIP?

Take a look through the Configuration Guides in the Wiki and see if your phone has a configuration guide. If not, you can ask on any of our [chat services](https://hamsoverip.github.io/wiki/General/user_guides/chat-services/) to see if someone has configured it. 

If there is not a configuration guide, you are also welcome to contribute to the Wiki and add a guide for your phone. That would help out others. To see how to contribute, look at the [Contributing Guide](https://hamsoverip.github.io/wiki/wiki/overview/).

### I had to reprovision my phone or factory reset my phone and I cannot find/lost my credientals. What do I do?

If you can't find your credentials, you can put a ticket into the [Helpdesk Ticketing](https://helpdesk.hamsoverip.com/osticket/) system and request your credentials be resent to you.


### I had to reprovision my phone (with HH) and now HOIP will not work. How do I fix this?
Hamshack Hotline provisions certain phones from their servers and take over line 1 of the phone. When a user needs to reprovision since HH does not care if other services could be running on the phone, there are alot of settings problems that are induced to the phone by them, which causes problems for end users.

For those of you that have reprovisioned your phone due to Hamshack Hotline or a factory reset and then reprovisioning Hamshack Hotline to fix these issues and be able to use other services:

* Goto your HOIP extension tab and change TCP to UDP.
* In the ```SYSTEM``` tab, please fill in 
    * ```PRIMARY DNS``` with 8.8.8.8
    * ```SECONDARY DNS``` to 8.8.4.4
    * or you can use DNS servers of your choice (for example if you run a DNS source on your home network like Pi-Hole or if you don't want to use the Google servers above).  
* Make sure you have your HOIP extension configured with the proper credentials.
* Submit changes and reboot.

<hr />

## PBXs

* What PBXs work with HOIP?
* How do I configure my PBX to work with HOIP?


<hr />

## Website/Ticket System

* I am a new user and just created an account in OS Ticket, but I am not able to log in.
* I put a ticket in to get a new extension, but I have not gotten my credentials?