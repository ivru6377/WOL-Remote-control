# WOL-Remote-control tutorial
## This is how I Wake On WAN for Cloud computing or cloud gaming from LAN or WAN using ISP router advanced configurations
This is how I WOL or WAN - Cloud computing/gaming from LAN or WAN – Movistar router advanced configurations 
In this tutorial I will show the solution I use for waking up my gaming/working PC from S5/S4 and use it for cloud computing or remote gaming. 
For this I use the combination of two open-source software solutions that are well known. Sunshine in the host, and Moonlight in the client.
The documentation on how to configure these programs is very clear so in the corresponding section you will have link to documentation and a summary of requirements for host and client so you can check if this solution is good for you.
So why am I doing this tutorial?
I had a lot of trouble setting some of these things and maybe some of this info may help people.

IF YOU ONLY WANT GAMMING SKIP THE FIRST SECTION
# SECTION 1. WOL AND ROUTER
**Wake on Lan / Wake on Wan**

Step 1: Computer configuration
Steps:
1.	Configure windows
2.	Configure UEFI
Windows:
Right click on start -> device management -> right click on internet card -> properties
 <img width="567" height="498" alt="imagen" src="https://github.com/user-attachments/assets/b48e2d1f-1ae5-4fab-9436-fd1526656c62" />
On energy management three ticks
On advanced make sure to enable PME and wake up on Magic Packet
This should work but if not then go to power saving advanced option and make sure your energy options don’t turn off NIC completely. 

**Configure UEFI – Linux systems**
I am on AsRock motherboard so here it is:
https://www.claudiokuenzler.com/blog/1208/how-to-enable-wake-on-lan-wol-asrock-b550-motherboard-linux

**Step2: WAL/WAN**
Note: This is way easier with ethernet connection.
**Wake on LAN:**
This is not a trouble.
My phone is android so I downloaded this app: https://play.google.com/store/apps/details?id=co.uk.mrwebb.wakeonlan&hl=en
connect to same network and PC was detected
But as I say: it is easier to just walk some steps and turn my PC so on WOL in LAN most of the time just being lazy.
**Wake on WAN:**
Here you can have some trouble because you need some more configuration on router.
Configurations on the router – Movistar Askey
I use Movistar and as you know those routers are modified and normally you have limited control. If you want to take full control you will need to buy another router and set Movistar as bridge as follows:
https://www.redeszone.net/tutoriales/configuracion-routers/configurar-askey-rtf8115vw-movistar-bridge-puente/
Right now, I don’t have the money. For Movistar routers Askey RTF8115VW configurations are here: https://192.168.1.1:8000/avanzada.asp user and password on sticker of router is usual.
**Steps:**
1.	Static IP on PC
2.	Dynamic DNS 
3.	PortMapping
**Static IP on PC**
The best way to achieve this is to modify ARP entry on the router and associate IP with MAC address. In that way if your motherboard allows it you can wake up computer from S5.
In my case, the firmware is modified in a way I could not mess with ARP table, so I had used Static Lease to my PC. I can wake it up from S4 if I am not in my LAN. 
Remember that is your internal IP address. External IP is changing unless you pay your ISP for a fixed external IP address. They use this mostly for business. 
<img width="567" height="406" alt="imagen" src="https://github.com/user-attachments/assets/82bed9fb-1641-492a-bfc0-7ae347adba9d" />


Dynamic DNS – get a fixed External Domain
Dynamic DNS is the solution as you get a fixed domain name associated with a moving IP
https://www.dynu.com/en-US/
Is a free solution that works like a cham. So, I created a free account and then control panel DDNS services and created one. There you will also find your domain name. 
Configure DDNS on router with your domain and credentials. 
 <img width="567" height="373" alt="imagen" src="https://github.com/user-attachments/assets/56952ae9-849c-4ac1-9b7b-0cbbbeeef8a0" />

**Port Mapping**
UDP on port 9 to your IP for the magic package to find your PC GAMMER.

**TOUBLESHOOTING**
Test on various PC states (S3/S4/S5), in general if it works in S3 but no S4 -> OS problem S4 vs. S5 -> UEFI or router
Always test locally first for telling router from software problems.

# SECTION 2 REMOTE SESSION
## Want windows RDP for working?
Note: Only some windows editions work as host
Default port is 3389. Some people chose another port for security. It is not that hard to change.  Open TCP port on router to your pc
Remember your URL is username.ddnsgeek.com and some apps need explicit port adding username.ddnsgeek.com:portnumber
It is intended for office work.
For gaming go with moonlight and sunshine

# Remote gamming Moonlight/Sunshine:
Follow this tutorial:
https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#quick-setup-instructions

**These are host requirements:**
Minimum Requirements
Component 	Requirement 
GPU 	AMD: VCE 1.0 or higher, see: obs-amd hardware support 

	Intel:
  Linux: VAAPI-compatible, see: VAAPI hardware support
  Windows: Skylake or newer with QuickSync encoding support 
	Nvidia: NVENC enabled cards, see: nvenc support matrix 

CPU 	AMD: Ryzen 3 or higher 
	Intel: Core i3 or higher 
RAM 	4GB or more 
OS 	Windows: 10+ (Windows Server does not support virtual gamepads) 
	macOS: 14+ 
	Linux/Debian: 13+ (trixie) 
	Linux/Fedora: 41+ 
	Linux/Ubuntu: 22.04+ (jammy) 
Network 	Host: 5GHz, 802.11ac 
	Client: 5GHz, 802.11ac 

**These are client requirements:**
 Android: An Android device running Android 4.1 (Jelly Bean) or newer. Newer and "flagship" devices with higher processor speeds are more likely to be able to handle Moonlight well by using the hardware video system on the device to produce smooth streaming without video stuttering or freezing.
iOS: An iOS device running iOS 9.3 or later.
tvOS: An Apple TV device running tvOS 12.0 or later.
PC: Windows 7+, macOS 10.13+, or Linux. Your PC should be new enough that it supports hardware-accelerated H.264 video decoding, otherwise it will have to use CPU decoding. Most PCs made since around 2010 should work fine, though older PCs may not be able to stream at 60 FPS without lag.
ChromeOS: All ChromeOS devices should have the required hardware.
Internet and Network Requirements
To have a good experience, you need a mid to high-end wireless router with a good wireless connection to your client device (5 GHz WiFi 5 (802.11ac) or WiFi 6 (802.11ax) strongly recommended) and a good connection from your PC server to your router (Ethernet/wired connections highly recommended).

# BONUS - PS VITA
Note: I own a Psvita this combination can so powerful and fast I can use it as a controller for my PC, with a cute second screen in my hands but sometimes you need to play with host and client resolution and Hz depending on your machines and your connection.

