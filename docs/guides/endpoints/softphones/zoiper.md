# Configuring Zoiper for HOIP

Zoiper is a free SIP client solution that is available for all platforms.

While the Zoiper Mobile App will work with the service, we do not really recommend using it unless you are willing to accept it's short comings.

Unless you are using the Paid version of the software, Zoiper does not do a keep alive to keep your connection active.

However, the desktop clients do not have that problem. As long as the application is running, it will remain connected to your extension.

Zoiper is available for download from: [https://www.zoiper.com/](https://www.zoiper.com/)

## Configuring

!!! tip "Configure Zoiper on..."

    === "Desktop app"

        First you will need to download and install the desktop version of the application for whatever platform you want to use it on.

        Once that is done, open the application. The first thing you should see is a splash screen asking if you want to `Activate your PRO License`. You do not. At the very bottom of that splash screen should be a link that says `Continue as a Free User`. That is what we want to do, so click that.

        On the next screen it should show 2 fields (in this order):

        * `Username/Login`: This will be your extension from the credentials email that you rececived.
        * `Password`: This will be your extension password from the crednetials email that you received.

        Fill those in and click `Login`

        On the next screen you will be asked for:

        `Hostname`: This will be the domain name and port from the credentials email that you received. (ex: `pbx-us1.hamsoverip.com:5160`)

        Fill that in and click next. On the next screen it will ask you for an outbound proxy. This is not needed so click `Skip`.

        On the next screen it will check all the protocols and encryption types. It should find `SIP UDP` and that bar should go green. Once it does, click `Next`.

        Next it will ask you to configure your speakers/mic/video camera. You can go through this or you can skip it if you want.

        Finally we are to the main screen. You should see at the top of the window a SIP Address and a green check mark. This means you are connected to your extension.

        ### Making Calls (Desktop)

        To make a call, click on the find a contact search field and enter the extension you wish to call. You can also hit the icon of a dial pad next to that field and use your mouse to click the buttons to dial the number as well.

        ### Receiving Calls (Desktop)

        To receive a call, you will need to have the application open. It can be minimized, but it needs to be running to accpet incoming calls.

        ### Adding Contacts (Desktop)

        The Desktop version of Zoiper does allow you to enter and save your own contacts.

        To add a contact, click the plus button and fill in the information in the fields.

    === "Mobile app"

        To configure the mobile app, you will need to download and install the app from the appropriate App Store.

        Once that is done, open the app. It will ask you for permissions to access varous aspects of your mobile device like Microphone and contacts. Give permissions as you see fit.

        Once that is done, you should be on the main screen. This should have a large dial pad int he middle of the screen and a large green call button in the middle. At the bottom should be some icons. The last icon to the right should be a gear icon marked `Settings`. Tap that.

        This should bring you to the Settings Screen.

        * Tap `Accounts`
        * Tap the `+` plus sign in the upper right corner to add a new account.

            * It will ask you `Do you already have an account (username and password)?` tap `Yes`

        * Tap `Manual Configuration`
        * Tap `SIP Account`
        * Fill in the following:

            * `Account Name`: This is what you want to call the account. This can be anything, it is just a place holder to show the name of the account you are using. Suggested using your Extension Number.
            * `Domain`: This is the domain and port number of the server sent to you in the crednetials email you received.
                * Example: `pbx-us1.hamsoverip.com:5160`
            * `Username`: This is the extension in your credentials email.
            * `Password`: This is the password in your crednetials email.
            * The rest of the fields/settings can be left at default.

        * Tap `Register`

        Once the registration process is completed, it should show `Registration Status: OK` across the top. This means that you are connected to your extension on the server.

        Go back to the dialpad screen. You should see the name of the account and a little `Ready` in green. This indicates that you are registered on the server.

        ### Making Calls (Mobile)

        On the dial pad screen tap out the number you wish to call and tap the big green ```Call``` button. You should dial out and make a connection.

        ### Receiving Calls (Mobile)

        To receive a call, you will need to have the app open on your device.

        ### Adding Contacts (Mobile)

        Zoiper will need access to your devices address book to allow you to add contacts or be able to view contacts.

## Troubleshooting

!!! warning "Troubleshooting"

    * If the mobile app says registration failed or the green check mark is not on the desktop app, this indicates that the account is not registered on the server. Try turning off your home wifi on your phone and letting it connect via cellular. If it connects, it's an issue with your home wifi. If it does not register, it is a configuration error.
    * If you are having a configuration problem, double check your settings on the account screen. Make sure if you copy and pasted there are no spaces in the username or password or anything. This will cause a registration issue.
    * If you have tried all the above and it still won't connect over your home wifi (but it will over Cellular) AND this is your only phone (IE no hardline phone), then you might have a CGNAT problem. Please see this part of the [FAQ Document](../../../guides/faq.md#the-light-for-my-hoip-extension-is-not-green-its-orange-amber-yellow-and-i-have-not-changed-anything-on-my-end-what-has-happened-or-what-do-i-do).

----

!!! info "Last Updated 2022-02-09"
