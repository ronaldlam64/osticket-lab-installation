<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environment and Technologies used</h2>

- osTicket
- <a href="https://knowledge.broadcom.com/external/article/344595/downloading-and-installing-vmware-workst.html">VMWare Workstation</a>
- <a href="https://drive.google.com/drive/folders/1hHvZopC54WQNf1yKBCvyFgn1ZHj8w4Qc?usp=drive_link">Windows 10 Enterprise Edition</a>

<h2>Installation steps</h2>

1. First, if you haven't already done so, please setup a virtual machine running at least Windows 10 or 11 Pro Edition. I am using Windows 10 Enterprise Edition for my VM. For the sake of time, I won't show how to install and setup the VM, but I've provided download links in the Environment and Technologies used section as well as video links below for instructions.

  - <a href="https://youtu.be/EMuw_IN-UOU?si=intt7per4Ua5KODH">How to install and run Windows Pro on VMWare Workstation</a><br />

2. Next, download the <a href="https://drive.google.com/file/d/10VR-lprxALBbs2NOZ94Y_AjS62zHB4rL/view?usp=drive_link">osTicket installation files</a> and unzip to Desktop.

   <img src="https://i.imgur.com/97PREIh.png" alt="Extract to desktop"/>

3. In order for osTicket to function, we need to turn on IIS (Internet Information Services) in Windows Features. IIS is a web server software by Microsoft that allows     us to host applications like osTicket. However, just turning on IIS isn't enough. osTicket is written in PHP and IIS isn't capable of processing PHP code, so we    will need to enable CGI in Windows Features to allow IIS to interpret PHP code.

   Open Control Panel -> Click Uninstall a program under Programs -> On the left side, click Turn Windows Features on or off -> click dropdown arrow next to Internet       Information Services -> dropdown next to World Wide Web Services -> dropdown next to Application Development Features -> click the checkbox next to CGI -> OK

   Also, click the dropdown next to Web Management Tools -> IIS Management Console

   Click the checkbox for all the other IIS features such as Common HTTP Features, Health & Diagnostics, etc. 

   If necessary, allow the VM to restart for the changes to take effect. 

   <img src="https://i.imgur.com/VNLXWP2.png" alt="IIS -> CGI"/>

   <img src="https://i.imgur.com/c0RfflA.png" alt="IIS Management Console"/>

   <img src="https://i.imgur.com/DM2RuPf.png" alt="Other IIS features"/>

5. From the osTicket installtion files, install the PHP manager.

   <img src="https://i.imgur.com/PQUs452.png" alt="install php manager"/>

6. From the osTicket installtion files, install the rewrite module. The rewrite module is an add-on for IIS that lets you control and modify URLs as they come into your web server — without changing the actual files or folders on your server. Rewrite Module matters for osTicket because it enables clean, user-friendly URLs and proper routing of requests.

   <img src="https://i.imgur.com/rxRk6TL.png" alt="rewrite module"/>

7. Create the directory C:\PHP to place the PHP files.

   Click This PC on the left in File Explorer -> Local Disk (C:) -> Right Click -> New - Folder - Rename folder as PHP

   <img src="https://i.imgur.com/uoHNS7K.png" alt="create php folder"/>

8. From the osTicket installation files, unzip the PHP 7.3.8 in the PHP folder created in step 7.

   <img src="https://i.imgur.com/AjpqpLj.png" alt="unzip into php folder"/>

9. From the osTicket installation files, install VC_redist.x86.exe.

   <img src="https://i.imgur.com/jorklAZ.png" alt="vc_redist.x86.exe" />

10. From the osTicket installation files, install MySQL 5.5.62. MYSQL is the database app where helpdesk data is stored. **Make sure user and password are both root.**

   <img src="https://i.imgur.com/Q7VMVoY.png" alt="install mysql"/>

