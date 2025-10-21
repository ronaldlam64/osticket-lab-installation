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
  - <a href="https://youtu.be/JWdxMZ2ldYA?si=vlUt4kZ7qTGyTyXL">How to install and run Windows Pro on Oracle Virtualbox</a>

2. Next, download the <a href="https://drive.google.com/file/d/10VR-lprxALBbs2NOZ94Y_AjS62zHB4rL/view?usp=drive_link">osTicket installation files</a> and unzip to Desktop.

   <img src="https://i.imgur.com/97PREIh.png" alt="Extract to desktop"/>

3. In order for osTicket to function, we need to turn on IIS (Internet Information Services) in Windows Features. IIS is a web server software by Microsoft that allows     us to host applications like osTicket. However, just turning on IIS isn't enough. osTicket is written in PHP and IIS isn't capable of processing PHP code, so we    will need to enable CGI in Windows Features to allow IIS to interpret PHP code.

   Open Control Panel -> Click Uninstall a program under Programs -> On the left side, click Turn Windows Features on or off -> click dropdown arrow next to Internet       Information Services -> dropdown next to World Wide Web Services -> dropdown next to Application Development Features -> click the checkbox next to CGI -> OK

   Also, click the dropdown next to Web Management Tools -> IIS Management Console

   Make sure all features in Common HTTP features are checked.

   If necessary, allow the VM to restart for the changes to take effect. 

   <img src="https://i.imgur.com/VNLXWP2.png" alt="IIS -> CGI"/>

   <img src="https://i.imgur.com/c0RfflA.png" alt="IIS Management Console"/>

   <img src="https://i.imgur.com/Tx1Sc8d.png" alt="Common HTTP features"/>

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

10. From the osTicket installation files, install MySQL 5.5.62. MYSQL is the database app where helpdesk data is stored. 

   <img src="https://i.imgur.com/Q7VMVoY.png" alt="install mysql"/>

11. When MYSQL finishes installing, launch the configuration wizard. Click Standard Configuration -> Install as Windows Service -> Modify Security Settings -> Enter root password as root -> Execute

   <img src="https://i.imgur.com/BhGHAL7.png" alt="configure mysql"/>

12. Open IIS as admin. Click start menu -> Open Internet Information Services (IIS) Manager as administrator.

    <img src="https://i.imgur.com/5HU8ydU.png" alt="IIS manager"/>

13. Register PHP manager withing IIS Manager.

    Click PHP Manager -> Register New PHP version -> Browse through files by clicking the ... box -> Open the PHP folder -> Click php-cgi and Open -> OK

    <img src="https://i.imgur.com/S0m0t0E.png" alt="Manage PHP manager"/>

    On the right, restart the server.

    <img src="https://i.imgur.com/OQnYen4.png" alt="restart IIS"/>

14. From the osTicket installation files, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”. Then rename "upload" to "osTicket". Restart IIS Manager

    <img src="https://i.imgur.com/E53DQ9m.png" alt="unload upload" />

15. 
