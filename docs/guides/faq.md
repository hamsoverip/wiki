---
icon: material/frequently-asked-questions
---

# Frequently Asked Questions

This document is a place to put some of the more Frequently Asked Questions of the service that are quick, short answers. If an answer requires more indepth steps, a guide will be created and linked to from this document.

This is a long document, so to the right side of this page is a Table of Contents that will link you to the sections and within each section is a smaller Table of Contents that will link you to the question you have and the answer. You can also do a search by doing `Ctrl` + `F` on Windows and Linux or `Cmd` + `F` on Mac.

----

## General

### How do I get started?

!!! note ""
    First you will need to get a phone. As long as your phone will allow or handle SIP, you are good to go.

    Then check out our [Getting Started Guide](./user/getting-started.md) to start the process.

    You can also look through the rest of the Wiki to get an idea on how to get started.

### Where can I go for more help?

!!! note ""
    You are already in the best place for getting more help! This Wiki. This is where alot of guides and information can be found about the service and things are added all the time.

    Next place you can go is one of our [Chat Services](./user/chat-services.md). Our main form of communication is Discord, but some other chat services are bridged into it. 

### Can I contribute to the Wiki?

!!! note ""
    Absolutely! We encourage our user community to contribute to the Wiki to help expand the knowledge here. To see how, check out our [Contributing Guide](../wiki/contributing.md)

### What Feature Codes can I use on the system?

!!! note ""
    All Feature Codes can be found in the [Feature Codes Guide](../guides/features/pbx-feature-codes.md)

----

## Troubleshooting

### The light for my HOIP extension is not green (its orange, amber, yellow) and I have not changed anything on my end

!!! note ""
    This is becoming a common issue on the service we are finding.

    The first thing to try is our [Troubleshooting Guide](./troubleshooting.md).  This will take you through some steps to try and resolve the issue.

    If the Troubleshooter doesn't work for you, then this could be a Carrier Grade NAT situation, where we might have to make some adjustments on the server for your extension.

    Head over to the [Helpdesk :material-open-in-new:](https://helpdesk.hamsoverip.com/osticket/){ target="_blank" } and create a new "Report a Problem" ticket.  Please include - a minimum - the following information:

    * Your name and callsign
    * Your extension number
    * Mention the fact that your light is orange
    * If you went through the troubleshooter, please mention this as well
    * Include your IP Address (which you can get from [here :material-open-in-new:](https://helpdesk.hamsoverip.com/diy){ target="_blank" }
    * Also, if you have a Dynamic DNS Service (DDNS) like DuckDNS or No-IP or similar, please provide us your dynamic hostname as this means we don't have to keep updating your IP address every time it gets blocked. Do a search for Dynamic DNS Services online.  If you're running an Allstar node on the same network as your phone, you already have a Dynamic DNS hostname thanks to allstarlink.org.
    
    This will allow the admins to make the adjustments needed and then they will get back to you about the fix being implemented.

### My phone is provisioned but I don't hear any audio after the dial tone when I check my voicemail or make any calls

!!! note ""
    Check the audio settings of the phone. Make sure the volume is turned up and there are no loose connections. If the phone checks out physically, check to see if the phone is behind a firewall. If it is the following ports need to be opened outbound only. (Keep in mind this is NOT port forwarding, just simply allowing the phone to initiate a connection on these ports)

    * SIP Ports UDP - 5160
    * DNS Ports UDP - 53
    * NTP Ports UDP - 123
    * RTP Ports UDP - 10000 through 15000  NOTE: RTP port can vary on what is set for your device to use.

----

## Phones

### What phones work with HOIP?

!!! note ""
    The nice thing about Hams Over IP is that we are a BOYD (Bring Your Own Device) service. So any phone that you can configure for SIP connections can be used on the service. We have people that use Cisco, Grandstream, Polycom, Yealink, Fanvil, softphones and many more.

    As long as you can configure the phone to use SIP, you are good to go.

### How do I configure X phone to work with HOIP?

!!! note ""
    Take a look through the [Configuration Guides](./index.md) in the Wiki and see if there is one available for your device. If not, you can ask on any of our [chat services](./user/chat-services.md) to see if someone else has configured it.

    If there isn't a Configuration Guide available, you are also welcome to contribute to the Wiki and add a guide for your phone. That would help out others.  To see how to contribute, look at our [Contributing Guide](../wiki/contributing.md).

### I had to reprovision my phone or factory reset my phone and I cannot find/lost my credentials

!!! note ""
    If you can't find your credentials, you can put a "General Enquiry" ticket into the [Helpdesk :material-open-in-new:](https://helpdesk.hamsoverip.com/osticket/) system and request your credentials be resent to you.

### How do I access my Voicemail?

!!! note ""
    Dial `*97` from your phone or hit the voicemail button. This will drop you into your mailbox. If this is the first time accessing your mailbox, the system will walk you through setting up your outgoing voicemail messages and make you change your pin. Once you have all this setup, all you need to do is dial `*97` from your phone, or hit the voicemail button and it will just drop you into your voicemailbox to let you retrieve messages.

----

## PBXs

### What PBXs work with HOIP?

!!! note ""
    Good Question. As of right now, we know that FreePBX and 3CX both work with the service. Both can connect via SIP Trunks and FreePBX is able to use IAX. But otherwise, we don't really know of more.  If you know of others that use SIP Trunks and can configure them, we would like to know more about it. In fact, if you can create a configuration guide, please submit it.

    If you want to use FreePBX or 3CX, please check out the configuration guides for each here in the Wiki.

### How do I configure my PBX to work with HOIP?

!!! note ""
    Good question! If it's one we have a guide for, check out the [Configuration Guides for PBXes](./pbx/index.md).

    If there isn't a Configuration Guide available, you are also welcome to contribute to the Wiki and add a guide for your PBX.  To see how to contribute, look at our [Contributing Guide](../wiki/contributing.md).
----

## Website/Ticket System

### I am a new user and just created an account in OS Ticket, but I am not able to log in

!!! note ""
    Chances are pretty good the verification email from the system was sent to your spam folder. There are some email providers that either block or mark the emails as spam. Check your spam folder. If it's not there, it might have been blocked. Reach out to an admin on Discord and see if they can activate your account. Once that is done, you should be able to log in and see your tickets.

### I put a ticket in to get a new extension, but I have not gotten my credentials email?

!!! note ""
    This could be a couple of things:

    * Remember we are all volunteers. We try to get to tickets as quick as we can, but we also have lives outside of this project. So it could take a day or two before we can get to the ticket
    * Possibly the same reason as above. Your email provider spam foldered it or blocked it. Again, reach out to an admin on Discord and they can DM you your credentials.

----

!!! info "Last updated 2025-07-29 Dave M7TLB"
