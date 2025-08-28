<h1>osTicket - Prerequisites and Installation</h1>

<p align="center">

<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>

</p>


This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

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
