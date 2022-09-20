# BidServer

Step #1 Buy server:
https://www.amazon.com/dp/B08YH5TRMZ?psc=1&ref=ppx_yo2ov_dt_b_product_details

Step #2 Setup: iDRAC (Integrated Dell Remote Access Controller) setup:
Bought the VGA to HDMI adapter to connect the server to PC.
Followed steps to setup static IP.
Tried accessing the IP on Chrome browser but could not connect  to the IP address. 
Tried to ping but got "host down" , "time out" and used "arp -an" but could not get arp responses: 
                     The Address Resolution Protocol (ARP) is a communication protocol used for discovering the link layer address, such as a MAC address,         associated with a given internet layer address.
After sometime , did a clean start and the I could see ping responses and arp responses.
In chrome , got "Your connection is not private" error due to self signed cert , tried multiple options but could not work. 
Tried in safari and could connect to the iDRAC web UI using the IP.

Step #3: Proxmox installation:
Downloaded the Proxmox ISO to USB drive. Copied it to  USB drive andplugged to the server. Could not get the Proxmox screen to setup.
Used balenaEtcher for Mac to flash OS image to USB drive. Then I could get the Porxmox screen. Did the RAID setup , then followed the steps. Got the IP and port  to connect to Proxmox web UI.



