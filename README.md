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
  
![Screenshot 2023-06-30 142454](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/7551a5f7-e711-47b6-9a44-06db8a36dad3)

</p>
<p>
<p>
  
![Screenshot 2023-06-30 143334](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/5b420889-e02e-406d-8dd5-1379f49cce99)

</p>
<p>
  
3.) After connecting to and setting up the VM go to the control panel. From the control panel select "programs". Then select "Turn Windows features on and off".

<p>
  
![Screenshot 2023-06-30 143858](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/85f9c9a5-1782-4784-9b97-8e8fcb28cbfe)

</p>
<p>
  
<p>
  
![Screenshot 2023-06-30 143836](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/b4faa255-2702-4a27-b416-e0d61f0d4161)

</p>
<p>
  
4.) Next you will need to install / enable IIS in Windows along with CGI and <b>ALL</b> Common HTTP Features

<p>
  
![Screenshot 2023-06-30 144823](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/1282f875-6369-4b34-845d-365c785a8f86)

</p>
<p>
 
 To test if the IIS is installed / enabled properly, go to a browser and type 127.0.0.1 into the search bar.
 You should see this: 
  
<p>
  
![Screenshot 2023-06-30 145558](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/1bd56a76-cb31-4d17-a03d-e4190e327c02)


</p>
<p>
  
5.) From the provided list of downloads above, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
  
6.) Next from the same list of downloads, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
  
7.) Create a folder in the C drive and title it "PHP".

<p>

![Screenshot 2023-06-30 150754](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/e82f3e9d-8285-45c6-87b2-1b7b5e1127d8)
  
</p>
  
8.) From the list of downloads, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP
  
9.) After extracting the zip file into the PHP folder, download and install the VC_redist.x86.exe from the list of downloads.
  
10.) Next, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi).  Run the setup wizard selecting "Typical Setup" and then "Launch Configuration Wizard" followed by "Standard Configuration".

Make the new root password: <b>Password1</b>
  
<p>
  
![Screenshot 2023-06-30 151750](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/4d51006e-36a6-4124-bb64-831f6bbce818)

</p>
<p>
  
Execute the process.
  
</p>
<p>
  
11.) Next search for IIS in the windows search bar and open it as administrator.

<p>
  
![Screenshot 2023-06-30 152258](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/a4e83ffb-202b-4fa5-baad-e45bee93ae0f)

</p>
<p>
  
12.) Register PHP from within IIS by selecting "PHP Manager" and then "Register new PHP version".
  
<p>
  
![Screenshot 2023-06-30 152741](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/8b500888-f14c-4f2e-9975-c1a29313088e)

</p>
<p>

![Screenshot 2023-06-30 152913](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/bdc4e2ff-bb86-497e-9027-4c6dc9a294ce)

</p>

<p>
  
You should provide a path to the PHP executable file (php-cgi.exe) by going to the C Drive, then PHP folder and clicking on the php-cgi file.
  
<p>
  
![Screenshot 2023-06-30 153347](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/77e869bc-6d45-41e8-93d9-3fe691e949cf)

</p>
<p>
  
Restart the IIS server.
  
<p>
  
![Screenshot 2023-06-30 155830](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/4dff4de4-dd08-423d-a88c-67d919a1b1a7)


</p>
<p>
  
13.) Download osTicket from the provided list of downloads. Extract and copy "Upload" folder to c:\inetpub\wwwroot. Within c:\inetpub\root rename "Upload" to "osTicket".
  
Restart the IIS server again.
  
14.) Within IIS expand "Sites", then "Default", and finally "osTicket".  In the right column, select “Browse *:80 (http)”
  
<p>
  
![Screenshot 2023-06-30 160647](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/96ab3b2c-a770-4e82-8c2c-07ce53af5bc5)

</p>
<p>
  
You will observe that some recommended extensions are not enabled on the osTicket browser.
  
<p>
  
![Screenshot 2023-06-30 161111](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/d04b8e3d-7765-49d0-bcf9-ff2e46ad1e04)


</p>
<p>
  
To enable the necessary extensions return to IIS.  Select "Sites", then "Default", and then "osTicket".  Double click "PHP manager" then "Enable or disable an extension"
  
<p>
  
Enable the following extensions:
  
- php_imap.dll
 
- php_intl.dll
  
- php_opcache.dll
  
<p>

![Screenshot 2023-06-30 161507](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/4c68e1a3-0ca7-4c62-9a2e-426bd04539af)

</p>
<p>
  
  
15.) Next you will need to rename one of the files in the osTicket folder by going to the file explorer and searching for C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
Rename this file ost-config.php.
  
Right click on the file and select "Properties".  
From there click "Security" then "Advanced".

<p>

![Screenshot 2023-06-30 162302](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/559a8df5-0f87-49f6-9961-3c9acffac14f)

</p>
<p>

Remove all inherited permissions from this object by clicking "Remove all inherited permissions from this object".

<p>

![Screenshot 2023-06-30 162344](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/653819b4-ac60-4fd0-88b9-e70a3c99ced2)

<p>
  
Now add new permissions by selecting "Add".
  
<p>
  
![Screenshot 2023-06-30 162829](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/a41be098-1365-4884-bed1-8246ba729cd8)

</p>
<p>
  
Select a principal.
  
<p>
  
![Screenshot 2023-06-30 163405](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/cedd1941-9aa9-401b-85b6-16aed5ecc2ec)

</p>
<p>
  
  
Enter "Everyone" into the box and click "OK".
  
<p>
  
![Screenshot 2023-06-30 163532](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/9c8bf06e-54db-4a42-8a0b-417fedc90a5d)

</p>
<p>
  
Check all boxes and click "OK".
  
<p>
  
![Screenshot 2023-06-30 163804](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/fc6bce4e-5cf5-4b8b-a544-0295431ffe29)

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
  
![Screenshot 2023-06-30 164614](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/4099b503-923d-4d99-9acc-4b244263b82e)

</p>
<p>
  
Set the user to "root" and the password to "Password1".  Click "Open".
  
<p>

![Screenshot 2023-06-30 164755](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/25e82c16-ab96-4b41-aa1a-d6e2817f6591)

</p>
<p>
  
Once connected, return to the browser to finish setting everything up. 

Under "Database Settings" enter the user "root" and the password "Password1".
  
Next you need to create a new database within HeidiSQL. In HeidiSQL, right click "Unnamed" on the left side, select "Create new", and then select "Database". 

<p>

![Screenshot 2023-06-30 165150](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/788dad7d-bcd0-4636-82e8-d1c38cc292ab)

<p>

Name the new database "osTicket". 

Return to the osTicket browser and under MySQL Database type in "osTicket".
  
<p>
  
![Screenshot 2023-06-30 165406](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/3fa527d4-5d66-4925-b3d6-92caaa3b66e6)

</p>
<p>
  
The last step is to do some clean up.  Start by deleting the setup folder. Delete: C:\inetpub\wwwroot\osTicket\setup
  
Next, set the permissions back to "Read" only in the ost-config.php file.
  
<p>
  
![Screenshot 2023-06-30 165823](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/4bfe4773-4ab1-43a1-a3c4-3c7aca73f582)

</p>
<p>
  
<p>
  
![Screenshot 2023-06-30 165847](https://github.com/rya-fenner/osticket-prereqs/assets/136194969/492019cf-d8fe-4e98-bc48-ebac68939e90)

</p>
<p>
  
Finally, login to osTicket in the browser.
  
<p>
<img src="https://imgur.com/uHVdDsx.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Congratulations! You have successfully installed and setup osTicket.
