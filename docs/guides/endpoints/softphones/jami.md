# Configuring Jami SIP Client for HOIP

Jami is a Free and Open Source (FOSS) solution for a SIP client. They do provide their own IM/calling service, but this is not required to make this application work. This client is able to connect directly to a SIP provider without a Jami Login.

The client is designed as an IM client for business first with calling capablity added later. This will be something to keep in mind when using the client. As such, there is no actual keypad on the screen at first. Once a call is established, there is the option to open a keypad for entering DTMF commands for Voicemail and other things.

There is not a way to add contacts to the application either.

The client is available for all major desktop platforms (Windows, MacOS and Linux) as well as all iOS and Android. (Note that for MacOS, it is also available in the MacOS App Store in addition to being a direct download.)

Each Platform requires slightly different ways to set up, but for the most part, all the things you will need to change will be pretty easy to find and configure.

Jami is available for download from: [https://jami.net/download/](https://jami.net/download/)

## Configuring

!!! tip "Configure Jami on..."

    === "Desktop app"

        **Configuring**

        **Note:** You do not need to setup a Jami account for this to work. DO NOT USE THAT METHOD. This Client will connect directly to a SIP provider.

        First you will need to download and install the client to your desktop platform (How that is done varies from platform to platform and is outside the scope of this document). Once it is installed, open the application.

        * When the initial screen comes up asking if you want to `Join Jami` or `I already have an Existing Account` don't choose either. Look for the option marked `Advanced Features` and click that and then click the option that says `Configure a SIP Account`.
        * Enter the information for the fields on the next screen (the configuration screen is a bit wonky, but the fields listed below are the fields as they appear. Make sure to select the correct fields to put information into):
        
            * `Server`: This will be the domain name and port sent in your credentials email (ex: `pbx-us1.hamsoverip.com:5160`)
            * `Proxy`: LEAVE THIS BLANK
            * `Username`: This is your extension sent in your credentials email.
            * `Password`: This is your password sent in your credentials email.

        * Click `Add SIP Account`
        * You're done. You should have a little circle icon in the upper left with a green dot on it. This indicates the account is connected.

        **Making a Call**

        This is where the app is a little lacking, but for a quick easy SIP client, this is still ok. Remember that this client was designed as an IM client first, with the ability to make and receive calls.

        To make a call, you will need to click on the field marked `Find a User or search for a conversation` and then type in the extension you want to call and then click on it in the search results. 

        Once this has been done, to the right an IM window will appear and in the top right hand corner, you will see what looks like the handset for a phone. Click that. The Client will start dialing.

        Once the call has been connected, you will be able to click on a keypad icon in the Ongoing Call window and bring it up. This will allow you to enter commands.

        **Receiving a Call**

        When a call comes into the extension, you will be presented with a screen that will allow you to accept or decline the call.

    === "Mobile app"

        **Configuring**

        Unfortuantely, it is not as easy to configure this for mobile and there are a couple of hoops you need to jump through.

        After installing the app from the appropriate app store, open the app.

        * You will be presented with a new account screen. Unfortuantly, you will need to create a Jami account for this part, however, it is only nessesary to be able to setup the app at first and then add a SIP account. 
        * Tap on `Create Jami Account`
        * On the next screen, deselect the `Register Username` switch. This will cause the app to create an anonymous username. Leave everything else alone on this screen.
        * Tap `Create Jami Account`
        * On the next screen, tap the screen once and then next, leaving the Display name and Avatar blank.

        At this point you will now be on the main screen, just like on the Desktop Application. It is here we can now add a SIP account.

        * Tap where the random numbers and letters are at the top of the screen.
        * You should get a slide up with the option to `Add Account`. Tap that.
        * Here you should see the same screen that you saw at first, but it will now have the option to `Create a SIP Account`. Tap that.
        * Fill in the fields as below:

            * `Enter Username`: This is your extension from the credentials email
            * `Enter Password`: This is the password from the credentials email
            * `Enter Address`: This will be the domain name sent in your credentials email (ex: `pbx-us1.hamsoverip.com`)
            * `Enter Port`: This will be `5160`

        * Tap `Create SIP Account`
        * It will again ask you to choose a Display Name and Avatar. This does not effect the outbound calls, so you can skip this by tapping the screen and then clicking `Next`

        You are finally dropped into the application.

        **Making a Call**

        Unlike the desktop app, once you are in the main part of the app, there is a button that will allow you to place calls just like other SIP Clients. 

        To make a call, just tap the dialpad button and then dial the number like normal.

        **Receiving a Call**

        When a call comes into the extension, you will be presented with a screen that will allow you to accept or decline the call.

## Troubleshooting

!!! warning "Troubleshooting"

    * If the mobile app says registration failed or the green check mark is not on the desktop app, this indicates that the account is not registered on the server. Try turning off your home wifi on your phone and letting it connect via cellular. If it connects, it's an issue with your home wifi. If it does not register, it is a configuration error. 
    * If you are having a configuration problem, double check your settings on the account screen. Make sure if you copy and pasted there are no spaces in the username or password or anything. This will cause a registration issue.
    * If you have tried all the above and it still won't connect over your home wifi (but it will over Cellular) AND this is your only phone (IE no hardline phone), then you might have a CGNAT problem. Please see this part of the [FAQ Document](https://hamsoverip.github.io/wiki/General/user_guides/faq/#the-light-for-my-hoip-extension-is-not-green-its-orange-amber-yellow-and-i-have-not-changed-anything-on-my-end-what-has-happened-or-what-do-i-do).

----

!!! info "Last Updated 2022-09-02"
