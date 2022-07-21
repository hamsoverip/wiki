# Fixing Issues Induced by Hamshack Hotline

Hamshack Hotline provisions certain phones from their servers and take over line 1 of the phone. When a user needs to reprovision since HH does not care if other services could be running on the phone, there are alot of settings problems that are induced to the phone by them, which causes problems for end users.

For those of you that have reprovisioned your phone due to Hamshack Hotline or a factory reset and then reprovisioning Hamshack Hotline to fix these issues and be able to use other services:

* Goto your HOIP extension tab and change TCP to UDP.
* In the ```SYSTEM``` tab, please fill in 
    * ```PRIMARY DNS``` with 8.8.8.8
    * ```SECONDARY DNS``` to 8.8.4.4
    * or you can use DNS servers of your choice (for example if you run a DNS source on your home network like Pi-Hole or if you don't want to use the Google servers above).  
* Make sure you have your HOIP extension configured with the proper credentials.
* Submit changes and reboot.

Last Updated: 07/20/2022