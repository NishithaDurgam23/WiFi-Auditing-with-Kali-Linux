# WiFi-Auditing-with-Kali-Linux

WiFi Auditing with Kali Linux
This repository contains scripts and instructions for WiFi auditing using Kali Linux tools like airmon-ng, wifite, and others. These tools allow you to test the security of WiFi networks by monitoring, capturing, and cracking passwords.

Note: This project is for educational purposes only. Do not use these tools on networks you do not own or have explicit permission to test.

Prerequisites
Before you begin, make sure you have the following installed:

Kali Linux: You can install Kali Linux on a physical machine or in a VirtualBox/VMware environment.
WiFi Adapter: A compatible external WiFi adapter capable of monitor mode and packet injection (e.g., Alfa AWUS036ACH).
Aircrack-ng: A complete suite of tools for WiFi network security auditing.
Wifite: An automated WiFi hacking tool that simplifies the use of various WiFi audit tools.


Tools Used
airmon-ng: To enable monitor mode on your WiFi adapter.
airodump-ng: To capture WiFi network packets.
aireplay-ng: For deauth attacks or packet injection.
wifite: To automate the auditing process.


Installation
Install the necessary tools:



sudo apt update
sudo apt install aircrack-ng wifite
Check if your WiFi adapter supports monitor mode:



sudo iwconfig
Enable monitor mode on your adapter:



sudo airmon-ng start wlan0

Usage
Using wifite
Run wifite to start scanning for available WiFi networks:


sudo wifite
Select the network(s) you wish to audit from the list displayed by wifite.

Wait for the attack to complete. Wifite will attempt different attacks based on the security type (WEP, WPA, etc.).

If successful, Wifite will crack the password and display it on the screen.

Manual WiFi Auditing
Start by placing your WiFi adapter in monitor mode:


sudo airmon-ng start wlan0
Use airodump-ng to scan for networks:


sudo airodump-ng wlan0mon
Target a specific network:


sudo airodump-ng --bssid [BSSID] -c [CHANNEL] -w [OUTPUT] wlan0mon
Deauthenticate a client to capture the handshake:


sudo aireplay-ng --deauth 10 -a [BSSID] wlan0mon

Crack the captured handshake:


sudo aircrack-ng [OUTPUT].cap -w [WORDLIST]


#Screenshots
Here are a few screenshots of the setup and usage:

Monitor mode enabled:


Scanning WiFi networks:


Successful password crack:


License
This project is licensed under the MIT License.

Disclaimer
This tool should only be used for ethical hacking purposes on networks you own or have permission to test. Unauthorized access to computer systems is illegal.
