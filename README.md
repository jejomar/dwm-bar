# dwm-bar
A modular statusbar for DWM
## Table of Contents
- [Features](#features)
- [Current Functions](#current-functions)
  - [dwm_alsa](#dwm_alsa)
  - [dwm_pulse](#dwm_pulse)
  - [dwm_battery](#dwm_battery)
  - [dwm_countdown](#dwm_countdown)
  - [dwm_keyboard](#dwm_keyboard)
  - [dwm_resources](#dwm_resources)
  - [dwm_cmus](#dwm_cmus)
  - [dwm_date](#dwm_date)
  - [dwm_mail](#dwm_mail)
  - [dwm_weather](#dwm_weather)
  - [dwm_network](#dwm_network)
  - [dwm_vpn](#dwm_vpn)
  - [dwm_ccurse](#dwm_ccurse)
- [Installation](#installation)
- [Usage](#usage)
- [Customizing](#customizing)
- [Acknowledgements](#acknowledgements)
- [More to come!](#more-to-come)
## Features
* Fully modular! If you don't want to use a function, no worries.
* Lightweight! dwm-bar is written entirely in POSIX-compliant shell script so need to install a hundred different packages to get it working.
* Options! You can decide to use either unicode symbols or plaintext for module identifiers with the ```IDENTIFIER``` value.
## Current Functions
### dwm_alsa
Displays the current master volume of ALSA
```
[🔉 55%]
```
Dependencies: ```alsa-utils```
### dwm_pulse
Displays the current master volume of PulseAudio
```
[🔉 55%]
```
Dependencies: ```pamixer```
### dwm_battery
Displays battery level and status
```
[🔋 100 full]
```
### dwm_countdown
Displays the status of [countdown](https://github.com/joestandring/countdown)
```
[⏳ 00:10:00]
```
Dependencies: ```countdown.sh```
### dwm_keyboard
Displays the current keyboard layout
```
[⌨ gb]
```
Dependencies: ```xorg-setxkbmap```
### dwm_resources
Displays information regarding memory, CPU temperature, and storage
```
[🖥 MEM 1.3Gi/15Gi CPU 45C STO 2.3G/200G: 2%]
```
### dwm_cmus
displays current cmus status, artist, track, position, duration, and shuffle
```
[▶ The Unicorns - Tuff Ghost 0:43/2:56 🔀]
```
Dependencies: ```cmus```
### dwm_date
Displays the current date and time
```
[🕰 Mon 06-05-19 21:31:58]
```
### dwm_mail
Displays the current number of emails in an inbox
```
[📫 2]
```
### dwm_weather
Displays the current weather provided by [wttr.in](https://wttr.in)
```
[☀ +20°C]
```
### dwm_network
Displays the current network connection, private IP, and public IP
```
[🌐 enp7s0: 192.168.0.1/24 | 185.199.109.153]
```
Dependencies: ```NetworkManager, curl```
### dwm_vpn
Displays the current VPN connection
```
[🔒 Sweden - Stockholm]
```
Dependencies: ```NetworkManager-openvpn```
### dwm_ccurse
Shows the next appointment from calcurse
```
[💡 18/04/19 19:00 20:00 Upload dwm_ccurse]
```
Dependencies: ```calcurse```
## Installation
1. Clone and enter the repository:
```
$ git clone https://github.com/joestandring/dwm-bar
$ cd dwm-bar
```
2. Make the script executable
```
$ chmod +x dwm_bar.sh
```
## Quick Start
Simply run the script and dwm should display your bar:
```
$ ./dwm_bar.sh
```
Most likely, you will need to change some values for functions to get them to work - these are outlined with a comment for functions where this is likely the case.
If you would like your bar to be displayed when X starts, add this to your .xinitrc file before launching dwm. For example, if the script is located in /home/$USER/dwm-bar/:
```
# Statusbar
/home/$USER/dwm-bar/dwm_status.sh &

# Start dwm
exec dwm
```
## Customizing
dwm-bar is completley modular, meaning you can mix and match functions to your hearts content. It's functions are located in the functions/ subdirectory and included in dwm_bar.sh
If you want to make your own function, for example dwm_myfunction.sh, you should create it in the functions/ subdirectory before including it in dwm_bar.sh and adding it to the xsetroot command:
```
# Import the modules
. "$DIR/functions/dwm_myfucntion"

while true
do
    xsetroot -name "$(dwm_myfunction)"
    sleep 1
done
```
You can also decide to use unicode or plaintext identifiers for functions by altering the ```$IDENTIFIER``` value. For example, set to ```"unicode"```, ```dwm_mail``` will display:
```
[📫 0]
```
Whereas, if it is not set it will display:
```
[MAI 0]
```
## Acknowledgements
Code for some functions was modified from:
* [Klemens Nanni](https://notabug.org/kl3)
* [@boylemic](https://github.com/boylemic/configs/blob/master/dwm_status)
* [Parket Johnson](https://github.com/ronno/scripts/blob/master/xsetcmus)
* [suckless.org](https://dwm.suckless.org/status_monitor/)
## More to come!
* dwm_bluez function to show currently connected Bluetooth device using bluez
