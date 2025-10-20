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

3. In order for osTicket to function, we need to turn on IIS (Internet Information Services) in Windows Features. IIS is a web server software by Microsoft that allows us to host applications like osTicket. However,      just turning on IIS isn't enough. osTicket is written in PHP and IIS isn't capable of processing PHP code, so we will need to enable CGI in Windows Features to allow IIS to interpret PHP code.

   Open Control Panel -> Click Uninstall a program under Programs -> On the left side, click Turn Windows Features on or off -> click dropdown arrow next to Internet Information Services -> dropdown next to World Wide    Web Services -> dropdown next to Application Development Features -> click the checkbox next to CGI -> OK

   <img src="https://i.imgur.com/VNLXWP2.png" alt="IIS -> CGI"/>

4. From the osTicket installtion files, install the PHP manager.

   <img src="https://i.imgur.com/PQUs452.png" alt="install php manager"/>

5. From the osTicket installtion files, install the rewrite module. The rewrite module is an add-on for IIS that lets you control and modify URLs as they come into your web server — without changing the actual files      or folders on your server. Rewrite Module matters for osTicket because it enables clean, user-friendly URLs and proper routing of requests.

   <img src="https://i.imgur.com/rxRk6TL.png" alt="rewrite module"/>
