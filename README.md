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
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>

<p>
</p>
<p>
Welcome to my first tutorial! Today, we’ll walk through creating a Virtual Machine (VM) using the Microsoft Azure portal.

Our goal is to set up a VM, which acts as a remote computer, so that we can protect our physical machine in case anything goes wrong. Let’s get started:

First, create a resource group and name it osTicket.
Next, create a Virtual Machine with 2 to 4 CPUs. In this example, we’ll use 4 CPUs to ensure optimal performance.
Let’s dive in and get your VM up and running!







  
 <img src="https://i.imgur.com/OPaIGoN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
</p>
<p> Next, connect to your newly created VM using Remote Desktop Protocol (RDP) and the public IPv4 address provided.

Windows Users: You can use the built-in Remote Desktop Connection tool.
Mac Users: You’ll need to download the Microsoft Remote Desktop app to connect.
Once connected, you’ll have full access to the VM environment.







</p>
<img src="https://i.imgur.com/uLVKzxS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
</p>
<p>
Now that you’re connected to your VM, it’s time to enable Internet Information Services (IIS).

Go to the Control Panel and select Uninstall a program.
On the left side, click Turn Windows features on or off.
A list of features will appear—find and enable Internet Information Services (IIS).
Once enabled, IIS will be set up to serve web content on your VM.







</p>  
<img src="https://i.imgur.com/qtEnuWu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
</p>
<p>
Great! Now that IIS is enabled, the next step is to install the **Web Platform Installer**.

1. Use this link to access the necessary resources: [Web Platform Installer and osTicket materials](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6).
2. From the provided folder, download and install the **Web Platform Installer**.

This tool will help you easily install the required components for getting osTicket up and running.
</p>
<img src="https://i.imgur.com/AxHCfQ6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
After installing the **Web Platform Installer**, open the application to install the necessary components:

1. **Install MySQL 5.5** from within the Web Platform Installer.
2. Next, install the **x86 versions of PHP**, progressing up to version **7.3**.

There are a few files that may not install automatically, such as the **C++ Redistributable Package**, **PHP 7.3.8**, and **PHP Manager for IIS**. These files are available in the installation link provided earlier. Download and install these manually if needed. 

With these components in place, your VM will be ready for osTicket.
</p>
<img src="https://i.imgur.com/JJ8bZeJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
Next, download **osTicket** from the provided resources or the official website.

1. **Extract** the downloaded osTicket files.
2. Locate the **"upload"** folder within the extracted files, then **copy** it into the directory: `C:\inetpub\wwwroot`.
3. After copying, **rename** the "upload" folder to **osTicket**.

This setup will allow IIS to serve osTicket files, bringing us closer to launching the application.
</P>
<img src="https://i.imgur.com/TUGiSKi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
</p>
<p>
Now, let’s open **IIS Manager** and restart the server to finalize the setup:

1. Open **IIS Manager**.
2. Restart the server to apply any changes.
3. In IIS Manager, navigate to **Sites** > **Default** > **osTicket**.
4. On the right side, click **Browse \*.80**.

This should open your default web browser, displaying the osTicket web server interface. From here, you’re ready to begin the osTicket setup process!
</p>
<img src="https://i.imgur.com/4AkTkV0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
To enable the necessary PHP extensions in **IIS Manager**, follow these steps:

1. In **IIS Manager**, go to **Sites** > **Default** > **osTicket**.
2. Double-click on **PHP Manager**.
3. Select **Disable or enable an extension**.
4. Enable the following extensions:
   - **php_intl.dll**
   - **php_opcache.dll**

After enabling these, refresh the osTicket web server page in your browser. You should now see that the **Intl Extension** is enabled, confirming the configuration change.
</p>
<img src="https://i.imgur.com/APZgUTT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Next, let’s configure permissions for the osTicket configuration file:

1. Navigate to `C:\inetpub\wwwroot\osTicket\include\`.
2. Find the file named **ost-sampleconfig.php** and rename it to **ost-config.php**.

Now, set the required permissions:

1. Right-click **ost-config.php**, select **Properties**, then go to the **Security** tab.
2. Click **Advanced**, then choose **Disable inheritance** and **Remove all** inherited permissions.
3. Next, add new permissions:
   - Click **Add**, select **Everyone**, and set **Full control** permissions.

This will secure the config file while allowing osTicket to use it.
</p>
<img src="https://i.imgur.com/1nYaYGe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Once you’ve set the permissions, you can continue setting up osTicket in your browser:

1. Click **Continue** on the osTicket setup page.
2. You will be prompted to name your Helpdesk—choose a name that you like.
3. Next, select a **default email address**. This email will be used to receive notifications from customers who submit tickets.

Complete these steps, and you’ll be well on your way to having osTicket fully operational!
</p>
<img src="https://i.imgur.com/RmVk3q5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
<p> Continue setting up osTicket in your browser by entering the following details:

1. **MySQL Database**: `osTicket`
2. **MySQL Username**: `root`
3. **MySQL Password**: `Password1`

Once you've entered this information, click **Install Now!** 

If all goes well, you should see a confirmation of a successful installation with no errors. Congratulations!

### Clean Up

To finalize the setup:

1. Delete the **setup** folder to improve security:
   - Path: `C:\inetpub\wwwroot\osTicket\setup`
   
2. Set permissions for the **ost-config.php** file to "Read" only:
   - Path: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`

### Access the Admin Panel

Now you can log in to the osTicket Admin Panel at:
- [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)

You're all set to start managing your helpdesk!
