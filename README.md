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

![20230413_192550](https://user-images.githubusercontent.com/113651761/235375656-c53d6810-fe7d-4a3c-89df-a6f840d63031.jpg)

![20230413_195435](https://user-images.githubusercontent.com/113651761/235375674-5e83d6a4-d315-4675-8187-1daafd9247dc.jpg)

<img width="1321" alt="Screen Shot 2023-04-30 at 4 01 46 PM" src="https://user-images.githubusercontent.com/113651761/235376087-b23c7e00-8c36-41fd-9674-4467a32b7300.png">

Step #3: Proxmox installation:
Downloaded the Proxmox ISO to USB drive. Copied it to  USB drive andplugged to the server. Could not get the Proxmox screen to setup.
Used balenaEtcher for Mac to flash OS image to USB drive. Then I could get the Porxmox screen. Did the RAID setup , then followed the steps. Got the IP and port  to connect to Proxmox web UI.

![pm1](https://user-images.githubusercontent.com/113651761/235375856-9a4af189-abef-47ae-8036-c2af0f989642.jpg)

![pm2](https://user-images.githubusercontent.com/113651761/235375860-d973e7c5-32e8-4f03-84e1-1bb47fb3d4b1.jpg)

![pm3](https://user-images.githubusercontent.com/113651761/235375866-151fa846-d9e6-4ea7-ae6d-bb68e1c526ce.jpg)

![pm4](https://user-images.githubusercontent.com/113651761/235375873-42132ccd-df86-4776-bfe0-041ed736890e.jpg)

![pm5](https://user-images.githubusercontent.com/113651761/235375890-4847004a-f2bb-4d0d-8e07-d361cf7ab39c.jpg)

![pm6](https://user-images.githubusercontent.com/113651761/235375894-2dced107-b631-47a0-a560-38cce3b99275.jpg)

![pm7](https://user-images.githubusercontent.com/113651761/235375901-0f416136-5fc0-48c7-84cf-fe7777702682.jpg)

![pm8](https://user-images.githubusercontent.com/113651761/235375906-425d0042-8b74-4b4d-8793-95a170b23141.jpg)

<img width="1323" alt="Screen Shot 2023-04-30 at 4 03 25 PM" src="https://user-images.githubusercontent.com/113651761/235376120-5f881e8d-48a7-4926-9fe4-252b62b424d4.png">

Step #4: Pihole setup:
Created LXC container using Centos.

<img width="762" alt="Screen Shot 2023-04-29 at 10 41 03 PM" src="https://user-images.githubusercontent.com/113651761/235375974-f4a43eb0-24d5-4ab4-996b-b7520526c476.png">

<img width="775" alt="Screen Shot 2023-04-29 at 10 41 08 PM" src="https://user-images.githubusercontent.com/113651761/235375977-be751747-4b0a-4020-9da4-4c0846dc0183.png">

<img width="783" alt="Screen Shot 2023-04-29 at 10 41 15 PM" src="https://user-images.githubusercontent.com/113651761/235375982-cf572283-6b46-47e4-8355-9a29db47d293.png">

<img width="774" alt="Screen Shot 2023-04-29 at 10 41 20 PM" src="https://user-images.githubusercontent.com/113651761/235375983-a44f29b5-dc78-4ecf-8333-67879f43c5fd.png">

<img width="809" alt="Screen Shot 2023-04-29 at 10 41 26 PM" src="https://user-images.githubusercontent.com/113651761/235375989-53965374-0b25-4ed9-84e4-24e4b0dfb0a1.png">

<img width="1046" alt="Screen Shot 2023-04-30 at 12 34 13 PM" src="https://user-images.githubusercontent.com/113651761/235375992-68e23de3-9b24-4297-93be-bedcf3773a81.png">

<img width="825" alt="Screen Shot 2023-04-30 at 12 34 35 PM" src="https://user-images.githubusercontent.com/113651761/235375996-f4f54cb4-2a36-45e8-abf7-52a0a4337861.png">

<img width="1320" alt="Screen Shot 2023-04-30 at 4 02 05 PM" src="https://user-images.githubusercontent.com/113651761/235376115-d0f84229-4dab-4b35-bd85-1d6cfc004bd9.png">

dnf update -y
dnf upgrade -y
curl -sSL https://install.pi-hole.net | bash
pihole -a -p
 

https://docs.pi-hole.net/guides/dns/unbound/

wget https://www.internic.net/domain/named.root -qO- | sudo tee /var/lib/unbound/root.hints

Note:
**Download the current root hints file (the list of primary root servers which are serving the domain "." - the root domain). Update it roughly every six months.**

<img width="1325" alt="Screen Shot 2023-04-30 at 4 04 19 PM" src="https://user-images.githubusercontent.com/113651761/235376145-cfe33f17-7db0-4898-9ae1-889713afea12.png">

<img width="1322" alt="Screen Shot 2023-04-30 at 4 08 00 PM" src="https://user-images.githubusercontent.com/113651761/235376307-866d9bf4-d510-48db-9d7f-5169106b3125.png">

Added the PiHole IP to Network-->Ethernet Adapter-->DNS in MAC to test add block and recursive DNS.

<img width="663" alt="Screen Shot 2023-04-30 at 4 04 59 PM" src="https://user-images.githubusercontent.com/113651761/235376169-88df3d62-847e-4a35-9bec-4865dd2c4483.png">


Step #5: OpenShift installation:

![Screen Shot 2022-09-20 at 6 02 58 PM](https://user-images.githubusercontent.com/113651761/191379791-a32b45ec-4ea6-46d2-b186-a0eb6fbc8e66.png)




Single Node Openshift

Three Master and two worker Openshift

Step #6: AAP installation:


Step #7: Automating provisioning:


Step #8: Smart Management/ Satellite/ Insights to manage the instances:
Register system to insights: insights-client --register
You can check the vulnerabilities and remediate via executing playbook on the system through cloud connector: https://access.redhat.com/articles/rhc-registration. 
You will need proper privilege for this "Remediations administrator": https://console.redhat.com/iam/user-access/users. You can add the proper role if not already added to the user.






