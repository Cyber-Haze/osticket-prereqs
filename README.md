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

<h2>Prepare The Windows 10 OS by turning it into a web server</h2>

<p>
<img width="1153" height="651" alt="Screenshot 2025-08-28 220003" src="https://github.com/user-attachments/assets/ee9a14e4-65e1-46b3-a9c3-916e140c41df" />

</p>
<p>
Install / Enable IIS in Windows WITH CGI

</p>
<br />

<h2>Install Prerequisite Programs. (mySQL, HeidiSQL, PHP, PHP Manager, VC Redist, Rewrite)</h2>

<p>
<img width="310" height="227" alt="image" src="https://github.com/user-attachments/assets/bd7f4af5-6492-40b8-b714-1e9976e9ead7" />

</p>
<p>
Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
We will use the files in this folder to install osTicket and some of the dependencies.

</p>
<br />

<h2></h2>

<p>
Next We want to Install the a few more of the prerequisites from the install folder. 
  
1. Install PHP Manager for IIS
2. Install the Rewrite Module rewrite_amd64_en_us
3. Install VC Redist

<p>
<img width="912" height="356" alt="Screenshot 2025-09-01 212821" src="https://github.com/user-attachments/assets/ba1b9c58-3d74-428b-bb5f-e03180a4247d" />
<img width="872" height="313" alt="Screenshot 2025-09-01 213054" src="https://github.com/user-attachments/assets/ed602000-2d3f-46a6-a71d-8c386649ac58" />
<img width="650" height="216" alt="Screenshot 2025-09-01 213419" src="https://github.com/user-attachments/assets/83ae2b34-b461-4a35-a324-163947caab9f" />

</p>

4. Install PHP:
    - Create the directory C:\PHP
    - Unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
    - Open IIS as an Admin
    - Register PHP from within IIS
    - Reload IIS (Open IIS, Stop and Start the server)
<h2></h2>

5. Install mySQL:
    - Typical Setup
    - Launch Configuration Wizard (after install) ->
    - Standard Configuration
    - Create Secret Password for "root" access
  
<h2></h2>

<p>
<img width="684" height="478" alt="Screenshot 2025-09-01 214744" src="https://github.com/user-attachments/assets/9ab0b844-da70-4576-8df0-5b66f97dc2d2" />
<img width="936" height="624" alt="Screenshot 2025-09-01 215243" src="https://github.com/user-attachments/assets/d3de7d12-89e5-41f3-a527-30d46632f37b" />
<img width="318" height="258" alt="image" src="https://github.com/user-attachments/assets/b0e75052-e594-4362-9085-c80f31c1a625" />
  
</p>

6. Install HeidiSQL
    - Create a new session (root user + Secret Password)
    - Connect to the session.
    - Create a database called "osTicket".
  
</p>
<br />

<h2>Install osTicket and confirm it is a website running on this web server</h2>


<p>

1. Install osTicket
     - Extract osTicket-v1.15.8.zip from installation file folder
     - Within the Osticket folder, Copy the "upload" folder into  “c:\inetpub\wwwroot”
     - Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
     - Reload IIS (Open IIS, Stop and Start the server)
2. Confirm osTicket is running through web server:
     -  Go to sites -> Default -> osTicket
     -  On the right, click “Browse *:80”
     -  Note some extensions arent active.

<p>
<img width="1040" height="332" alt="Screenshot 2025-09-01 222746" src="https://github.com/user-attachments/assets/13cb538d-3eeb-41f2-b2af-1ffa465e6d3c" />
<img width="819" height="735" alt="image" src="https://github.com/user-attachments/assets/8a358362-1ca3-4c05-85be-d4f6b03853ca" />
</p>
</p>
<br />

<h2>Enable Features and assign permissions to osTicket</h2>


<p>
<img width="754" height="383" alt="Screenshot 2025-09-01 223658" src="https://github.com/user-attachments/assets/f5e0fd64-58d5-4807-94a9-a2588046e390" />

</p>
<p>

1. Enable Extensions in PHP Manager:
   - Enable: php_imap.dll
   - Enable: php_intl.dll
   - Enable: php_opcache.dll
   - Refresh the osTicket site in your browser, observe the changes

<p>
<img width="820" height="732" alt="image" src="https://github.com/user-attachments/assets/191f1447-d015-486a-8550-23ca9ade8b10" />

</p>
<p>  

2. Rename: ost-config.php
   - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
   - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
  
3. Assign Permissions: ost-config.php
   - Right click -> Properties -> Security -> Advance
   - Disable inheritance -> Remove All.
   - Add New Permissions -> Select a Principan -> Everyone -> All. (or whichever config matches your Organization needs)
   - Apply -> Ok

</p>
<br />

<h2>Complete installation by registering email and mySQL database.</h2>


<p>
  
1. Continue setting up osTicket in the browser (click Continue).
2. Name Helpdesk.
3. Default email (receives email from customers).
4. link Data base:
   - MySQL Database: osTicket.
   - MySQL Username: root.
   - MySQL Password: (**********).
5. Click “Install Now!”.

<p>
<img width="449" height="339" alt="Screenshot 2025-09-01 230025" src="https://github.com/user-attachments/assets/9842d889-4c71-4048-bbb1-cad88fc310bd" />
<img width="1568" height="586" alt="image" src="https://github.com/user-attachments/assets/778448cb-2708-48f0-ab5d-10321467f82a" />
</p>
</p>
<br />

<h2>Confirm osTicket can be reached by users on LocalHost</h2>


<p>

1. Test link for agents and end-users:
   - Admin/Agents URL: http://localhost/osTicket/scp/login.php
   - End Users URL: http://localhost/osTicket/
   
</p>
<p>
<img width="944" height="378" alt="image" src="https://github.com/user-attachments/assets/1b52cc9f-a80c-4344-996f-f3aadbfd78c6" />
<img width="831" height="339" alt="image" src="https://github.com/user-attachments/assets/c60ec757-fc83-4229-b4ca-6ffd93988a29" />

</p>
<br />

<h2>Clean up files that pose a security risk</h2>

<p>
  
1. Delete: C:\inetpub\wwwroot\osTicket\setup.
2. Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php.

</p>
<br />


