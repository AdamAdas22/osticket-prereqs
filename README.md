<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
osTicket is an open-source help desk ticketing system that allows organizations to manage customer inquiries efficiently. In this guide, we will walk through the installation process step by step, setting up osTicket on a Windows environment using IIS, MySQL, and PHP. This is a general overview of the process.

By the end of this tutorial, you will have a fully functional osTicket system ready for use. Let's get started!.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Prerequisites:</h2>

- osTicket-Installation-Files (for demonstration)
- Microsoft Azure Virtual Machine







  
<h2>Installation Steps</h2>
<h3>Step 1: Downloading installation files and enabling IIS wtih CGI</h3>
<img src="https://github.com/user-attachments/assets/e4b421ae-46ab-4e74-9dbe-026582a92ad4" height="40%" width="40%" alt="osTicket Installation Step"/>
<p>
Launch your Azure virtual machine, and from within the virtual machine download and extract all the installation files that include the dependencies. To enable IIS, go to the start menu --> control panel --> programs --> then, on the left click 'Turn Windows features on or off", and check and expand Internet Information Services. We also want to install CGI, a dependency that osTicket relies on. Expand the Application Development Features tab and click the CGI box. Click OK and wait a few minutes while Windows makes the neccessary changes.
</p>
<br />




<h3>Step 2: Downloading PHP manager with other dependencies</h3>

![image](https://github.com/user-attachments/assets/89dbe504-0ecd-407b-a57f-7edcfe8e7851) ![image](https://github.com/user-attachments/assets/da548fc5-f2ff-40c4-8e29-d8a3ce9e6bf7)
<p> From the osTicket installation files download PHP manager, click yes to everything and install. Then do the same with Rewrite Module, and VC_redist files. Install mysql, and when installing click the "typical setup option launch the configuration wizard. Choose "standard Configuration", click next and click next again. This next part is very important, DO NOT MESS THIS UP! For the purpose of an installation guide, just type the word "root" as the username and password when prompted. Click next and execute the program and finish. The empty database is installed.</p>







<h3>Step 3: Opening IIS and an Admin and registering PHP from within IIS</h3>

<p> 
Type "iis" in the windows start menu, and open it as an administrator. We want to register PHP from within, this just means we are making the web server aware of the existance of PHP on the computer. Open the PHP manager, and click "register new PHP version", and simply browse to it, more specifcally the file named "php-cgi". Now we will reload IIS, underneath the manage server tab click STOP and then START. minimize the application and Nnow we will finally unzip and install the osTicket folder. 
</p>







<h3> Step 4: Installing osTicket</h3>

<p>
To install osTicket v1.15.8, start by navigating to the "osTicket-Installation-Files" folder on your system. Inside, you will find the "osTicket-v1.15.8.zip" file. Extract the contents of this zip file, which will create a folder named "upload." Next, copy the "upload" folder and move it to the C:\inetpub\wwwroot\ directory on your server. Once the folder is placed there, rename it from "upload" to "osTicket." This will ensure that the osTicket files are properly located and ready for web-based configuration.
</p>


<h3>Step 5: Reloading IIS and Accessing osTicket</h3>
<p>
To ensure that the osTicket installation is properly configured, open IIS Manager, go to the "Manage server" tab, click "Stop," and then click "Start" to reload the server. Afterward, navigate to "Sites" and locate the "Default" site. Under "Default," select the "osTicket" directory. On the right-hand side, click on the "Browse *:80" button to open your osTicket site in your default web browser, confirming that the installation is accessible. This should load the osTicket site.
</p>



<h3>Step 6: Enabling Required PHP Extensions</h3>
<p>
Some extensions may not be enabled by default. To enable the required extensions, go back to IIS Manager, navigate to "Sites" and select "Default" -> "osTicket." Double-click on "PHP Manager," then click on "Enable or disable an extension." From here, enable the following extensions: "php_imap.dll," "php_intl.dll," and "php_opcache.dll" by right clicking them and clicking enable. After enabling these extensions, refresh the osTicket site in your browser to observe the changes.
</p>


<h3>Step 7: Renaming ost-sampleconfig.php to ost-config.php</h3>
<p>
Navigate to the "C:\inetpub\wwwroot\osTicket\include\" directory and locate the file named "ost-sampleconfig.php." Rename this file to "ost-config.php." This is a important and potientially costly step to configure the osTicket system with the correct settings.
</p>


<h3>Step 8: Assigning Permissions to ost-config.php</h3>
<p>
To secure the configuration file, navigate to the "C:\inetpub\wwwroot\osTicket\include\" directory and locate "ost-config.php." Right-click on the file and select "Properties." Under the "Security" tab, click on "Advanced," then choose "Disable inheritance" and remove all existing permissions. After that, click on "Add" and assign new permissions by selecting "Everyone" and granting "All" permissions. This ensures the correct permissions for osTicket to function properly. Again, giving access to everyone in a real life situation is a terrible idea, but we are doing this to showcase the lab.
</p>


<h3>Step 9: Continue Setting Up osTicket in the Browser</h3>
<p>
After assigning the necessary permissions, continue with the setup in the browser. Click the "Continue" button to proceed. In the next steps, you'll be prompted to name your helpdesk and set up the default email. For the helpdesk name, an example would be "User's Helpdesk." For the default email, enter a placeholder email address that will receive emails from customers, such as "admin.helpdesk@example.com." Use a random placeholder name for the admin, for example, "John Doe" with the email "john.doe@example.com." This setup allows osTicket to process incoming emails for the helpdesk.
</p>

<h3>Step 10: Installing HeidiSQL and Creating a Database</h3>
<p>
From the “osTicket-Installation-Files” folder, begin by installing HeidiSQL. Once installed, open HeidiSQL and create a new session. Enter "root" as both the username and password. Click "Connect" to establish a connection to the session. After connecting, create a new database called "osTicket" by typing "CREATE DATABASE osTicket;" in the query window and executing it. This database will be used to store the data for your osTicket installation. In the osTicket installer, type the neccesary information in the Database settings, such as the database username osTicket and the username and password to that database.
</p>

<h3>Step 11: Completing osTicket Setup in the Browser</h3>
<p>
Continue setting up osTicket in your browser. When prompted, enter the following details for the database setup:
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: root
Once these are filled out, click the “Install Now!” button to complete the installation process. This will finalize the osTicket setup and prepare it for use.
</p>


<h3>Step 12: Finalizing osTicket Installation and Cleanup</h3>
<p>
Congratulations, your osTicket system should now be installed without errors! To access the admin panel, browse to the help desk login page: http://localhost/osTicket/scp/login.php
For end users, the osTicket URL will be: "http://localhost/osTicket/
</p>

<p>
To clean up after the installation, navigate to the following directory and delete the "setup" folder: "C:\inetpub\wwwroot\osTicket\setup"
Next, set the permissions of the "ost-config.php" file to "Read" only by modifying the permissions at: "\inetpub\wwwroot\osTicket\include\ost-config.php"
</p>









