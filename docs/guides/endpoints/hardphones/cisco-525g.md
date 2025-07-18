# Cisco SPA-525

![Picture of SPA525](https://user-images.githubusercontent.com/65520146/174688561-4787f8ae-8d77-4bae-9228-1fbd294a23a6.png)

The Cisco SPA525G 5-line IP Phone with Color Display is a full-featured VoIP (Voice over Internet Protocol) phone that provide voice communication over an IP network. It provides traditional features, such as call forwarding, redialing, speed dialing, transferring calls, conference calling, and accessing voice mail. Calls can be made or received with a handset, headset or speaker.

Your Cisco IP Phone provides a web interface for the phone user that allows you to configure some features of your phone by using a web browser.

This article will guide you through the steps for basic configuration to make it work with HOIP

## Step 1

**Get the IP address of your phone**:

a. Press `Setup`.

b. Select to `Status` > `Network Status`.

c. Scroll to view IP Address. This is the IP address of your phone.

This should show your IP Address in the format of xxx.xxx.xxx.xxx (EX: 192.168.0.2)

## Step 2

**Logging in to the Phone Web User Interface**:

* On your PC, open a Web browser window. Your PC must be on the same subnetwork as the phone.
* Enter the IP address in the browser address bar.
  * This is the IP address you obtained above

You will now see this screen:
![Top menu Bar of Cisco SPA525](https://user-images.githubusercontent.com/65520146/174688789-60893e08-7f8d-4e08-9691-ab2cad8105e7.png)

Click on the `Admin Login` button near the top right side of the screen, then click on the `Ext 1` tab. This could be `Ext 2` if you already have a current extenstion.

![Admin Menu Bar](https://user-images.githubusercontent.com/65520146/174689423-1052c960-17d2-4505-a134-7b06f9099991.png)

## Step 3

**Configure with your Hams over IP account**:

Find the following fields on the `Ext` tab and configure accordingly.

**Nat Keep Alive**: Yes

**Nat Mapping/Traversal**: Yes

**Proxy**: This will be the domain name sent in your credentials email (ex: `pbx-us1.hamsoverip.com:5160`)

**Register Expires**: 3600

**User ID**: Enter your Extension from the credentials email.

**Password**: Enter your password from the credentials email.

**Use DNS SRV**: NO

**DNS SRV Auto Prefix**: NO

![Extenstion Part 1](https://user-images.githubusercontent.com/65520146/174689828-8d9bbc16-08a3-4f0c-903c-d59fd9e7b0c1.png)
![Extenstion Part 2](https://user-images.githubusercontent.com/65520146/174689834-822579c8-d276-41db-aebc-496cfc401797.png)

Written by Jeff N8EMA

Last Updated: 2024-06-01 Dave M7TLB
