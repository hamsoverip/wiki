# Configure Cisco 8800 Series for HOIP

The Cisco 8800 Series (including models 8811, 8841, 8851, 8861, etc.) are SIP-capable IP phones with color displays and Power over Ethernet (PoE) support. These phones are full-featured, supporting call forwarding, redial, speed dial, do not disturb, voicemail, and more. Calls can be made using the handset, speakerphone, or a headset.

You can often find these phones **relatively cheap on eBay**, but make sure you buy the correct version:

- Look for an **MPP model** (Model #: `CP-88XX-3PCC-K9`), which works directly with HOIP.
- If you buy an **Enterprise model** (Model #: `CP-88XX-K9`), you will need to convert it to MPP by flashing MPP firmware and purchasing a Cisco migration license (around **$42–$65**).

This guide assumes you have an MPP (3PCC) model or an Enterprise model successfully converted to MPP firmware.

---

## Obtain the IP Address of the Phone

After powering up and connecting the phone to your network:

- Press the **Settings** button.
- Navigate to **Status → Network Status → IPv4 status**.
- Note the IP address (e.g., `192.168.1.150`) for use in the next step.

---

## Log into the Web Interface

- Open a web browser on a computer connected to the same network.
- Enter the phone’s IP address in the address bar.
- When logging in for the first time, it may prompt you to create a Admin password and a User Password. If you chose to create a password, be sure to remember them as you will need them in the future when accessing this page, and for certain actions on your 8800 Series phone.
- Once logged in, click **Admin Login** and switch to **Advanced**, both which can be found at the top right of your dashboard.

---

## Configure Your Extension for HOIP

- Click on the **Ext 1** tab (or another free extension tab if Ext 1 is in use).
- Set the following fields:

  - General
    - Set `Line Enabled`: `yes`
  - NAT Settings
    - Set `NAT Mapping Enable`: `yes`
    - Set `NAT Keep Alive Enable`: `yes`
  - SIP Settings
    - Set `SIP Transport`: `UDP`
  - Proxy and Registration
    - Set `Proxy`: domain and port from your HOIP credentials email  
        - Example: `pbx-us1.hamsoverip.com:5160`
    - Set `Register Expires`: `3600`
  - Subscriber Information
    - Set `Display Name`: Your callsign or HOIP extension
        - Example: `W2DIY Daniel`
    - Set `User ID`: Your HOIP extension number
    - Set `Password`: Password from your HOIP credentials email

Leave all other settings as default and click **Submit All Changes**.  

The phone will reboot *or* refresh, and the configured line should display as **registered (green)**.

---

## Make a Test Call

To confirm your setup:

- Pick up the handset or press the speaker button.
- Dial `3192` (HOIP talking clock) to verify connection.
  - If you have setup everything correctly, it should read you the date & time and then hang up

---

## [EXTRA] Setup the Voicemail Button

HOIP normally suggests using `*97` to check your voicemail. On many softphones or ATAs, `*97` automatically logs into the mailbox of the device that placed the call.  

However, on the Cisco 8800 series, `*97` is treated as a generic feature code and does **not** send your extension automatically. As a result, the system will prompt you to “enter pick up number,” which is not the desired behavior.

There are two methods around this. One is simple, and the other one took me 45 minutes to figure out before I found the simple method.

### Method 1 [SIMPLE]

- Navigate to **Voice → Regional**
- Locate `Vertical Service Activation Codes`
- Set `Call Pickup Code` : `(blank)` or a different extention that doesn't conflict
- Click **Submit All Changes**

Once configured, pressing the voicemail button will:

1. Dial `*97`  
2. Connect you directly to your voicemail

### Method 2 [COMPLICATED (BUT WORKS)]

Instead, you should use `*98`. When you dial `*98`, the HOIP server asks you to **enter your extension number** and then your voicemail password. By default, this requires two steps every time you access voicemail.

If you are okay with entering your extension number and voicemail password everytime, then you can do the following:

- Navigate to **Voice → Phone**
- Set `Voice Mail Number` : `*98`
- Click **Submit All Changes**

If you would like to automatically have your extension number and voicemail password entered when you click the voicemail button, continue reading.

### Automating Extension Entry with a Dial String

The Cisco 8800 series allows you to embed DTMF tones and pauses into the voicemail dial string so that your extension is sent automatically. This means you won't need to enter your extension number or voicemail password everytime.

You can insert a short pause using the `p` character (each `p` is roughly 0.5–1 second), and in this case, **you must include a space between the two p’s** to ensure the pause is recognized correctly (based on my quick testing).

#### Example Dial String

`*98p p102290#p p123456#`

- `*98` → Connects to the HOIP voicemail system  
- `p p` → Inserts a delay before sending your extension  
- `102290#` → Sends your extension followed by `#`  
- `p p` → Inserts a delay before sending your password
- `123456#` → Sends your voicemail password followed by `#`

Once configured, pressing the voicemail button will:

1. Dial `*98`  
2. Pause briefly  
3. Send your extension & voicemail password automatically
4. Connect you directly to your voicemail

Note: If you prefer to enter your password manually, remove everything after the first `#`:

- Example: `*98p p102290#` will only send my extension, and then I will be prompted to enter my password followed by `#`

---

## [EXTRA] Set the Date and Time Automatically

To keep the phone’s time accurate:

- Click the **System** tab.
- Under Optional Network Configuration:
  - `Primary NTP Server`: `pool.ntp.org`
- Click the **Regional** tab.
- Set:
  - `Time Zone`: Your local offset (e.g., `GMT-05:00` for New York)
  - `Daylight Saving Time Enable`: `yes`
- Click **Submit All Changes** and reboot.

---

## [EXTRA] Custom Background and Logo (Optional)

The 8800 Series supports custom backgrounds:

- Host your PNG (recommended) or JPG file on an HTTP server.
- In **Voice → User**, scroll all the way to the bottom:
  - `Background Image`: `http://your-server-ip/W2DIY_8851.png`
- Click **Submit All Changes** and reboot.

For best results, use the phone’s native screen resolution (e.g., `800x480` for the 8851).

---

## Final Notes

Once configured, the Cisco 8800 Series works perfectly with HOIP.  

For anyone who is **migrating** an Enterprise phone to MPP:

- The activation code prompt you may see after migration is **only for Cisco Webex Calling** — you can ignore it for HOIP or other SIP services. After following this guide, if you get a popup saying you need to activate a license, you must purchase one from a Cisco partnered retailer.

!!! quote "Author's note (Daniel, W2DIY)"
    I ran into a TON of issues trying to get my HOIP setup after I was sent an Enterprise version of the Cisco 8851 instead of the MPP version. It was a lot of learning for me, but that's what the hobby is all about! If you run into a similar situation and need some guidence, feel free to email me at [:material-email: daniel@w2diy.com](mailto:daniel@w2diy.com) and I will gladly do my best to help you get past the same hurdles I had to go through! 73!

!!! note "Written by Daniel W2DIY,  last updated 2025-07-31"
