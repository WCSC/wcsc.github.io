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
<li>Email: <a href="mailto:araujoj@mail.usf.com">araujoj@mail.usf.com</a></li>
</ul>
<h3 id="table">Table</h3>
<ol>
<li><a href="#id-link-to-section">Prerequisites</a></li>
<li><a href="#id0">Summary</a></li>
<li><a href="#id1">Setting up and Installing Windows Server 2003</a></li>
<li><a href="#id2">Creating and Configuring an FTP Server</a></li>
</ol>
<h2 id="prerequisites-a-idid-link-to-sectiona">Prerequisites <a id="id-link-to-section"></a></h2>
<ol>
<li>Have your <a href="https://silexone.github.io/guides/nestor/ISPsetup.html">virtual environment</a> configured</li>
<li>Have the <a href="https://silexone.github.io/guides/william/DNSNotes.html">DNS</a> machine running.</li>
<li>Have <a href="link-to-guide">pfSense</a> running.</li>
</ol>
<h2 id="summary-a-idid0a">Summary <a id="id0"></a></h2>
<p>This guide features the initial setup of the virtual machine, installation of Windows Server 2003, and the creation of FTP servers along with configuring and securing the servers.</p>
<h2 id="setting-up-and-installing-windows-server-2003-a-idid1a">Setting up and Installing Windows Server 2003 <a id="id1"></a></h2>
<p>Before you can setup your FTP server, you must download this ISO file to install the virtual machine.  Once downloaded, open VirtualBox and click on “New” at the top left.  Go through the initial setup for creating the virtual machine similarly to the way you did with the first few boxes.  Just make sure to allow yourself enough memory to be able to work in the environment properly.</p>
<p>Before starting the virtual machine, make sure it is selected and click on “Settings”.  Once you’re in settings, navigate to the “Network” tab and under “Adapter 1”, select “Host-Only Adapter” and choose the adapter representing the LAN.</p>
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
<p>Let the installation process complete and allow the machine to reboot.  Once the machine has restarted, login to the computer.  Once logged in, a page should open detailing your next steps for getting the server ready.</p>
<h2 id="creating-and-configuring-an-ftp-server-a-idid2a">Creating and Configuring an FTP Server <a id="id2"></a></h2>
<p>When you restart the server, you’ll notice a window pops up with details on what to do next.  Click on “Finish” at the bottom right of the page.  Once you’re back at your desktop, click the “Start” button, open up the control panel then click on “Add or Remove Programs”.</p>
<p>Choose “Add/Remove Windows Components”.  Here, you can add or remove all the different components that Windows Server 2003 offer.  The components that we are looking for are within the “Application Server” component.  Once checked, click on “Details” to make sure that “Internet Information Services (IIS)” is checked.  click on the details for IIS and make sure that the FTP service is selected.</p>
<p><img src="/pics/Capture.PNG" alt=""></p>
<p><img src="/pics/Capture1.PNG" alt=""></p>
<p><img src="/pics/Capture2.PNG" alt=""></p>
<p>Click OK and continue through the rest of the installation process and let it finish.  Once that is done, click on the start button and mouse over “Administrative Tools” then click on “Internet Information Services (IIS) Manger”</p>
<p>Here is the main interface in which you’ll be configuring and operating your FTP server.  This also allows you to configure and operate a web server, but for the purposes of this guide, we will stick to FTP exclusively.</p>
<p><img src="/pics/Capture4.PNG" alt=""></p>
<p>Click on your computer on the left panel and a folder names “FTP Sites” should appear.  If you open the folder, you’ll notice that there is already a FTP server running named “Default FTP Site”.  Since we are going to make our own server, you’ll want to stop it and delete it by right-clicking on the site.</p>
<p>Right-click on the “FTP Sites” folder and mouse-over “New”, then click on “FTP Site”.  Add a description for the FTP site that you find appropriate then add the same IP address (172.20.241.9) that you set for the server in the following box and make sure that the site is running on port 21.</p>
<p>Depending on the situation, you’ll want to select the appropriate user isolation policy for this server.  As an example, the SECCDC competition involves an Active Directory server, so in that situation, you’d want to Isolate users using Active Directory, but for the purposes of this tutorial, select “Do not isolate users”.</p>
<p>For security purposes, DO NOT place your home directory for your FTP server in the default “inetpub/ftproot” folder.  Make sure to create a separate directory just for the FTP server and select that as your root.  Finally, set your initial permissions to read and write for now, you’ll be able to change them whenever you’d like.</p>
<p>At this point, you should have a FTP site that is up and running.  Right click on the site and select “Properties”, then click on the “Security Accounts” tab and change the anonymous username and password to test out the service.</p>
<p><img src="/pics/Capture3.PNG" alt=""></p>
<p>Use the Windows 10 client machine to test out the service by going on the web browser and typing in “<a href="ftp://172.20.241.9">ftp://172.20.241.9</a>”.  You should be prompted with a login and by using the anonymous login credentials you previously set, login to the server and place a test file to see if the service works properly.</p>
<p>Now, all that is left is to configure the FTP site accordingly (testing purposes/competition practice) and to secure it.</p>
<p><a href="../../">Homepage</a></p>

