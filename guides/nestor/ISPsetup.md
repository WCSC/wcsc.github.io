---
Layout: Post
Title: ISP setup ubuntu
Author: Nestor N Torres
---

### Contact
- Slack: @nanjuan on wcscusf.slack.com
- [LinkedIn](https://www.linkedin.com/in/nestor-n-torres-737172a5/)
- Email: nestor@nntorres.com

### Table
1. [Prerequisites](#preinfo)
2. [Summary](#Summary)
3. [VirtualBox VM Setup](#First)
4. [Ubuntu Server installation](#Second)
5. [Ubuntu Server Configuration](#Third)

## Prerequisites <a id="preinfo"></a>
1. Have [Network Adapter setup](link-to-guide)running
1. If you have not setup your network adapter look here https://goo.gl/vs4cHC.
2. Just copy the Prerequisites of peoples guides before yours here.
3. Have your [virtual environment](link-to-guide) configured
4. Have the [ISP](link-to-guide) gateway running.
5. Have [pfSense](link-to-guide) running.

## Summary <a id="Summary"></a>
The logical ideal of this tutorial is for you to be able to setup the ISP server for your lab. The ISP lab is the one that allow you to connect your other lab to the internet think at it as your internet provider at home.  


<br>

| Network adapters | Description                             |
|------------------|---------------------------------        |
| Adapter 1        | Leave it to NAT                         |
| Adapter 2        | Change to Host-only (WAN Environment)   |


## VirtualBox VM Setup <a id="First"></a>


1. Go to [Ubuntu](https://www.ubuntu.com/download/server) and download the LTS server version. 

- Install Ubuntu Server in Virtual Machine
- On Virtual Box go to top left corner to `New` to create the virtual box.

![Section2](https://i.imgur.com/QnoKC2F.png) 

- Create the name of this Box recommended name `ISP Ubuntu`
- In Type choose `Linux` if is not auto setected
- In Version choose `Ubuntu (64-bit)`

![Section3](https://i.imgur.com/2JtRAzY.png)

- On the memory section depending to your machine `RAM` capacity the minimun should be `(254MB)` but if you have enough memory use `(1024MB)`

![Section4](https://i.imgur.com/3KinU4J.png)

- Leave the Hard drive section as default which is `(Create a virutal hard disk now)`

![Section5](https://i.imgur.com/OwYGx2s.png)

- Leave the Hard disk file type to `(VDI)` 

![Section5](https://i.imgur.com/XPpGqxm.png)

- Leave storage on physical hard disk to `(Dynamically allocated)` this will used the hard drive memory dinamically until it reach the max you gave it on the next step. 

![Section5](https://i.imgur.com/YGrvBmV.png)

- For this machine the minimun for Ubuntu so it does not give you problem set the File location and `size to (20.00GB)`

![Section5](https://i.imgur.com/p2jIaGn.png)

- After the Virtual Machine is created now you have to add the `ISO` that you download at the beginning 
- Go to Storage section and click on top that it say `[Optical Drive]Empty`

![Section6](https://i.imgur.com/8Rfq6nZ.png)

- Then press `Choose disk image...`

![Section6](https://i.imgur.com/Hbb1y7h.png)

- Find the location where you download your ISO for Ubuntu Server.

![Section6](https://i.imgur.com/JHKaWpk.png)

- On this step make sure you add the network adapters to the server 

- `Right click` the `ISP Ubuntu` and click `settings`

![Section7](https://i.imgur.com/8w6rRfO.png)

- On network adapter one leave it to `NAT`
- Then go to Network Adapter 2 and change the network adapter to `WAN Environment` like the picture bellow.

![Section7](https://i.imgur.com/EB1ajQl.png)
![Section7](https://i.imgur.com/N2OBoxs.png)

- On this part start the ISP ubuntu virtual box to start the setup. 

- Click on the `ISP Ubuntu` then press `start`

![Section8](https://i.imgur.com/wvUCwDs.png)

## Ubuntu Server installation <a id="Second"></a>

2. The setup of the ISP Ubuntu on the photos bellow

- select you language

![Section9](https://i.imgur.com/Cr4wj1w.png)

- Press enter on `Install Ubuntu Server`

![Section9](https://i.imgur.com/FCEeu3L.png)

- Select the language again

![Section9](https://i.imgur.com/cptpprK.png)

- Select your location

![Section9](https://i.imgur.com/G03SKC5.png)

- Press `no` on the Configure the Keyboard

![Section9](https://i.imgur.com/6x0pEuX.png)

- Select Keyboard language

![Section9](https://i.imgur.com/zQ2EeJk.png)

![Section9](https://i.imgur.com/jsibCL2.png)

- Select `enp0s3` which is the `NAT` this might vary on your PC

![Section9](https://i.imgur.com/xN9m2js.png)

- Set the `Hostname` of you VM machine to whatever you want

![Section9](https://i.imgur.com/isHnTuW.png)

- Set the full name for `new user`

![Section9](https://i.imgur.com/SeJZZFJ.png)

![Section9](https://i.imgur.com/mmDpJK9.png)

- Then set your `Username` for your account

![Section9](https://i.imgur.com/zuIqs7E.png)

- Set the new user `password`

![Section9](https://i.imgur.com/t4L1H5v.png)

- verify password again

![Section9](https://i.imgur.com/Ypjs1pV.png)

- Select if you want to encrypt your home directory `I advice to select no for this test lab`

![Section9](https://i.imgur.com/Tfju0kx.png)

- Select your `Time zone` if the one shown is correct press yes otherwise press no

![Selection9](https://i.imgur.com/FHvvLvn.png)

- Select Partition disks select the `default` the one on the picture.

![Selection9](https://i.imgur.com/ed9XOYY.png)

- Select disk partition the `default`

![Selection9](https://i.imgur.com/VGm3bD6.png)

- On the next step select `YES` on configure LVM

![Selection9](https://i.imgur.com/btRTEMa.png)
![Selection9](https://i.imgur.com/K0Xme6H.png)

- Select the partition size `you need to leave it as default`

![Selection9](https://i.imgur.com/TiERK5h.png)

- Press `yes` on write the changes to disks

![Selection9](https://i.imgur.com/eTfOxHK.png)

- `Do not` set a proxy leave black and press continue

![Selection9](https://i.imgur.com/ywLngCl.png)

- The update question is all up to you. Can be setup to `no auto updates` or `install security updates automatically`

![Selection9](https://i.imgur.com/2MzOrqS.png)

- On the `sofware selection` for this lab `leave default`

![Selection9](https://i.imgur.com/325nEqo.png)

- on the install the grub boot loader question select `YES`

![Selection9](https://i.imgur.com/ilxTd3J.png)

- On the last question select `continue`

![Selection9](https://i.imgur.com/az5SGZO.png)

## Ubuntu Server Configuration <a id="Third"></a>

3. After Reboot log in into computer with the `username` you setup early and enter `password` to log in

![Selection9](https://i.imgur.com/HjsqfkV.png)
![Selection9](https://i.imgur.com/avlp5hu.png)

- First step run `sudo apt-get update` `sudo apt-get upgrade` to make sure the system is up to date. 
- Enable ipv4 routing on Ubuntu. By default Ubuntu doesn't allow for routing on IP traffic.
- To get this done you will need to edit `sysctl.conf` which is on the directory /etc/. 
- This can be done by using nano like so, `sudo nano /etc/sysctl.conf`. 
- It will require your `root password` since it effect the entire system when you edit this file.

![Selection9](https://i.imgur.com/cWJB3p5.png)
![Selection9](https://i.imgur.com/nkxml1h.png)

- Go to the line that say `Uncomment the next line to enable packet forwarding for IPv4` and the remove the symbol `#` by removing the `#` sign this will make the program read and use that line to `enable packet forwarding`. 

![Selection9](https://i.imgur.com/LJgDvBJ.png)

- Then press `control+X` to save the config file on ubuntu and enter `Y` to confirm the file and safe the file 

![Selection9](https://i.imgur.com/D2IAI1b.png)

- Then press `Enter` to make sure the file name stay the same

![Selection9](https://i.imgur.com/aWGEO3P.png)

- Next step run command `ip link show` to see which network interfaces are up  it will look like the picture bellow
- You should have you loopback `lo` and your network adapters `enp0s3` and `enp0s8` or similars. 

![Selection9](https://i.imgur.com/2r0ghbi.png)

- You will need to add another interface to the server which is going to be the ip address for your lap to go into th einternet. 
- Run command on the terminal `sudo nano /etc/network/interfaces` and enter your admin password

![Selection9](https://i.imgur.com/EmMewtr.png)

- Then you will see a text file like bellow

![Selection9](https://i.imgur.com/YzAyL1s.png)

- Then add the new network adapter like bellow
- ISP sever network interface 
-	`auto enp0s8`
		`iface enp0s8 inet static`
			`address 172.31.11.1`
			`netmask 255.255.255.248`
			`up route add -net 172.0.0.0 netmask 255.0.0.0 gw 172.31.1.2`

![Selection9](https://i.imgur.com/cU2izxY.png)

- Then press `control X` to exit and `Y` to save file then enter to leave the file with the same name do not change the file name

![Selection9](https://i.imgur.com/gCgEyWU.png)

- run `sudo reboot` on the terminal this will reboot the machine and the seeting on the interfaces will take effect
- Then run `router` on the terminal after it reboot it shout look like picture bellow 

![Selection9](https://i.imgur.com/wCEIwLd.png)

- Then run the next line on terminal this will add the new network adapter to your network route. 
- `sudo route add –net 172.0.0.0 netmask 255.0.0.0 gw 172.31.1.3 dev enp0s8`

![Selection9](https://i.imgur.com/AveqQd6.png)

- Then run `route` again to verify it took effect 

![Selection9](https://i.imgur.com/I9QDTpD.png)

- Then run `sudo services networking restart` to restard the network services nothing will display it only going to ask you for your admin password. This will restard your network services for the code above take effect. 

![Selection9](https://i.imgur.com/hR7cdtQ.png)

- Then to verify everything is working fine run `ifconfig` the enp0s8 should have the infomation you enter like bellow

![Selection9](https://i.imgur.com/b4lVh9W.png)

- Before running the following command run `sudo apt-get update and upgrade` and `sudo apt-get install iptables-persistant` this will make the followin lines work correctly.  
- Then run this tree line on terminal like the picture bellow this will enable persistent on the iptables. 
- `sudo apt-get install -y iptables-persistent`

![Selection9](https://i.imgur.com/xncEGuM.png)

- Then on the next two question select yes like bellow

![Selection9](https://i.imgur.com/yjjPrcx.png)
![Selection9](https://i.imgur.com/Fjd9QBr.png)

- Run next line bellow and password if ask it will not display anything after you run the line same as above is to make the iptables not reset.
- `sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE`

![Selection9](https://i.imgur.com/jJrCz0Z.png)

- Run next line bellow and password if as and it will look like the picture bellows
- `sudo netfilter-persistent save`

![Selection9](https://i.imgur.com/JTUsR1o.png)
![Selection9](https://i.imgur.com/JamB7Pu.png)

- Run next line bellow and password if as and it will look like the picture bellows
- `sudo netfilter-persistent reload`

![Imgur](https://i.imgur.com/SmgzpkB.png)
![Imgur](https://i.imgur.com/njlW4bE.png)

- After all this reboot Virtual Machine which can be done by running the following command `sudo reboot now` and move to next step pfsense setup.