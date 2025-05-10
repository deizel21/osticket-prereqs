# osticket-prereqs
Here is an osticket installation guide
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

- Creating an Azure Virtual Machine for osTicket and Enabling IIS(Information Internet Services)
- Installing the web platform installer
- Installing MYSQL and setting up username/passowrd
- Installing the C++ redistributable
- Configuring Permissions and finishing osTicket installation

<h2>Installation Steps</h2>

<p>
•Create an Azure Virtual Machine Windows 10, 4 vCPUs
	Name: osticket-vm
	Username: labuser
	Password: osTicketPassword1!(or whatever password you want to use)

•Create your VM by nameing the Resource Group : osTicket > then Virtual Machine name : osticket-vm > Region : US East 2 or another region depending on your location > then Zone options should be on : Azure Selected Zone > Image: Windows 10, 22H2 -x64 Gen2 > Administrator Account | username: labuser1  password: whatever password you want that meets the requirement
Next click disk >  Click next on networking >  Click the “Review and Create” Button

  ![image](https://github.com/user-attachments/assets/b845701b-3bf8-4632-8331-82f6158e3696) 

![image](https://github.com/user-attachments/assets/ed3b4207-6579-477f-89f0-af2aa8b6e4e4)

•	Once the Resource Group is created, click “Go to Resource” > Then once in the Virtual machine Overview, to the far right copy your Public IP address> Then log into the VM with Remote Desktop
•	You can click the “RDP download file” button to connect. 
•	When you log into the VM, select no for every option on the blue privacy screen> Then copy and paste this link into the Microsoft Edge Browser : https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD
•	You will then need to download this zip file > Once downloaded, right click on the zip file in the folder and press “Extract All”

![image](https://github.com/user-attachments/assets/bdd1f060-6684-43e7-83e3-37bb12321943)
![image](https://github.com/user-attachments/assets/eb4a23b6-e641-4c9c-a223-61b5b1ba8066)
![image](https://github.com/user-attachments/assets/da7723b9-b8c1-42fe-aca6-60f32adb8951)
![image](https://github.com/user-attachments/assets/22cb61b6-a4ec-46e4-8a8c-0a1df59c9e50)

•Then we will Install / Enable IIS in Windows WITH CGI

•Go to the start menu > Then Control Panel > Programs > Uninstall a program > Turn windows features On or Off > Scroll down and Select  Internet Information Services > Hit the plus sign on the IIS you selected to expand > Hit plus sign by World Wide Web Services > Plus sign by Application Development Features > Select [X] CGI and press OK
	
•Type in 127.0.0.1 and press Enter. You should see a Internet Information Services Page

![image](https://github.com/user-attachments/assets/200fdf73-acdf-4be9-853e-5836b7d9300b)
![image](https://github.com/user-attachments/assets/eee521f5-50bc-4f6a-a929-f2514b3846b1)
![image](https://github.com/user-attachments/assets/6a712688-04b2-4faa-89ac-7754e7c92468)

</p>
<p>
•	From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) > Select Next > Select I agree button and click next > then Finish
•	Next select the  “osTicket-Installation-Files” folder  and install the Rewrite Module (rewrite_amd64_en-US.msi) Select I agree button and click Install > then Finish
•	Next right click the File folder on the taskbar and go to the C:\ drive > then right click on the blank space and choose the New Folder option > then type PHP to create the directory C:\PHP 

•	From the “osTicket-Installation-Files” folder, right click and select extract all to unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and extract it into the “C:\PHP” 

•	From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

•	From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi) > Make sure you select Typical setup and then install! > Then the configuration setup choose Standard Configuration > Then click Next > Then type root for both user and password next Modify Security Settings(VERY IMPORTANT!!!) > Next and press execute

![image](https://github.com/user-attachments/assets/10ba0b70-c503-4398-897b-e76188b70519)
![image](https://github.com/user-attachments/assets/cef13ce6-ddba-4422-82a5-7880535147fc)
![image](https://github.com/user-attachments/assets/42ff837a-13ad-4744-8169-ce8734679b55)
![image](https://github.com/user-attachments/assets/376b7f40-a3ca-42e9-8711-8ad888e7f987)
![image](https://github.com/user-attachments/assets/48064952-8545-4a2f-a840-dc5be6e7f9a7)
![image](https://github.com/user-attachments/assets/8a18ac86-f4e9-4e78-8e6a-17ca014ca04f)


</p>
<br />

<p>
•	Open IIS as an Admin/ Type IIS in the search bar and Right Click on IIS > The Run as Administrator 

•	Register PHP from within IIS (Double click PHP Manager> Click Register PHP new PHP version > Browse by clicking 3 little dots to the right ->double click C:\PHP\php-cgi.exe)

•	Reload IIS (Open IIS, Stop and Start the server)

![image](https://github.com/user-attachments/assets/b737dee7-511b-49dd-af28-58f2cdd30132)
![image](https://github.com/user-attachments/assets/8abff2c5-0cf8-45c0-9e1f-d706da1951c9)

•Install osTicket v1.15.8
 From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
 Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”(NO SPACES!)

•Reload IIS (Open IIS, Right click on the PHP Manger Icon on the left to Stop and Start the server)
Go to sites -> Default -> osTicket
	On the right, click “Browse *:80”

![image](https://github.com/user-attachments/assets/ce440541-e812-406d-ba06-bdea0f768f89)
![image](https://github.com/user-attachments/assets/28864337-8760-4469-9bc3-9ada8fd8b8a6)
![image](https://github.com/user-attachments/assets/d74390b6-a0b3-4814-86f7-fb58a31a7b5a)

•	Overall Steps

Note that some extensions are not enabled
•	Go back to IIS, sites -> Default -> osTicket
•	Double-click PHP Manager
•	Click “Enable or disable an extension”
•	Enable: php_imap.dll
•	Enable: php_intl.dll
•	Enable: php_opcache.dll
•	Refresh the osTicket site in your browser, observe the changes

•	Rename: ost-config.php >	From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php > To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
•Assign Permissions: ost-config.php
	Right click the ost-config.php file and go to properties> Advanced > Disable inheritance ->  Remove All Inherited Permissions > Add> Select a Principal > check names > press OK > Select Full Control > Select Apply > press Ok
•Click	New Permissions -> Everyone -> All

![image](https://github.com/user-attachments/assets/e83ed7f5-7bab-4035-aa2c-8f348e5a6ba2)
![image](https://github.com/user-attachments/assets/f8bf860a-1db6-4400-a6ed-225e75af33d1)
![image](https://github.com/user-attachments/assets/a3ff5f23-760f-4abd-a1a7-313b697e3c66)
![image](https://github.com/user-attachments/assets/784a5630-7f99-4440-a7a7-b2916d8535b3)

• Continue Setting up osTicket in the browser (click Continue)
	Name Helpdesk > Default email (receives email from customers)

•From the “osTicket-Installation-Files” folder, install HeidiSQL.
 Open Heidi SQL (Allows us to make a connection to our database and configure it.) Once installed Select/Create a new session, >Connect root/root
 Connect to the session
	Right click unnamed and select Database >Create a database called “osTicket”

•Continue Setting up osTicket in the browser
	MySQL Database: osTicket >MySQL Username: root > MySQL Password: root >	Click “Install Now!”

Congratulations, hopefully it is installed with no errors!
	Browse to your help desk login page: http://localhost/osTicket/scp/login.php

• End Users osTicket URL: >	http://localhost/osTicket/ 

•Clean up >	Delete: C:\inetpub\wwwroot\osTicket\setup >	Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

![image](https://github.com/user-attachments/assets/ae377b1e-dde3-42ce-8d0d-a5a192b09dea)
![image](https://github.com/user-attachments/assets/c3af6a3d-488e-4033-b9c3-2d7e26d00a5c)
![image](https://github.com/user-attachments/assets/a4f44be3-4c8f-43f8-b429-642d3722dc02)
![image](https://github.com/user-attachments/assets/8b8ff2df-b769-4b16-b5f2-3aad972547ae)
![image](https://github.com/user-attachments/assets/57cdfcf8-9e30-476f-bc22-1a748e226cb1)

![image](https://github.com/user-attachments/assets/e838a239-671b-4c82-a30a-9c5b7bfa3d87)

You should now have successfully installed osTicket!
</p>
<br />