11. When MYSQL finishes installing, launch the configuration wizard. Click Standard Configuration -> Install as Windows Service -> Modify Security Settings -> Enter root password as root -> Execute

   <img src="https://i.imgur.com/BhGHAL7.png" alt="configure mysql"/>

12. Open IIS as admin. Click start menu -> Open Internet Information Services (IIS) Manager as administrator.

    <img src="https://i.imgur.com/9FXKaam.png" alt="IIS manager"/>

13. Register PHP manager withing IIS Manager.

    Click PHP Manager -> Register New PHP version -> Browse through files by clicking the ... box -> Open the PHP folder -> Click php-cgi and Open -> OK

    <img src="https://i.imgur.com/VbWhgzT.png" alt="Manage PHP manager"/>

    On the right, restart the server.

    <img src="https://i.imgur.com/Nmykmnd.png" alt="restart IIS"/>

14. From the osTicket installation files, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”. Then rename "upload" to "osTicket". Restart IIS Manager

    <img src="https://i.imgur.com/E53DQ9m.png" alt="unload upload" />

15. Go to sites -> Default -> osTicket. On the right, click “Browse *:80”

    <img src="https://i.imgur.com/Yu9cQsy.png" alt="find osticket in IIS" />

16. Some extensions in PHP manager need to be enabled in order for osTicket to work. In IIS, go to PHP manager -> Enable or disable an extension -> Enable the following extensions: php_imap.dll, php_intl.dll, and php_opcache.dll. Refresh osTicket in the browser.

    <img src="https://i.imgur.com/SikuMB4.png" alt="enable php extensions" />

    <img src="https://i.imgur.com/n3RPmI8.png" alt="osticket upon loading" />

17. From file explorer, go to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename ost-sampleconfig.php to ost-config.php

    <img src="https://i.imgur.com/gBzy71W.png" alt="renaming file" />

    ost-sampleconfig.php is a default template and tt contains the basic structure (variables and placeholders) osTicket needs to connect to your database and set up initial settings.

    ost-config.php is the active configuration file and is used to store the real settings for the helpdesk.

18. For the purposes of this lab, let's give everyone permission to edit the os-config.php file. Right click on os-config.php file -> Properties -> Security tab -> Advanced -> Disable inheritance -> Remove all inherited permissions from this object.

    <img src="https://i.imgur.com/fgjBDVH.png" alt="Disable inheritance" />

    Click Add under the Permissions tab -> Select a principal -> type everyone in the "enter the object name" box -> click Check Names -> OK -> Apply -> OK
    **Don't everyone full control in a real work setting**

    <img src="https://i.imgur.com/KSnXlDQ.png" alt="Giving everyone permission" />

19. Fill the next page with the appropriate info

    <img src="https://i.imgur.com/0ToYbtF.png" alt="setting up osticket" />

20. We need to login into MySQL and create a database just for osTicket.

    Go to the osTicket installation files and install HeidiSQL, which will create a connection between osTicket and the MySQL database.

    <img src="https://i.imgur.com/PaqMOWt.png" alt="HeidiSQL" />

    Open HeidiSQL -> Click New -> Make sure user and password are both root -> Open -> Right click Unnamed -> Create new -> Database -> name the database as osTicket (spell exactly as osTicket) -> click OK

    <img src="https://i.imgur.com/oDFraoi.png" alt="creating database" />

21. Back in the browser, fill the Database settings section with the following info and then click Install Now

    Database: osTicket
    User: root
    Password: root

    <img src="https://i.imgur.com/rfAbOpI.png" alt="database settings" />

22. Click open and bookmark the following links.

    Admin link: http://localhost/osTicket/scp/login.php

    username and password to login are from step 19

    <img src="https://i.imgur.com/y4OXb4L.png" alt="Admin login" />

    Enduser link for users to create tickets: http://localhost/osTicket/

    <img src="https://i.imgur.com/9slG5RP.png" alt="Enduser login" /> 

Congratulations, you have successfully installed osTicket!

<img src="https://i.imgur.com/arf28y2.png" alt="installed osTicket" />
