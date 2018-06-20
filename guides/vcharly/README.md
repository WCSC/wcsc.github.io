## Written by Varghese Emlin Charly
----------------------------------
### Contact :smiley:
- Slack: **@vcharly**
- Email: emlincharly@gmail.com

### Table of Contents

- [Prerequisites](#prereq)
- [Summary](#summary)
- [Downloading and First-Time Startup of CentOS](#downloadingcentos)
- [Setting up CentOS](#settingupcentos)
- [Installing Apache](#installapache)
- [Installing the Database](#installdb)
- [Installing PHP](#installphp)
- [Adding a User to the Database](#adduser)
- [Installing Wordpress](#installwordpress)
- [Configuring Wordpress](#configwordpress)
- [Installing Wordpress from Web GUI](#wordpressgui)
- [Troubleshooting](#trouble)

## Prerequisites <a id="prereq"></a>
1. Have pfSense Running
2. Have Ubuntu DNS Running
3. Have Windows 10 Running
4. Have ISP Gateway Running

## Summary <a id="summary"></a>
The CentOS machine will be hosting a public e-commerce site created using Wordpress. When you are finished, the site will be accessible from the WAN network through the Windows 10 machine.

<p align="center">
  <img src="chart.jpg?raw=true" alt="Topology Image"/>
</p>

## Downloading and First-Time Startup of CentOS <a id="downloadingcentos"></a>
1. First, download the CentOS ISO. It can be found [here](https://www.centos.org/download/)

    We are going to be using the CentOS Minimal ISO and install everything we need.

    Once the ISO is done downloading, proceed to create a new virtual machine inside VMWare or Virtualbox using the downloaded ISO. Use the recommended settings for the allocated ram, storage, and cpu cores.
And when asked for network adapter, allow CentOS to access the Host-Only, DMZ adapter. Adding the DMZ adapter allows the pfSense box to control the network traffic going in and out of the CentOS box.

    Boot the CentOS vm to proceed with the installation 

2. Once booted, choose the `Install CentOS 7` option.

    Now you will be greeted with a `Welcome to CentOS 7` screen.

    Choose your prefered language and proceed to the `Installation Summary` screen.

    Before the installation can begin, you must choose the installation destination. Click on `Installation Destination` and choose the virtual hard drive you created for the vm. This will ensure that the Operating system is installed to the correct location.

    Click `Done` and `Begin Installation`.

3. While CentOS installs, you must setup a `Root Password` and create a `New User`. Make sure you take a note of this information because you will be using this later to login.

    Once the install is done, you will be prompted to `Reboot`.

4. The reboot process shouldn't need any user input. But, once it has booted up, login with the new user you created while CentOS was installing.

    If you successfully logged in, Congratulations! You have installed CentOS. If you couldn't login, try login in with `localhost login: root`
and `Password: (The root password you set)`. Once you login with root, **BE SURE YOU CREATE A NEW USER**. If that didn't work, try reinstalling CentOS from the beginning.

## Setting up CentOS <a id="settingupcentos"></a>

1. Execute `ip a` and take note of your network adapter. It should be something along the lines of `enp0s3` for Virtual Box vms and `ens33` for VMWare vms.

2. Type `su root` to obtain root. The `su`is sometimes referred to as the "superuser" or "switch user" command. Using this command is one of the easiest way to switch your current user to root.

3. And then, `vi /etc/sysconfig/network-scripts/ifcfg-enp0s3`. (If you are using a VMWare vm, use `vi /etc/sysconfig/network-scripts/ifcfg-ens33`) Vi is a text editor you can use in the terminal.

    To edit text in `vi`, you must click `i` to enter "insert mode" and once you are done editing, click `ESC` to exit insert mode, now click `SHIFT` and `:` at the same time and enter `wq`. `wq` means write to the file and quit the file. The same can be done by doing `x` instead of `wq`. Refer to [this website](https://www.cs.colostate.edu/helpdocs/vi.html) to learn more about vi.

    You need to change the configuration from
    ``` bash
    BOOTROTO=dhcp
    ONBOOT=no
    ```
    to
    ``` bash
    BOOTROTO=static
    ONBOOT=yes
    ```
   DCHP is a protocol that dynamically assigns IPs to machines. Changing `BOOTORO` to static makes sure that machine doesn't try to acquire an IP address automatically. This is because we are going to manually give it an IP. This also means that if the IP configuration is not done correctly, you cannot connect with the other machines properly.
   
    Once that has been added, add these lines to the end of the configuration document
    ``` bash
    IPADDR=172.20.240.11
    NETMASK=255.255.255.0
    GATEWAY=172.20.240.254
    DNS1=172.20.240.23
    NM_CONTROLLED=no
    ```
    `IPADDR=172.20.240.11` will manually set the machine's IP. This is possible because we disable DHCP and changed it to static earlier. `DNS1=172.20.240.23` will make sure that DNS requests will be passed through the Ubuntu DNS.
    
4. Now to ensure that CentOS has an IP address, execute these commands (Again, if you are VMWare, your adapter is most likely ens33 or something similar).
    - `sudo ifdown enp0s3` (`ifdown` takes down the network interface)
    - `sudo ifup enp0s3` (`ifup` bring back up the network interface, while essentially doing a reboot)
    - `ip a` (Displays the network interfaces on the machines so you can make sure that `enp0s3`/`ens33` shows up)

    Let's verify everything worked by doing `ping 8.8.8.8` and `ping wwww.google.com` and making sure both responds. The response should be in the form of a reply from the IP address of Google. At this point you can also try to ping the Gateway (`172.20.240.254`) or any other machines that are on the same network (Ubuntu DNS).
    
## Installing Apache <a id="installapache"></a>
Install Apache using the following commands:
1. `sudo yum update` (Updates yum and will ensure that the next lines will run smoothly.)
2. `sudo yum install httpd` (HTTPD is a daemon created by Apache and this command is installing Apache Server for the machine to host the Wordpress site later on.)
    Next, `sudo iptables -F` needs to be run to flush the iptables. You can also run `iptables -S` to make sure there are no rules currently on the table.
    
    Now, you can restart the service by running `sudo systemctl start httpd.service`
    
    We want Apache to start on boot, so we can run `sudo systemctl enable httpd.service` to enable that. (At this point you can visit `172.20.240.11` from the Windows 10 machine to ensure everything is running properly. You should see the default page for Apache with lots of useful information about file locations and your Configuration Overview.
    
## Installing the Database <a id="installdb"></a>
Install the database using the following commands:
1. `sudo yum install mariadb-server mariadb` (This installs the Maria Database, which is similar to MySQL.)
2. `sudo systemctl start mariadb`
3. `sudo systemctl status mariadb` (Will ensure that MariaDB is installed and started.)
4. `sudo mysql_secure_installation` (Is used to secure the database.)

## Installing PHP <a id="installphp"></a>
Install PHP using the following commands:
1. `sudo yum install php php-mysql`
2. `sudo yum install nano` (Installs nano. Nano will be used to edit `.php` files that will be later created. You can also use others like vim))
3. `sudo nano /var/www/html/info.php` (Will create and open a new `.php` file in that directory. Make sure that you `sudo` this command, if not, you may have difficulties when trying to save the file.)
    Add `<?php phpinfo(); ?>` to the file. (This will be used to display general information about PHP later on. This can also be used as a check to make sure that PHP is installed correctly later.)
4. `sudo systemctl restart httpd.service` (Restarts the Apache service.)
    Run `sudo systemctl status httpd.service` (Verifies that the service is back up and running.)
5. Now you can visit `172.20.240.11/info.php` from the Windows 10 machine and it will now display information about PHP that is created in step 3.
## Adding a User to the Database <a id="adduser"></a>
Add a user to the database using the following commands:
1. `mysql -u root –p` to login as root

    After entering MYSQL, the terminal should look something like this:
    ```bash
    mysql>
    ```
2. Execute the following commands to add a user to the database:
    - `CREATE DATABASE wordpress` Creates a database called `wordpress`
    - `CREATE USER web@localhost IDENTIFIED BY 'password';` Creates a user called `web@localhost` that has a password of `password`(You can change the password to something you prefer).
    - `GRANT ALL PRIVILEGES ON wordpress.* TO web@localhost IDENTIFIED BY 'password';` Grants all privileges for the database `wordpress` to the user `web@localhost` with the password `password`.(The `*` means everything inside that database, just like `/Desktop/*` means everything inside the Desktop folder.)
    - `FLUSH PRIVILEGES;` (Running this tells MySQL to reload the privileges granted to users)
    - `exit`
 
## Installing Wordpress <a id="installwordpress"></a>
Install Wordpress using the following commands:
1. `sudo yum install php-gd` (Installs PHP for the Wordpress website to communicate with the database)
   Use `sudo service httpd restart` to restart the Apache service.
2. `cd ~` Will take you back to the home directory.
3. `sudo yum install wget` (Will install `wget`, which is needed to retrieve the zip file needed to install Wordpress. Running `wget` on a URL will download the files that URL leads to.)
4. `wget http://wordpress.org/latest.tar.gz` (Downloads a zip file for Wordpress.)
5. `tar xzvf latest.tar.gz` (Unzips the file that was downloaded.)
6. `sudo rsync -avP ~/wordpress/ /var/www/html/` (Is used to move the `wordpress` directory to its new home at `/var/www/html/`.)
7. `mkdir /var/www/html/wp-content/uploads` (Creates a new directory.)
8. `sudo chown -R apache:apache /var/www/html/*` (Changes the owner for the directories.)

## Configuring Wordpress <a id="configwordpress"></a>
1. `cd /var/www/html` (Moves the working directory to the `html` directory.)
2. `cp wp-config-sample.php wp-config.php` (Copies the sample Wordpress config file and renames it `wp-config.php`.)
3. `nano wp-config.php` Edit the file to accompany these new changes:
    ```bash
    define('DB_NAME', 'wordpress');
    define('DB_USER', 'web')
    define('DB_PASSWORD', 'password');
    ```
    (These credentials will be used by PHP to connect to the database called `wordpress` using the user "`web`" and the password "`password`" that we created earlier in MySQL.)
4. Visit `172.20.240.11` from the Windows 10 machine to ensure that the service is running properly.

## Installing Wordpress from Web GUI <a id="wordpressgui"></a>
1. Visit `http://172.20.240.11/wp-admin/install.php` from the Windows 10 machine. You should see a greeting from Wordpress and instructions to install Wordpress.
2. Follow the prompted instructions and proceed into setting. Use the following images to guide you through the process. (The images are provided by Wordpress)

<p align="center">
  <img src="step1.png?raw=true" alt="Step 1 Image"/>
  <img src="step2.png?raw=true" alt="Step 2 Image"/>
</p>

## Troubleshooting <a id="trouble"></a>
If you have any issues installing Wordpress, please refer to Wordpress's official documentation. The documentation for the installation process can be found [here](https://codex.wordpress.org/Installing_WordPress).
