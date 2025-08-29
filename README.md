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

- mySQL: The database which will contain the data from osTicket.
- HeidiSQL: The database manager or GUI we will use to interact with the database.
- PHP: The server-side scripting language used to display the HTML webpages of osTicket.
- PHP Manager: This allows us to interact with the scripts through the Management Console.
- VC Redist: Provides the necessary runtime components for running C++ applications, essential for certain dependencies of PHP and IIS.
- Rewrite: (URL Rewrite Module for IIS) Allows for the customization of URLs, enabling redirection and URL rewriting for osTicket.
- 

<h2>Project Outline</h2>

- Prepare The Windows 10 OS by turning it into a web server.
- Install Prerequisite Programs. (mySQL, HeidiSQL, PHP, PHP Manager, VC Redist, Rewrite)
- Install osTicket and confirm it is a website running on this web server.
- Enable Features and assign permissions to osTicket.
- Complete installation by registering email and mySQL database.
- Confirm osTicket can be reached by users on LocalHost.
- Clean up files that pose a security risk.

<h2>Installation Steps</h2>

<p>
<img width="310" height="227" alt="image" src="https://github.com/user-attachments/assets/bd7f4af5-6492-40b8-b714-1e9976e9ead7" />

</p>
<p>
Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
We will use the files in this folder to install osTicket and some of the dependencies.

</p>
<br />

<p>
<img width="1153" height="651" alt="Screenshot 2025-08-28 220003" src="https://github.com/user-attachments/assets/ee9a14e4-65e1-46b3-a9c3-916e140c41df" />

</p>
<p>
Install / Enable IIS in Windows WITH CGI

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next We want to Install the rest of the prerequisites 
  
  PHP is a server-side scripting language designed for web development. It is embedded within HTML to manage dynamic content, databases, session tracking, and even build entire e-commerce sites. PHP scripts are executed on the server, and the result is sent to the client as plain HTML. This allows for the creation of dynamic and interactive web pages. PHP is widely used due to its ease of integration with various databases, flexibility, and large community support.

  rewrite_amd64_en_us is part of Microsoft’s IIS URL Rewrite Module (64-bit, English) that’s used for redirecting or rewriting web addresses on a server.


  
</p>
<br />
