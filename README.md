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
- osTicket Installation Files: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Steps</h2>

1. Create a virtual machine in Azure (https://portal.azure.com/). Set up your virtual machine using Windows 10 Pro, with at least 2 vcpus and 16 GBs of memory.

2. Using the remote desktop connection app, connect to your VM by using the public IP address the VM is set up with.

3. Go to "Control Panel", inside your VM, and open up programs. Select "Turn Windows features on and off" and install/enable Internet Information Services (IIS) in Windows with CGI (in a subfolder labeled "Application Development Features") and ensure all Common HTTP Features are also installed/enabled.

4. From the Installation Files provided under "List of Prerequisites", download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi). Once installed, download and install the Rewrite Module (rewrite_amd64_en-US.msi), also found in the Installation Files provided above.

5. Create a folder in the C drive called PHP. Then, from the Installation Files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into the folder created in the C drive: C:\PHP. If any of the downloads get a yellow/orange triangle next to the download, ensure you "Keep" the file instead of deleting it.

6. From the Installation Files, download and install the VC_redist.x86.exe. Once installed, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the Instillation Files. (Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->)

7. Search for IIS in the Windows search bar and open IIS as an administrator. Open "PHP Manager" and click on "Register new PHP version" and provide a path to the PHP executable file (php-cgi.exe) by going to C Drive -> PHP -> php-cgi.exe.

8. Stop the IIS server.

9. Download osTicket from the Installation Files Folder, extract and copy the folder titled "upload" to c:\inetpub\wwwroot, and then rename "upload" to "osTicket"

10. Reload IIS and go to sites -> Default -> osTicket. On the right of the screen, click "Browse *:80" and note how some extensions are not enabled.

11. Go back to IIS (sites -> Default -> osTicket), double-click "PHP Manager", click on "Enable or disable an extension” and enable php_imap.dll, php_intl.dll, and php_opcache.dll.

12. Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php, rename "ost-sampleconfig.php" to "ost-config.php", and then right-click on the file to go into "Properties"

13. Inside "Properties" click on Security, then Advanced, and disable inheritance -> remove all. Then to add new permissions, "Everyone" in this example, click "Add" -> "Select a principal" Enter "Everyone" into the box labeled "Enter the object name to select (examples):", make sure "Full Control" and all the other boxes are checked. Click on "Apply" and "OK" to finalize all of the changes made.

14. Go to your osTicket browser page (http://SERVER/osticket "SERVER" being the domain or IP address of the hosting server). Click Continue on the osTicket browser page and fill out the page as required except the Database Settings at the bottom of the page.

15. Download and install HeidiSQL from the Installation Files. When the program opens create a new session in it using the Username and Password you used when setting up MySQL.

16. Create a new database within HeidiSQL. Inside Heidi, on the left side where it says "Unnamed", right-click and select "Create new", then "Database", and name the new database osTicket. Once we have the new database setup go back to the osTicket browser (http://SERVER/osticket "SERVER" being the domain or IP address of the hosting server) and under MySQL Database type in osTicket.

17. Delete the setup folder in our system. -Delete: C:\inetpub\wwwroot\osTicket\setup. ONLY DELETE THE SETUP FOLDER, NOTHING ELSE!

18. You can then set the permissions back to "Read Only" for "Everyone" in the ost-config.php file.

19. Login to osTicket on the browser (http://SERVER/osticket "SERVER" being the domain or IP address of the hosting server).
