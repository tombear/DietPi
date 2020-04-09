# DietPi
DietPi scripts that I've hacked together for various purposes

## dietpi-setup | `Configure Raspberry Pi DietPi microSD card for Roon`

The goal with this script is to enable a Roon subscriber to easily transform a standard Raspberry Pi into a network audio transport that can drive a USB DAC. This allows any USB DAC to show up on your home network as a Roon Output. DietPi makes this super easy to do, but some folks struggle with getting Wi-Fi and the audio settings configured, so I wrote this script to simplify the process.

Here's an example of what running it looks like on macOS after flashing a fresh microSD card with the latest Raspberry Pi DietPi image using etcher:

```
$ cd /Volumes/boot/
$ curl -Lo dietpi-setup ws-e.com/dietpi-setup
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   295  100   295    0     0   1710      0 --:--:-- --:--:-- --:--:--  1705
100  6209  100  6209    0     0  12314      0 --:--:-- --:--:-- --:--:-- 12314
$ perl ./dietpi-setup

---------------------------------------------------------
-  This will edit dietpi.txt for your home network.
-  At each prompt below, type the information requested
   and then hit [enter] or [return].

- Name your RPi (only letters, numbers and dashes): roon-usb
- Do you have a wifi network? (y/n) : y
- Your wifi SSID: Audiophiles
- Your wifi password: **********

- Settings updated in dietpi.txt:
       CONFIG_BOOT_WAIT_FOR_NETWORK = 2
                   CONFIG_SOUNDCARD = usb-dac
               AUTO_SETUP_AUTOMATED = 1
         AUTO_SETUP_KEYBOARD_LAYOUT = us
                  AUTO_SETUP_LOCALE = en_US.UTF-8
         CONFIG_CHECK_CONNECTION_IP = 8.8.8.8
         CONFIG_G_CHECK_URL_TIMEOUT = 2000
            AUTO_SETUP_NET_HOSTNAME = roon-usb
                AUTO_SETUP_TIMEZONE = America/Los_Angeles
            CONFIG_CHECK_DNS_DOMAIN = google.com
       CONFIG_SERIAL_CONSOLE_ENABLE = 0
     AUTO_SETUP_INSTALL_SOFTWARE_ID = 5,121
        AUTO_SETUP_NET_WIFI_ENABLED = 1
           CONFIG_WIFI_COUNTRY_CODE = US
    AUTO_SETUP_NET_ETHERNET_ENABLED = 0
- Updates to dietpi.txt saved.

- Settings updated in dietpi-wifi.txt:
                           WIFI_KEY = '**********'
                          WIFI_SSID = 'Audiophiles'
                        WIFI_KEYMGR = 'WPA-PSK'
- Updates to dietpi-wifi.txt saved.
```

After doing this, eject the microSD card, shove it into the Raspberry Pi, and add power. It's not necessary to attach a display to the Raspberry Pi, but if you did, this is an example of what you might see: https://youtu.be/8uOV4iBN4KM

Make sure that your USB DAC is connected to the Raspberry Pi and powered on. If all goes well, you should find your new output hiding under the Audio settings of Roon. Enable it and click on the gear to verify the settings. It will now show up in your list of output zones. Enjoy some music.
