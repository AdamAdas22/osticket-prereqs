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
<img src="https://raw.githubusercontent.com/user/repository/branch/assets/96705782-1f70-4669-a823-401bfc8f1c5c.png" height="40%" width="40%" alt="osTicket Installation Step"/>
<p>
To install osTicket v1.15.8, start by navigating to the "osTicket-Installation-Files" folder on your system. Inside, you will find the "osTicket-v1.15.8.zip" file. Extract the contents of this zip file, which will create a folder named "upload." Next, copy the "upload" folder and move it to the C:\inetpub\wwwroot\ directory on your server. Once the folder is placed there, rename it from "upload" to "osTicket." This will ensure that the osTicket files are properly located and ready for web-based configuration.
</p>
























