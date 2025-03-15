<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

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

<h2>Installation Steps</h2>

1.) The first step is to create a virtual machine by visiting https://portal.azure.com/. Configure your virtual machine using Windows 10 Pro, version 22H2. Ensure that the virtual machine has at least 2 vCPUs and 16 GBs of memory.

2.) Once you have created your virtual machine, you will want to connect to it using the public IP address with which the VM is set up. You can connect through the Remote Desktop Connection application.

<p>
<img src="https://i.imgur.com/dvANTqj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/HizznRf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


<p>
  
3.) Once connected to your virtual machine, navigate to the control panel. Within the control panel, access programs and choose 'Turn Windows features on or off'.

  
<p>
<img src="https://imgur.com/fGXMpx4.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/LBGkAw6.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

4.) To install/enable IIS on Windows with CGI and Common HTTP Features, follow these steps:
  - Navigate to World Wide Web Services -> Application Development Features, then select:
[X] CGI
[X] Common HTTP Features

<p>
<img src="https://imgur.com/LQjw9le.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/pbPeHb1.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  ***NOTE*** Be sure that all Common HTTP Features are selected.

To verify that IIS is installed and enabled, open a browser and navigate to 127.0.0.1; the page should display the default IIS welcome screen.


<p>
<img src="https://imgur.com/J3AILEQ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<p>

5.) With IIS now enabled, proceed to download and install the PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) from the Installation Files. Follow the installation wizard to completion.

<p>
<img src="https://i.imgur.com/7CKKobF.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

6.) Then, from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi).

<p>
<img src="https://i.imgur.com/WUWLs9Z.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
7.) Create a new folder on the C drive and name it PHP.

8.) Download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) from the Installation Files and extract the contents into the C:\PHP folder.

!! ATTENTION !!
If prompted, select "Keep" to retain the file

<p>
<img src="https://imgur.com/xZv1Yhw.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

9.) After downloading and extracting the zip file into the PHP folder on the C drive, proceed to download and install VC_redist.x86.exe from the installation files. Complete the setup by following the setup wizard for VC_redist.x86.exe.

<p>
<img src="https://imgur.com/sGDpqbL.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

10.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi). Execute the setup wizard with the following steps:
- Choose Typical Setup
- Launch the Configuration Wizard post-installation
- Select Standard Configuration

Set the new root password to 'Password1'.

<p>
<img src="https://i.imgur.com/eds9E1o.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/CMcsc6a.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

11.) Having downloaded and installed the files, we should now search for IIS in the Windows search bar. Open IIS with administrator privileges. The program interface should appear as expected.

<p>
<img src="https://i.imgur.com/gBMdeNt.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

12.) We now need to register PHP within IIS.
- Click on the PHP Manager
- Register new PHP version
- To specify the path to the PHP executable file (php-cgi.exe), navigate to the C Drive, then to the PHP folder, and select the php-cgi file.
-  A then restart the IIS server.

13.) Install osTicket v1.15.8:
  - Download osTicket from the Installation Files Folder.
  - Extract and copy the "upload" folder to c:\inetpub\wwwroot.
  - Within c:\inetpub\wwwroot, rename "upload" to "osTicket".

<p>
<img src="https://i.imgur.com/kXKLpZ4.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

  Reload IIS.

14.) In IIS, navigate to Sites -> Default Web Site -> osTicket:
  - On the right-hand side, click “Browse *:80 (http)”.

<p>
<img src="https://imgur.com/Yw55d5b.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

Certain extensions are not enabled in the osTicket browser.

To enable the extensions:
- Return to IIS, navigate to Sites -> Default Web Site -> osTicket.
- Double-click on PHP Manager.
- Choose "Enable or disable an extension."

<p>
<img src="https://i.imgur.com/tgleJCd.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

To proceed, we need to enable three extensions:

1. php_imap.dll
2. php_intl.dll
3. php_opcache.dll

<p>
<img src="https://i.imgur.com/xuW1oAe.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

15.) After enabling the necessary extensions in IIS, we need to rename a file within our osTicket folder. Navigate to the file explorer and locate C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php.

We will rename ost-sampleconfig.php to ost-config.php.

Following the file renaming, right-click on the file and select properties. Then, click on the security tab, select advanced, and disable inheritance. Choose to remove all inherited permissions from this object.

Next, we will proceed to add new permissions.

- Click on Add.
- Select a principal
- Type "Everyone" in the box.
- Ensure that Full Control is enabled and all other options are selected.
- Click Apply and Ok.

Once that is completed, the next step is to set up osTicket in the browser. Click 'Continue' on the osTicket browser page. Complete the required fields on the page, except for the Database Settings at the bottom; those will be addressed later. 

Next, proceed to download and install HeidiSQL from the Installation Files.

<p>
<img src="https://i.imgur.com/L9TxKBd.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

Once the program is open, we will initiate a new session within it.
- Ensure that the username is set to 'root' and the password is 'Password1'.
- Once connected to the session, return to the browser to complete the setup. In the Database Settings of the browser, use 'root' as the username and 'Password1' as the password.
- To create a new database in HeidiSQL, right-click on the "Unnamed" section on the left side, choose "Create New," and then select "Database." Name the new database "osTicket." After setting up the new database, return to the osTicket browser and enter "osTicket" in the MySQL Database field.

16.) The final step involves cleanup. We need to remove the setup folder from our system.
  - Delete: C:\inetpub\wwwroot\osTicket\setup
  Ensure only the setup folder is deleted.

Afterwards, we should revert the permissions of the ost-config.php file to "Read" only.

17.) The final step is to log in to osTicket via the browser.

<p>
<img src="https://i.imgur.com/GW3WGqx.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/09t8mmM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

This action will direct you to the osTicket login page, where you can sign in and begin utilizing the application.
