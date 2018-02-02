---
layout: post
title: Title of Page
author: Jordan Bermudez
---

### Contact
- Whatever you want, or don't want
- Slack: @SilexOne on wcscusf.slack.com
- [LinkedIn](look-at-me)
- Email: something@blank.com

### Table
1. [Prerequisites](#id-link-to-section)
2. [Summary](#id-link-to-section)
3. [First logical group of Page](#id-link-to-section)
4. [Second logical group of Page](#id-link-to-section)
5. [Troubleshooting (optional)](#id-link-to-section)

## Prerequisites <a id="id-link-to-section"></a>
1. The Prerequisites before this.
2. Just copy the Prerequisites of peoples guides before yours here.
3. Have your [virtual environment](link-to-guide) configured
4. Have the [ISP](link-to-guide) gateway running.
5. Have [pfSense](link-to-guide) running.

## Summary <a id="id-link-to-section"></a>
Description on subject. Context of the Network Location/OS/Service/Other. Any other things that might be helpful.

![](box.png)

<br>

| Record Type | Description                          |
|-------------|--------------------------------------|
| A           | Links a host name to an IPv4 Address |
| AAAA        | stuff                                |
| MX          | more stuff                           |

##### Supporting detail (optional/ title name can change also)
group together logical ideas for the summary if needed

## First logical group of Page <a id="id-link-to-section"></a>
1. Use the text editor [vim](link-to-Knowledge) to edit the file `\etc\network\interfaces`. (Just hyperlink the first instance of each term that needs explaining then never again. I mention vim here. No link with it. Look at the IPv4 reference below to see how to link to another page in a certain section) You will need to be `root` because the file requires permissions that your user doesn't have. This can be done by using [sudo](link-to-Knowledge) before the command. Think of it as using the window administrator account with the User Access Control (UAC). If the command had a verify step be sure to explain why we do it and how to interpret the results.
- `sudo vim \etc\network\interfaces`
- `another command if needed`
- `You should have indvidual commands follow the instructions like so`
- `verify command if possible`
2. Once in the file change the default configuration of:

    ``` bash
    # The loopback network interface
    auto lo eth0
    iface lo inet loopback

    # The primary network interface
    iface eth0 inet dhcp
    ```

    Into:

    ``` bash
    # The loopback network interface
    auto lo eth0
    iface lo inet loopback

    # The primary network interface
    iface eth0 inet static
        address 192.168.10.33
        netmask 255.255.255.0
        broadcast 192.168.10.255
        network 192.168.10.0
        gateway 192.168.10.254 
        dns-nameservers 192.168.10.254

    ```

    Restart the service:

    `systemctl restart service-name`

    Verify:

    `ifconfig`

    Expected Outcome:

    ``` bash
    eth0      Link encap:Ethernet  HWaddr 00:15:c5:4a:16:5a  
              inet addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
              inet6 addr: fe80::215:c5ff:fe4a:165a/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:466475604 errors:0 dropped:0 overruns:0 frame:0
              TX packets:403172654 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:2574778386 (2.5 GB)  TX bytes:1618367329 (1.6 GB)
              Interrupt:16 
    ```

    This is done because... The address needs to be the [IPv4 address](/../../knowledge/bermudez/subnet.md#jump-to-section) of `192.1.1.1`. We restart blank because. We verify because. The outcome we expected was because. 
    Configs files should be formatted like this

3. another item, feel free to add images of your setup

## Second logical group of Page <a id="id-link-to-section"></a>
1. [Change Directory (cd)](link-to-Knowledge) into the serivce folder and perform some actions...
``` python
# notice how this block has python on top
# this is python code
import os
```

## Troubleshooting (optional) <a id="id-link-to-section"></a>
##### First logical group of Page (optional)
Common problems this section might of had
Resolutions to thoughs problems
Why those problems occured

##### Second logical group of Page (optional)
If no troubleshooting was needed in this logical group then this specific section isn't needed and shouldn't be included

[Homepage](../../)