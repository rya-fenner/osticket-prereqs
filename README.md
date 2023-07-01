<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>
1.) Begin by creating a virtual machine (VM) by going to https://portal.azure.com/. Setup your virtual machine with Windows 10 Pro, version 22H2. 
<b>Note: you should create a virtual machine with at least 2 vcpus and 16 GiB of memory.</b>
<p></p>
2.) Once you have created your virtual machine, connect to it by using the public IP address of the VM which can be found by clicking on the VM's name in Azure. You will connect to the VM by entering the public IP address into the remote desktop connection app in Windows.
</p>
<br />

<p>

<img src="https://imgur.com/GxzVn0K.png" alt="osTicket logo"/>


</p>
<p>
<p>
  
<img src="https://imgur.com/tWQoa3t.png" alt="osTicket logo"/>


</p>
<p>
  
3.) After connecting to and setting up the VM go to the control panel. From the control panel select "programs". Then select "Turn Windows features on and off".

<p>

<img src="https://imgur.com/25ndQZ8.png" alt="osTicket logo"/>

</p>
<p>
  
<img src="https://imgur.com/rCLOIuT.png" alt="osTicket logo"/>

</p>
<p>
  
4.) Next you will need to install / enable IIS in Windows along with CGI and <b>ALL</b> Common HTTP Features

<p>
  
<img src="https://imgur.com/N3z5e0g.png" alt="osTicket logo"/>

</p>
<p>
 
 To test if the IIS is installed / enabled properly, go to a browser and type 127.0.0.1 into the search bar.
 You should see this: 
  
<p>
  
<img src="https://imgur.com/SFYB1Bi.png" alt="osTicket logo"/>

</p>
<p>
  
5.) From the provided list of downloads above, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
  
6.) Next from the same list of downloads, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
  
7.) Create a folder in the C drive and title it "PHP".

<p>

<img src="https://imgur.com/LsGX4o5.png" alt="osTicket logo"/>
  
</p>
  
8.) From the list of downloads, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP
  
9.) After extracting the zip file into the PHP folder, download and install the VC_redist.x86.exe from the list of downloads.
  
10.) Next, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi).  Run the setup wizard selecting "Typical Setup" and then "Launch Configuration Wizard" followed by "Standard Configuration".

Make the new root password: <b>Password1</b>
  
<p>
  
<img src="https://imgur.com/xnHYRad.png" alt="osTicket logo"/>

</p>
<p>
  
Execute the process.
  
</p>
<p>
  
11.) Next search for IIS in the windows search bar and open it as administrator.

<p>

<img src="https://imgur.com/G3ebCl3.png" alt="osTicket logo"/>

</p>
<p>
  
12.) Register PHP from within IIS by selecting "PHP Manager" and then "Register new PHP version".
  
<p>

<img src="https://imgur.com/wku9JQW.png" alt="osTicket logo"/>

</p>
<p>

<img src="https://imgur.com/BmfOkiA.png" alt="osTicket logo"/>

</p>

<p>
  
You should provide a path to the PHP executable file (php-cgi.exe) by going to the C Drive, then PHP folder and clicking on the php-cgi file.
  
<p>

<img src="https://imgur.com/DwStgn2.png" alt="osTicket logo"/>

</p>
<p>
  
Restart the IIS server.
  
<p>

<img src="https://imgur.com/o5lidAO.png" alt="osTicket logo"/>

</p>
<p>
  
13.) Download osTicket from the provided list of downloads. Extract and copy "Upload" folder to c:\inetpub\wwwroot. Within c:\inetpub\root rename "Upload" to "osTicket".
  
Restart the IIS server again.
  
14.) Within IIS expand "Sites", then "Default", and finally "osTicket".  In the right column, select “Browse *:80 (http)”
  
<p>

<img src="https://imgur.com/60Hfno4.png" alt="osTicket logo"/>

</p>
<p>
  
You will observe that some recommended extensions are not enabled on the osTicket browser.
  
<p>

<img src="https://imgur.com/UIh8Fji.png" alt="osTicket logo"/>

</p>
<p>
  
To enable the necessary extensions return to IIS.  Select "Sites", then "Default", and then "osTicket".  Double click "PHP manager" then "Enable or disable an extension"
  
<p>
  
Enable the following extensions:
  
- php_imap.dll
 
- php_intl.dll
  
- php_opcache.dll
  
<p>

<img src="https://imgur.com/DL2H8Rl.png" alt="osTicket logo"/>

</p>
<p>
  
  
15.) Next you will need to rename one of the files in the osTicket folder by going to the file explorer and searching for C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
Rename this file ost-config.php.
  
Right click on the file and select "Properties".  
From there click "Security" then "Advanced".

<p>

<img src="https://imgur.com/TmNgtXp.png" alt="osTicket logo"/>

</p>
<p>

Remove all inherited permissions from this object by clicking "Remove all inherited permissions from this object".

<p>

<img src="https://imgur.com/su4bwVj.png" alt="osTicket logo"/>

<p>
  
Now add new permissions by selecting "Add".
  
<p>

<img src="https://imgur.com/JUp1eYz.png" alt="osTicket logo"/>

</p>
<p>
  
Select a principal.
  
<p>

<img src="https://imgur.com/Uwrt3Xk.png" alt="osTicket logo"/>

</p>
<p>
  
  
Enter "Everyone" into the box and click "OK".
  
<p>

<img src="https://imgur.com/THAuy1h.png" alt="osTicket logo"/>

</p>
<p>
  
Check all boxes and click "OK".
  
<p>

<img src="https://imgur.com/SSdD4ne.png" alt="osTicket logo"/>

</p>
<p>
  
Click "Apply" and then "OK".
  
<p>
  
To continue setting up osTicket in the browser click "Continue" on the osTicket browser page.
Fill out the page as required ignoring (for now) "Database Settings" at the bottom of the page.
  
Next, you need to download, install, and launch HeidiSQL from the provided downloads. 
  
<p>
  
Once the program is launched, create a new session in it.
  
<p>

<img src="https://imgur.com/1PIJAHv.png" alt="osTicket logo"/>

</p>
<p>
  
Set the user to "root" and the password to "Password1".  Click "Open".
  
<p>

<img src="https://imgur.com/S1gtxD1.png" alt="osTicket logo"/>

</p>
<p>
  
Once connected, return to the browser to finish setting everything up. 

Under "Database Settings" enter the user "root" and the password "Password1".
  
Next you need to create a new database within HeidiSQL. In HeidiSQL, right click "Unnamed" on the left side, select "Create new", and then select "Database". 

<p>

<img src="https://imgur.com/TWLA3Ep.png" alt="osTicket logo"/>

<p>

Name the new database "osTicket". 

Return to the osTicket browser and under MySQL Database type in "osTicket".
  
<p>

<img src="https://imgur.com/Vd4s9T0.png" alt="osTicket logo"/>

</p>
<p>
  
The last step is to do some clean up.  Start by deleting the setup folder. Delete: C:\inetpub\wwwroot\osTicket\setup
  
Next, set the permissions back to "Read" only in the ost-config.php file.
  
<p>

<img src="https://imgur.com/NjMa2bP.png" alt="osTicket logo"/>

</p>
<p>
  
<p>

<img src="[https://imgur.com/Vd4s9T0](https://imgur.com/IShGSpF).png" alt="osTicket logo"/>

</p>
<p>
  
Finally, login to osTicket in the browser.
  
<p>
<img src="https://imgur.com/uHVdDsx.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Congratulations! You have successfully installed and setup osTicket.
