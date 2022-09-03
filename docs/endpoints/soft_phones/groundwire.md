# Configuring Groundwire SIP Client for HOIP

Groundwire is the recommended softphone application for HOIP on cellphones and tablets. It is a one time cost of approxamatly $10 Dollars, but it is well worth that cost.

Groundwire has the ability to keep your connection alive to the servers and also push notifications of an incoming call to the user. And it is not bad on battery life either.

Groundwire is available for iOS and Android platforms at the following links:

* Apple/iOS: [App Store](https://itunes.apple.com/us/app/acrobits-groundwire/id378503081?mt=8)
* Android: [Google Play Store](https://play.google.com/store/apps/details?id=cz.acrobits.softphone.aliengroundwire&hl=en_US&gl=US)

## Configuration Steps

* First download the client from the appropriate App Store.
* Once it is downloaded, open it on your device. It will either open right to the settings screen or to the quickdial tab. If it is not on the settings screen, click the gear in the upper right hand corner of the screen.
* On the Settings screen, tap the ```Accounts``` Option and then click the ```+``` in the upper right hand corner top add a new account.
* On the next screen, select the ```Generic SIP Account``` Option.
* You should now be on the ```New Account``` Screen. Here is where you will configure the account to connect to HOIP. You will need to enter the following in the fields:
    * ```Title``` - This is the name of the account you are setting up. Suggested is your extension number (the actual extension) on HOIP.
    * ```Username``` - This is the (actual) extension number of your account.
    * ```Password``` - This is the password sent in your user credentials email from the HOIP system.
    * ```Domain``` - This is the ```domain:port``` of the server you are getting an account on. This will be in the email you received from the HOIP system. An example would be ```pbx-us1.hamsoverip.com:5160```.
    * ```Display Name``` - This is optional, but this would be the name you would want displayed on the other end.
* Once you have all of these set, Tap ```Save```.
* Then tap ```Settings``` in the upper left corner.
* Finally tap ```Done``` in the upper right corner.

You should now be back at the main screen. In the upper left, there should be a dashed green circle around the Extension number. After a few seconds, it should become solid green. This indicates that the account is registered on the server.

## Configure Push Notifications

* On the main settings screen, tap ```Incoming Calls```
* Then tap ```Push Notifications``` at the top of the screen.

This sets up Push Notifications for Groundwire.

## Configure Voicemail

This one is a bit tricky. It doesn't make sense on why all these switches are in different places, but here goes.

* Click the gear in the upper right hand corner of the screen.
* Tap ```Preferences```
* Tap ```Controls```
* Scroll down till you see ```Always show Voicemail button``` and enable that switch.
* Hit ```Done```
* Go back into the ```Settings``` Gear.
* Tap ```Accounts```.
* Tap the little blue ```information``` circle next to the account you want to edit.
* Tap ```Advanced Settings```
* Scroll down to ```Voicemail Number``` and enter \*97 there.
* Tap ```Done```
* Tap ```Settings``` and then Tap ```Done``` and this will bring you back to the main dial screen.
* You should now have a blue voicemail button at the bottom of your dial pad screen. If you tap this, it will dial your voicemail box and let you retreieve voicemails.

## Troubleshooting

* If the circle goes red, this indicates that the account is not registered on the server. Try turning off your home wifi on your phone and letting it connect via cellular. If it connects, it's an issue with your home wifi. If it does not register, it is a configuration error. 
* If you are having a configuration problem, double check your settings on the account screen. Make sure if you copy and pasted there are no spaces in the username or password or anything. This will cause a registration issue.
* If you have tried all the above and it still won't connect over your home wifi (but it will over Cellular) AND this is your only phone (IE no hardline phone), then you might have a CGNAT problem. Please see this part of the [FAQ Document](https://hamsoverip.github.io/wiki/General/user_guides/faq/#the-light-for-my-hoip-extension-is-not-green-its-orange-amber-yellow-and-i-have-not-changed-anything-on-my-end-what-has-happened-or-what-do-i-do).
  
Last Updated: 09/02/2022