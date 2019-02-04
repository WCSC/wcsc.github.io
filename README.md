### Mission
Through competing in CCDC competition, we aim to provide Whitehatters Computer Security Club members with valuable enterprise level experience that will be applicable to their future careers in the cybersecurity field.

##### Semester Framework
Build, setup services, and secure the network based on the template below.

<center>
    <figure>
        <img src="assets\images\CCDC_2019.png" style="border: 1px solid #000">
        <figcaption><center>Southeast Regional Cyber Defense Qualification Network Topology</center></figcaption>
    </figure>
</center>

##### Machines and IP
| Internal     | Local IP      |
|--------------|---------------|
| Phantom      | 172.20.240.10 |
| Debian MySQL | 172.20.240.20 |

| User                    | Local IP       |
|-------------------------|----------------|
| Ubuntu DNS              | 172.20.242.10  |
| 2008 R2 AD/DNS/Exchange | 172.20.242.200 |
| Windows 8.1             | 172.20.242.100 |

| Public                 | Local IP      |
|------------------------|---------------|
| Splunk                 | 172.20.241.20 |
| CentOS E-Commerce      | 172.20.241.30 |
| Fedora Webmail/WebApps | 172.20.241.40 |

### Getting Started
_Notice: Some of the guides below may be out of date due to the recent update of the CCDC network topology. Don't let that discourage you! Use these guides as a reference to build the new topology. We are currently working on new guides for the updated topology._ :smile:
1. Download a virtualization program:
    - [Vitualbox](https://www.virtualbox.org/wiki/Downloads)
2. Download the ISO Images:
    - [Ubuntu](https://www.ubuntu.com/download/server)
    - [CentOS](http://isoredirect.centos.org/centos/7/isos/x86_64/CentOS-7-x86_64-Everything-1611.iso)
    - [Windows](https://www.microsoft.com/en-us/evalcenter/)
    - [Debian](https://www.debian.org/distrib/)
    - [PFsense](https://www.pfsense.org/download/)
3. Setup the Virtual Environment:
    - TODO: Merge a whitehatter's guide
4. Setup the Ubuntu ISP (Cloud): 
    - [Nestor's Tutorial](guides/nestor/ISPsetup.md)
5. Setup the PFsense box (Palo Alto):
    - [Tong's Tutorial](guides/Tong/README.md)
6. Setup the Ubuntu DNS:
    - [Whilliam's Tutorial](guides/william/DNSNotes.md)
7. Setup CentOS E-Commerce:
    - [Emlin's Tutorial](guides/vcharly/README.md)
8. Setup Windows 10 (Window 7):
    - TODO: Merge a whitehatter's guide
9. Setup Debian Email:
    - [Leon's Tutorial](guides/leon/debain-email.md)
10. Setup FTP server:
    - [Josh's Tutorial](guides/araujo/FTP_Writeup.md)
    - [Leon's Linux FTP Tutorial](guides/leon/vsftpd.md)
11. Setup Web Apps:
    - TODO: Merge a whitehatter's guide
12. Setup AD/DNS:
    - TODO: Merge a whitehatter's guide
13. Contributing back:
    - [Bermudez's Template](guides/bermudez/template.md)

### Core Knowledge
##### Learning Bash:
- [Jon's Guide](knowledge/jonathan/Bash-Guide-WCSC/Bash-Guide.md)

##### Leaning Git:
- TODO: Merge a whitehatter's guide

##### Learning Markdown:
- TODO: Merge a whitehatter's guide

##### Learning IPv4:
- [SilexOne's Guide](knowledge/bermudez/subnet.md)

##### Learning FTP:
- [Leon's Guide](knowledge/leon/ftp_shell.md)
