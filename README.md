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

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/9x0e06b.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First we are going want to RDP into our VM (if you are going to use one). Just find the public IP of the VM and connect with RDP.
</p>
<br />

<p>
<img src="https://i.imgur.com/AHEJz0J.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We are going to open up the web browser and paste the following link.
https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
</p>
<br />

<p>
<img src="https://i.imgur.com/juwJOuV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to the Programs section in Control Panel and click on "Turn Windows features on or off".
</p>
<br />

<p>
<img src="https://i.imgur.com/knnxxEZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install / Enable IIS in Windows WITH CGI

Just make sure every box that is shown in the image above is checked, you can hit the little "+" to expand menus out.

Hit OK and wait for everything to install and apply changes.
</p>
<br />

<p>
<img src="https://i.imgur.com/oocDORu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now in a new browser tab, type 127.0.0.1 (this is your loopback IP, if you don't know what that is google it). You then should see the IIS page popup, if you don't, go back and make sure you actually installed IIS with CGI.
</p>
<br />

<p>
<img src="https://i.imgur.com/LEs0xkr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now from the drive folder install PHPManagerForIIS_V1.5.0.msi and rewrite_amd64_en-US.msi
</p>
<br />

<p>
<img src="https://i.imgur.com/PTUWGf7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a new directory called C:\PHP
</p>
<br />

<p>
<img src="https://i.imgur.com/7d7kXY3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now install php-7.3.8-nts-Win32-VC15-x86.zip, move and extract all the contents into C:\PHP
</p>
<br />

<p>
<img src="https://i.imgur.com/a92AxFB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download and install VC_redist.x86.exe.

Download and install mysql-5.5.62-win32.msi
- Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
- Next ->
- Password1 (root will be the username, but you don't need to set that up) ->
- Execute 

</p>
<br />

<p>
<img src="https://i.imgur.com/CxMrZ4k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open IIS as administrator as shown above.
</p>
<br />

<p>
<img src="https://i.imgur.com/SGqmxvj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After opening IIS Manager as admin, click on the "PHP Manager" icon", hit "Register new PHP version". 

Browse files and find the PHP folder we made earlier and select "php-cgi" and hit open.
</p>
<br />

<p>
<img src="https://i.imgur.com/J4X5fP8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now open windows to the downloads folder and click on osTicket-v1.15.8, and on the other window open up your C:/ drive.
In that C:/ window, navigate to "inetpup" -> "wwwroot" and move in the "upload" folder from the osTicket zip and let it finish copying. Then rename the "upload" folder to "osTicket".
</p>
<br />

<p>
<img src="https://i.imgur.com/Myb9NCi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Close and reopen IIS manager as admin again, on the left expand the menus osTicket-VM -> Sites -> Default Web Site -> then click on osTicket.

On the right hit Browse *:80 and you should see the osTicket installer open inside of your default browser.
</p>
<br />

<p>
<img src="https://i.imgur.com/PJ7Wtpg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to IIS Manager, osTicket-VM -> Sites -> Default Web Site -> click osTicket -> click PHP Manager, then click on "Enable or disable an extension".
</p>
<br />

<p>
<img src="https://i.imgur.com/ebn67j3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Locate "php_imap.dll", "php_intl.dll", and "php_opcache.dll". Enable them all by right-clicking.
</p>
<br />


<p>
<img src="https://i.imgur.com/t2RSfAu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In file explorer go to C: -> inetpub-> wwwroot -> osTicket -> include, then locate ost-sampleconfig.php at the bottom.
Then rename the file form "ost-sampleconfig.php" to "ost-config.php"
</p>
<br />

<p>
<img src="https://i.imgur.com/T5L15v5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Then right click on that file got to Properties -> Security -> Advanced -> Disable inheritance -> Remove all
</p>
<br />

<p>
<img src="https://i.imgur.com/Ql9mhhS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Then click Add -> Select a principal -> In the object box type "Everyone" and check for names -> click OK
</p>
<br />

<p>
<img src="https://imgur.com/a/XQ3qTu3" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select Full control and hit OK -> click Apply -> OK -> OK
</p>
<br />

<p>
<img src="https://i.imgur.com/Zmue47F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now go back into the osTicket installer in the browser and click continue.
</p>
<br />

<p>
<img src="https://i.imgur.com/wetQO7Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
For the name I just did "Helpdesk" and for the email I did "john@helpdesk.com", then I set the Admin User credentials, write these down if you made up your own. 

Now just leave this page be and go onto the next step in this tutorial.
</p>
<br />

<p>
<img src="https://i.imgur.com/SzqiZ4Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download HeidiSQL form the Drive folder, it will download as a word doc and open it, then click the link to download the HeidiSQL Setup. 

Then install it.

Once it opens, click the green new button in the bottom left of the window, the username should be "root" and the password should be "Password1" if you set them to those earlier in this tutorial, then hit open.
</p>
<br />

<p>
<img src="https://i.imgur.com/wWBdupT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In HeidiSQL, right click Unnamed -> Create new -> Database, name it "osTicket" and click OK
</p>
<br />

<p>
<img src="https://i.imgur.com/PcWMFxf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Going back into the osTicket installer in the browser, put in the username and password for MySQL (should be "root" and "Password1" if you set them to those) and click install.
</p>
<br />

<p>
<img src="https://i.imgur.com/d2vjriv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We are almost ready to go on to the next tutorial, but first we need to clean some things up.

First browse to the C: drive -> inetpub -> wwwroot -> osTicket -> and delete the "setup" folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/hDbHCP0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now browse to C: -> inetpub -> wwwroot -> osTicket -> include -> and locate ost-config.php

Then on ost-config.php go to Properties -> Security -> Advanced -> click Everyone -> Edit -> and set the permissions to Read and Read & Execute only -> Apply.

Click OK.
