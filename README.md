<h1>osTicket - Prerequisites and Installation</h1>

<p align="center">

<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>

</p>


This tutorial outlines the prerequisites and in-depth installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)

- Remote Desktop

- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure subscription

- Access to Remote Desktop
  
- Microsoft Windows app installed (if using Mac)

- Access to osTicket files (provided below)

<h2>Installation Steps</h2>

<p>

<img width="60%" height="60%" alt="Screenshot 2025-08-21 at 1 32 05 PM" src="https://github.com/user-attachments/assets/c38f2e5f-63ad-4822-a40a-d1a3e6bc24f1" />

</p>

<p>
The first thing we need to do is set up a Virtual Machine inside of our Azure account. Here we can provision the operating system we would like to use for this demonstration, which we will be using Windows 10 (22H2) and give it access to 4 vcpus and 16 gigabytes of RAM.
</p>

<br />

<p>

<img width="60%" height="60%" alt="Screenshot 2025-08-21 at 1 39 36 PM" src="https://github.com/user-attachments/assets/b1ad77b3-98aa-498f-b7cb-24036944ff61" />

</p>

<p>

After successfully creating the VM (and if you're using a Mac), we must add the VM to Microsoft's Windows App. Copy the public IP address and enter it into the PC name input box. Feel free to name this whatever you prefer.

</p>


<p> <?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>URL</key>
	<string>https://drive.google.com/uc?export=download&amp;id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD</string>
</dict>
</plist>

Use this link here to download the osTicket installation files onto the VM.

<br>

<img width="60%" height="60%" alt="Screenshot 2025-08-21 at 1 51 28 PM" src="https://github.com/user-attachments/assets/301ad10f-d5e0-4bf5-adc1-981aad2dd8bd" />

<br />
<br />

Click download anyway.

<br />
</p>

<p>

<img width="60%" height="60%" alt="Screenshot 2025-08-21 at 2 02 19 PM" src="https://github.com/user-attachments/assets/4fd32b66-f9d1-42cc-a048-eb15f236c314" />

When downloaded, right click the file to then Extract all to the desktop.

Congratulations, you have just extracted the osTicket files onto your VM. Good work.

</p>
<br />

<p>
Next, in this step, we will enable IIS and install CGI.

<br />
<br />

  <img width="60%" height="60%" alt="Screenshot 2025-08-21 at 2 14 11 PM" src="https://github.com/user-attachments/assets/ba52735c-7a74-4128-9807-b84ae48a4586" />

<br>


We will start this by opening up the windows start menu, go into the control panel and click on Uninstall a program.

  <br />
 <br />
 <img width="266" height="441" alt="Screenshot 2025-08-21 at 2 37 49 PM" src="https://github.com/user-attachments/assets/2a0764a2-be6d-40fe-be0c-7a0cffff5935" />


<br />
  <br />
  
  Click Turn Windows features on or off. 
  
</p>

<p>

  <img width="416" height="369" alt="Screenshot 2025-08-21 at 2 15 35 PM" src="https://github.com/user-attachments/assets/23dfe245-0404-4e54-839f-eb27dfe8d88f" />

  <br>
  <br> 
  Select Internet Information Services.
  <br>
  <br>
<img width="626" height="558" alt="Screenshot 2025-08-21 at 2 43 55 PM" src="https://github.com/user-attachments/assets/59277de4-036b-408b-b587-7a2626417032" />
   <br>
   <br>
   Expand Internet Information Services, go into the World Wide Web Services folder, then into the Application Development Features, and finally click on the CGI box and hit OK. This will download CGI onto the VM. (CGI is a dependency that osTicket needs as part of the web server) This turns the VM into a web server.

</p>

<p>
  Now you have successfully downloaded CGI and enabled IIS. Great work.
</p>

<p>
  Next, we will install the PHP manager for IIS. PHP is a back-end web server language. OsTicket runs off this language. The PHP manager allows you to register, configure and manage multiple PHP installations.
</p>

<p>
  <img width="615" height="321" alt="Screenshot 2025-08-21 at 3 18 27 PM" src="https://github.com/user-attachments/assets/53c83215-d2a8-4a1d-9ff9-9b89cbe05579" />
</p>
<br>
<p>
  Open up the osTicket installation folder that was extracted earlier. Inside this folder, run PHPManagerForIIS_v1.5.0. Follow the onscreen instructions to install.
</p>
<p>
<img width="620" height="624" alt="Screenshot 2025-08-21 at 3 31 11 PM" src="https://github.com/user-attachments/assets/26f66c76-09ef-434c-a721-420b0207b66c" />
</p>
<p>
  Inside the osTicket installation folder, run rewrite_amd64_en-US and follow the onscreen instructions to install. The rewrite module allows for clean URLs and routing inside osTicket. 
</p>
<p>
  After installing rewrite_amd64_en-US, we need to add the directory to this PC's C: drive. We will name the folder PHP.
</p>
<p>
<img width="722" height="415" alt="Screenshot 2025-08-21 at 3 36 58 PM" src="https://github.com/user-attachments/assets/67ce5749-8eab-45e1-b21e-7fe56d065ef9" />
</p>
<p>
  To do this, Open file explorer --> This PC --> Windows (C:) and add a new folder named PHP. We will extract the php-7.3.8-nts-Win32-VC15-x86 file into our new directory.
</p>
<p>
  <img width="616" height="724" alt="Screenshot 2025-08-21 at 3 46 30 PM" src="https://github.com/user-attachments/assets/4c87aff2-1174-48de-b488-7343923079e7" />
</p>
<p>
  Right click the zipped file php-7.3.8-nts-Win32-VC15-x86 and select Extract All. Look for This PC --> Windows (C:) --> PHP. Select the PHP folder and extract.
</p>
<p>
  Now, install VC_redist.x86.
</p>
<p>
  <img width="613" height="630" alt="Screenshot 2025-08-21 at 3 52 44 PM" src="https://github.com/user-attachments/assets/413ab96e-c48d-40c5-a105-9ce43eee5f88" />
</p>
<p>
  Inside the osTicket install folder, run VC_redist.x86. This is required to allow PHP to run properly on windows.
</p>
<p>
  Let's install mysql-5.5.62-win32.
</p>
<p>
  <img width="617" height="613" alt="Screenshot 2025-08-21 at 4 02 55 PM" src="https://github.com/user-attachments/assets/bba2402a-9c06-430e-a28f-ace29ba8fe81" />
</p>
<p>
  Inside the osTicket install folder, run mysql-5.5.62-win32. This is a database osTicket will use to store of the data, like ticket information and user accounts.
</p>
<p>
  <img width="497" height="390" alt="Screenshot 2025-08-21 at 4 06 54 PM" src="https://github.com/user-attachments/assets/511f56bb-9e5f-4e05-bbe2-10aa1f61f2bd" />
</p>
<p>
  When prompted, select Typical setup, then install. This will launch the MySQL Server Instance Configurator.
</p>
<p>
  <img width="499" height="381" alt="Screenshot 2025-08-28 at 10 26 35 AM" src="https://github.com/user-attachments/assets/06a6928b-26aa-4227-a94c-fdfeaee11c54" />

</p>
<p>
  Click next.
</p>
<p>
  <img width="502" height="383" alt="Screenshot 2025-08-28 at 10 46 32 AM" src="https://github.com/user-attachments/assets/843ed9c3-4f61-48bb-89c4-85979c96084d" />

</p>
<p>
  Select standard configuration. 
</p>
<p>
  <img width="500" height="380" alt="Screenshot 2025-08-28 at 10 46 47 AM" src="https://github.com/user-attachments/assets/c6762262-7407-4348-b29a-dcb74d69c1c3" />

</p>
<p>
  Ensure Install As Windows Service is selected, select next.
</p>
<p>
  <img width="499" height="381" alt="Screenshot 2025-08-21 at 4 10 28 PM" src="https://github.com/user-attachments/assets/a22ad1f2-342c-4e62-93c3-bf94cda947d7" />

</p>
<p>
  Create your own root password, then select next. Then, exexcute the configurator and finish.
</p>
<p>
 <img width="498" height="378" alt="Screenshot 2025-08-28 at 1 15 22 PM" src="https://github.com/user-attachments/assets/66b7c134-a97d-44a9-97b6-6790d2c06d99" />

</p>
<p>
  Well done. Next, we will open IIS as an admin. 
</p>
<p>
	<img width="765" height="318" alt="Screenshot 2025-09-01 at 1 21 32 PM" src="https://github.com/user-attachments/assets/880c976e-0d5d-443d-ac3d-491c6bb204a7" />

</p>
<p>
	In the search bar, type in IIS. Then click on Run as administrator. Now with IIS open and running as an admin, we must register the PHP we made earlier.
</p>
<p><img width="1000" height="573" alt="Screenshot 2025-09-01 at 1 26 03 PM" src="https://github.com/user-attachments/assets/0b35d2b4-6f37-49b4-ac5c-f9db31922744" />
	
</p>
<p>
	Open up the PHP Manager.
</p>
<p>
	<img width="500" height="226" alt="Screenshot 2025-09-01 at 1 26 21 PM" src="https://github.com/user-attachments/assets/bb0913bc-78af-4c7e-ae3b-5102ab517c0a" />

</p>
<p>
 Click Register new PHP version.
</p>
<p><img width="640" height="451" alt="Screenshot 2025-09-01 at 1 27 25 PM" src="https://github.com/user-attachments/assets/0037d7bf-878a-45ac-b4dc-27da0d8b57e4" />
	
</p>
<p>
	We will now search for the PHP file. Go into the Windows (C:) drive.
</p>
<p><img width="610" height="465" alt="Screenshot 2025-09-01 at 1 27 34 PM" src="https://github.com/user-attachments/assets/c06cb909-6b99-4035-8caf-c54f51f4663d" />
	
</p>
<p>
	Click the PHP folder we created.
</p>
<p>
	<img width="609" height="470" alt="Screenshot 2025-09-01 at 1 27 43 PM" src="https://github.com/user-attachments/assets/0377c1b4-e695-42fc-9161-7dd83149271c" />
	
</p>
<p>
	Double click php-cgi file.
</p>
<p>
	<img width="513" height="219" alt="Screenshot 2025-09-01 at 1 28 01 PM" src="https://github.com/user-attachments/assets/372964c8-25aa-4638-ae97-1f0ae604c8a1" />

</p>
<p>
	Ensure the correct file is selected, and select OK. 
</p>
<p>
	Now we must reload IIS. We can do this by stopping and starting the server.
</p>
<p>
	<img width="1023" height="556" alt="Screenshot 2025-09-01 at 1 49 06 PM" src="https://github.com/user-attachments/assets/b5f0b4fb-1cd5-4a2e-a619-e257a093b7dc" />
	
</p>
<p>
	You can stop and start the server with the Manage server options on the right side of IIS.
</p>
<p>
	<img width="297" height="344" alt="Screenshot 2025-09-01 at 1 32 01 PM" src="https://github.com/user-attachments/assets/390ea9d0-ed7f-409a-900e-92425b345975" />
	
</p>
<p>
	We can also stop the server by right-clicking the osticket-vm file on the left side of IIS.
</p>
<p>
	<img width="337" height="328" alt="Screenshot 2025-09-01 at 1 32 25 PM" src="https://github.com/user-attachments/assets/3143ec07-5c2a-4516-a896-de7096d30875" />

</p>
<p>
	Right-click it again to start the server back up.
</p>
<p>
	Good work so far. Now let us intall "osTicket V1 15.8". Minimize IIS for now and navigate back to the osTicket installation files folder.
</p>
<p>
	<img width="786" height="592" alt="Screenshot 2025-09-01 at 2 06 44 PM" src="https://github.com/user-attachments/assets/66d969c1-580b-4d05-8b31-1b6ac3f00133" />

</p>
<p>
	Right-click osTicket-v1.15.8 and select extract all to the desktop.
</p>
<p>
	With that extracted, we will copy the upload folder into the inetpup folder inside the C: drive.
</p>
<p>
	<img width="784" height="381" alt="Screenshot 2025-09-01 at 2 11 21 PM" src="https://github.com/user-attachments/assets/95e45b3c-adc5-4103-98dc-1700d142f98a" />

</p>
<p>
	Open up file explorer, go inside of This PC, open Windows (C:) and open inetpub.
</p>
<p>
	<img width="788" height="305" alt="Screenshot 2025-09-01 at 2 11 33 PM" src="https://github.com/user-attachments/assets/744d3307-4915-4c80-b498-0c86122d9bb2" />

</p>
<p>
	Copy the upload folder into wwwroot.
</p>
<p>
	<img width="724" height="240" alt="Screenshot 2025-09-01 at 2 17 24 PM" src="https://github.com/user-attachments/assets/4abef0db-7144-4d98-baa7-48d287d2c044" />

</p>
<p>
	After copying the folder, rename it to "osTicket".
</p>
<p>
	<img width="1021" height="315" alt="Screenshot 2025-09-01 at 2 20 11 PM" src="https://github.com/user-attachments/assets/e1af598c-b2b0-41a7-a777-38c49cc124a2" />

</p>
<p>
	Please reload IIS again at this time. Go back inside IIS and select stop, and then start again. Next, let's try to load our newly installed osTicket site from IIS.
</p>
<p>
	<img width="1021" height="349" alt="Screenshot 2025-09-01 at 2 26 08 PM" src="https://github.com/user-attachments/assets/fbc96cc0-e29a-4a99-a104-37127c45fb49" />

</p>
<p>
	Within IIS, on the left-hand side of the screen, expand the osticket connection, then Sites, then Default Web Site and click on osTicket. On the right-hand side, inside Manage Folder, there should be an option named "Browse*:80 (http). Click that.
</p>
<p>
	<img width="895" height="766" alt="Screenshot 2025-09-01 at 2 29 46 PM" src="https://github.com/user-attachments/assets/58551061-ace7-49c7-983f-de0244275021" />

</p>
<p>
	osTicket Installer should open up if everything was installed correctly. Excellent job! 
</p>
<p>
	Note that there are a couple of extensions that we still need to enable for the best experience possible. Let's dive into that. Please open up IIS again (as admin if not still open).
</p>
<p>
	<img width="813" height="433" alt="Screenshot 2025-09-01 at 2 35 11 PM" src="https://github.com/user-attachments/assets/11c80f65-e249-4603-a3e9-3c322bc9ce39" />

</p>
<p>
	Inside IIS on the left side, expand osticket, Sites, Default Web Site and select the osTicket folder. Double click PHP Manager.
</p>
<p>
	<img width="732" height="562" alt="Screenshot 2025-09-01 at 2 37 39 PM" src="https://github.com/user-attachments/assets/14ee6533-02c9-4c08-9516-0d4f9d0d6687" />

</p>
<p>
	Select Enable or disable an extension. Inside the disabled extensions section, you must find and enable 'php_imap.dll', 'php_intl.dll', and 'php_opcache.dll'.
</p>
<p>
	<img width="366" height="308" alt="Screenshot 2025-09-01 at 2 44 40 PM" src="https://github.com/user-attachments/assets/eac92e66-d35e-4698-ae8b-41e1c48d6b8c" /> <br>
<img width="334" height="333" alt="Screenshot 2025-09-01 at 2 43 30 PM" src="https://github.com/user-attachments/assets/6eefeb97-beb1-4bb7-b723-f9999f7b9ab9" /> <br>
<img width="351" height="356" alt="Screenshot 2025-09-01 at 2 43 57 PM" src="https://github.com/user-attachments/assets/9c1c9f4f-f197-4c5d-bb56-2b6a5b8661ee" /> <br>


</p>
<p>
	With those extensions enabled, navigate back to the osTicket Installer page on the web browser. Refresh this page to observe these changes.
</p>
<p>
	<img width="602" height="665" alt="Screenshot 2025-09-01 at 2 50 15 PM" src="https://github.com/user-attachments/assets/ee2e22c0-0ec1-474e-96cb-907ce70ad47e" />

</p>
<p>
	Now we need to rename one of the files we installed.
</p>
<p>
	<img width="787" height="416" alt="Screenshot 2025-09-01 at 2 58 54 PM" src="https://github.com/user-attachments/assets/b7e9a609-b958-4c69-b04b-3db08aacc49b" />

</p>
<p>
	Go back into file explorer -> This PC -> Windows (C:) -> inetpub -> wwwroot -> osTicket -> include -> and scroll until you find the file ost-sampleconfig.php. Right-click and select rename.
</p>
<p>
<img width="782" height="290" alt="Screenshot 2025-09-01 at 3 02 56 PM" src="https://github.com/user-attachments/assets/c68b8395-0bdd-49af-a145-31e60b88eabd" />

</p>
<p>
	Rename this file to 'ost-config.php'. Please ensure this is spelled exactly the same as it is here.
</p>
<p>
<img width="517" height="342" alt="Screenshot 2025-09-01 at 3 04 41 PM" src="https://github.com/user-attachments/assets/2df8ff73-3930-459a-a2b1-30f635a27334" />
</p>
<p>
	We must assign permissions for osTicket to be able to make changes to this file on the back-end. To do this, right click our newly named file and select properties.
</p>
<p>
	<img width="363" height="508" alt="Screenshot 2025-09-01 at 3 08 24 PM" src="https://github.com/user-attachments/assets/2c9de9bd-f5ed-4ee1-a8fa-35b03e591576" />

</p>
<p>
	Once inside, go to the security tab at the top, then click the Advanced settings button. 
</p>
<p>
	<img width="764" height="518" alt="Screenshot 2025-09-01 at 3 09 59 PM" src="https://github.com/user-attachments/assets/1a8fa2c4-5407-41ff-b0f3-d7523ad690f5" />

</p>
<p>
	We must first Disable inheritance, and Remove all inherited permissions from this object.
</p>
<p>
	<img width="528" height="330" alt="Screenshot 2025-09-01 at 7 01 40 PM" src="https://github.com/user-attachments/assets/522c979a-a1bf-4438-95e2-7f7052bf2fc7" />

</p>
<p>
	Click Select a principal.
</p>
<p>
	<img width="502" height="310" alt="Screenshot 2025-09-01 at 7 05 16 PM" src="https://github.com/user-attachments/assets/c0a92f02-2ef1-411f-90a9-115339b4d04a" />

</p>
<p>
I am using Everyone as the object to test the install. Please do not do this on an enterprise level.
</p>
<p>
<img width="765" height="520" alt="Screenshot 2025-09-01 at 7 09 33 PM" src="https://github.com/user-attachments/assets/de3b1dc3-85c1-4ee5-bcc5-9dce8f8effa4" />

</p>
<p>
	After applying the permissions you would like to enable, click Apply and then OK.
</p>
<p>
	Now head back to osTicket Installer on your web browser.
</p>
<p>
	<img width="841" height="1034" alt="Screenshot 2025-09-01 at 7 14 23 PM" src="https://github.com/user-attachments/assets/762a658a-614d-42e3-9edf-ac0ae743ebec" />

</p>
<p>
	Go ahead and fill out the information to have your osTicket setup.
</p>
<p>
	After getting the personal information filled out, we must now install HeidiSQL. This is an application that allows us to make a connection to our database and gives us a friendly way to interact with the MySQL database. Navigate your way back into the osTicket-Installaiton-Files folder.
</p>
<p>
	<img width="784" height="415" alt="Screenshot 2025-09-01 at 7 22 16 PM" src="https://github.com/user-attachments/assets/c1902b94-2039-41d7-b0b7-07d273d36c18" />

</p>
<p>
	Inside the osTicket-Installation-Files folder, click on HeidiSQL_12.3.0.6589_Setup and follow the onscreen instructions. Click accept terms and all of the other settings can be left as they are.
</p>
<p>
	<img width="686" height="480" alt="Screenshot 2025-09-01 at 7 25 29 PM" src="https://github.com/user-attachments/assets/472d419a-8b93-45f5-9b41-2d1be28a433e" />
	
<p>
	When HeidiSQL is finished installing, the Session Manager should show up. Select New in the bottom-left corner.
</p>
<p>
	<img width="684" height="483" alt="Screenshot 2025-09-01 at 7 29 36 PM" src="https://github.com/user-attachments/assets/00180e4b-8435-417a-8061-2c69ae791a5f" />
	
</p>
<p>
	Enter the root password we made earlier in the password box.
</p>
<p>
	<img width="933" height="591" alt="Screenshot 2025-09-01 at 7 31 19 PM" src="https://github.com/user-attachments/assets/f565804b-dc2c-4658-bbf8-3ace32ddfc8f" />

</p>
<p>
	We have just opened a connection to our database. Now we will create a new database.
</p>
<p>
	<img width="548" height="306" alt="Screenshot 2025-09-01 at 7 35 41 PM" src="https://github.com/user-attachments/assets/5a90bca6-5484-4c08-9852-69f91cb42829" />
	
</p>
<p>
	Underneath the Database filter on the left-hand side of the screen, right-click on Unnamed, scroll to create new and scroll to Database.
</p>
<p>
	<img width="317" height="259" alt="Screenshot 2025-09-01 at 7 36 20 PM" src="https://github.com/user-attachments/assets/42dff8bb-de7a-42d6-a7fa-bb7af5a1fbea" />

</p>
<p>
	Name the Database osTicket. Click OK. After this, it is now time to return to osTicket installer on our web browser.
</p>
<p>
	<img width="831" height="370" alt="Screenshot 2025-09-01 at 7 41 26 PM" src="https://github.com/user-attachments/assets/89ff5304-a145-4d16-9a3d-93870870b540" />

</p>
<p>
	The name for the MySQL database will be osTicket. Enter your user name and your password now. When you are finished, go ahead and click install.
</p>
<p>
	<img width="842" height="645" alt="Screenshot 2025-09-01 at 7 52 53 PM" src="https://github.com/user-attachments/assets/f29f66ee-d420-4087-8e93-51299e0b550c" />

</p>
<p>
	osTicket should now be installed. To verify that this has worked, head on over to <a href ="http://localhost/osTicket/scp/login.php">osTicket Login</a> and enter your username and password name. </p>
<p>
<img width="1185" height="669" alt="Screenshot 2025-09-01 at 8 16 03 PM" src="https://github.com/user-attachments/assets/b658b773-b8fd-4704-a479-6b4d758c9269" />

</p>
<p>
	Congratulations, you have successfully installed osTicket on your VM. Great work!
</p>
