---


---

<hr>
<h2 id="layout-posttitle-how-to-setup-an-ftp-serverauthor-joshua-araujo">layout: post<br>
title: How to Setup an FTP Server<br>
author: Joshua Araujo</h2>
<h3 id="contact">Contact</h3>
<ul>
<li>Slack: @Shinpuru on <a href="http://wcscusf.slack.com">wcscusf.slack.com</a></li>
<li><a href="look-at-me">LinkedIn</a></li>
<li>Email: <a href="mailto:something@blank.com">something@blank.com</a></li>
</ul>
<h3 id="table">Table</h3>
<ol>
<li><a href="#id-link-to-section">Prerequisites</a></li>
<li><a href="#id0">Summary</a></li>
<li><a href="#id1">Creating the Virtual Machine</a></li>
<li><a href="#id2">Installing Windows Server 2003</a></li>
</ol>
<h2 id="prerequisites-a-idid-link-to-sectiona">Prerequisites <a id="id-link-to-section"></a></h2>
<ol>
<li>Just copy the Prerequisites of peoples guides before yours here.</li>
<li>Have your <a href="https://silexone.github.io/guides/nestor/ISPsetup.html">virtual environment</a> configured</li>
<li>Have the <a href="https://silexone.github.io/guides/nestor/ISPsetup.html">ISP</a> gateway running.</li>
<li>Have <a href="link-to-guide">pfSense</a> running.</li>
</ol>
<h2 id="summary-a-idid0a">Summary <a id="id0"></a></h2>
<p>This guide sets up and configures the Windows Server 2003 as an FTP Server for the SECCDC 2018 Competition.</p>
<h2 id="creating-the-virtual-machine-a-idid1a">Creating the Virtual Machine <a id="id1"></a></h2>
<p>Before you can setup your FTP server, you must download this ISO file to install the virtual machine.  Once downloaded, open VirtualBox and click on “New” at the top left.</p>
<p>Name your FTP server whatever you’d like and select these options.</p>
<p><img src="/pics/cap%202.PNG" alt=""></p>
<p>Make sure to stay at least at the recommended amount of memory or add more if you’re able to.</p>
<p><img src="/pics/cap%203.PNG" alt=""></p>
<p>Leave the options as is and click create.</p>
<p><img src="/pics/cap%204.PNG" alt=""></p>
<p>Do the same and click next.</p>
<p><img src="/pics/cap%205.PNG" alt=""></p>
<p>Name the folder whatever you’d like and click create because 20 GB will be enough space.</p>
<p><img src="/pics/cap%207.PNG" alt=""></p>
<h2 id="installing-the-windows-server-2003-a-idid2a">Installing the Windows Server 2003 <a id="id2"></a></h2>
<p>Once the options are completed, make sure your new server is selected and click start at the top.  Once started, make sure to select the proper ISO file from where you downloaded it from.</p>
<p>Choose the default options for these first few pages and let the installation process begin.</p>
<p><img src="/pics/cap%208.PNG" alt=""></p>
<p>Once promoted, fill in the boxes with appropriate info and continue through the settings and make sure to set an admin password.</p>
<p><img src="/pics/cap%209.PNG" alt=""></p>
<p>Instead of choosing “Typical settings”, click on “Custom settings” and click next.</p>
<p><img src="/pics/cap%2010.PNG" alt=""></p>
<p>Select the “Internet Protocol (TCP/IP)” option and click on properties.</p>
<p>Once you’re at this screen, make sure to select the manual options for both IP addresses and DNS server addresses and input these addresses as follows:<br>
<br></p>

<table>
<thead>
<tr>
<th>Name</th>
<th>IP Address</th>
</tr>
</thead>
<tbody>
<tr>
<td>IP Address</td>
<td>172.20.241.9</td>
</tr>
<tr>
<td>Subnet Mask</td>
<td>255.255.255.0</td>
</tr>
<tr>
<td>Default Gateway</td>
<td>172.20.241.254</td>
</tr>
<tr>
<td>Preferred DNS Server</td>
<td>8.8.8.8</td>
</tr>
</tbody>
</table><p><img src="/pics/cap%2011.PNG" alt=""></p>
<p>Once you’ve filled in these settings, it should look like this.  Click OK and proceed on.</p>
<p><img src="/pics/cap%2012.PNG" alt=""></p>
<p>Let the installation process complete and allow the machine to reboot.  Once the machine has restarted, login to the computer.  Once logged in, a page should open detailing your next steps for getting the server ready.  Click on “Update this server” and run through the update process.  Once that is done restart your machine.  Finally, watch this helpful video on how to finish setting up the FTP Server since it helped me set it up.</p>
<p><a href="https://www.youtube.com/watch?v=0I7jNC5XIwM">https://www.youtube.com/watch?v=0I7jNC5XIwM</a></p>
<p><a href="../../">Homepage</a></p>

