<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Prerequisites and Installation

In this lab, we set up the osTicket helpdesk ticketing system by completing the prerequisites and installation process. Using tools such as Microsoft Azure, IIS, and Remote Desktop, we prepare a virtual environment, configure essential components like the web server and database, and guide you through a step-by-step installation of osTicket, ensuring all dependencies are properly addressed for a functional setup.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop (macOS)
- Internet Information Services (IIS)

## Operating Systems Used

- Windows 10</b> (21H2)

## List of Prerequisites

- Create a Resource Group
- Create a Virtual Machine inside the Resource Group
- Connect Virtual Machine with Remote Desktop
- Download & Install osTicket
  - [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
  - Install/Enable IIS in Windows
  - Enable Extensions for osTicket
  - Rename: **ost-sampleconfig.php**
  - Assign Permissions To: **ost-config.php**
  - Create a database for osTicket
- Clean Up Resources
- Change: **ost-config.php** File Permissions

## Configuration Steps

<details>

<summary>

## ⚙️ Part A: Create a Resource Group

</summary>

### 1. ) Create a Resurce Group

Create a resource group named "RG-osTicket" in the "(US) West 3" region, then select **Review + Create** and click **Create**.

*Double-check spelling when creating resources, virtual machines, regions, and similar inputs. Errors may require deletion and re-creation. For help with creating Virtual Machines and Resource Groups, refer to [my other lab](https://github.com/vincentchachere/virtual-machine).*

<p align="center">
<img width="800" alt="E2C30B0C-FA81-4329-8F23-DBB018C41018" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/4829d10a-d483-4c28-93a1-64034a6e0cf3">

</details>

<details>

<summary>

## ⚙️ Part B: Create a Virtual Machine

</summary>

### 2. ) Create a Virtual Machine inside the Resource Group

Use the same resource group and region you created earlier (RG-osTicket and US West 3). Name the virtual machine **vm-osticket**, select the imaging **Windows 10 Pro, version 22H2 - ×64 Gen2**, and set the size to **Standard_D45_v3 - 4 vcpus, 16 GiB memory**. Create a username and password you can easily remember (for the simplicity of the lab) and be sure to check the **licensing box** at the bottom. Review your information and proceed to create your virtual machine.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/4081f85f-969f-44ba-b922-173a14e9ac78">
<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d2ce647d-88fe-440a-9a34-387d4cc3b56d">

</details>

<details>

<summary>

## ⚙️ Part C: Remote Desktop into your Virtual Machine

</summary>

### 3. ) Connect your Virtual Machine to Remote Desktop (RDP)

Use the username and password you created earlier to connect via RDP.

*For help connecting Virtual Machines to Remote Desktop, refer to Step 5 in [my other lab](https://github.com/vincentchachere/virtual-machine)*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ccaac932-e865-4110-a96e-96d18b5b3cd0">

<br>
<br>
<br>

<ins>Connect your Virtual Machine to Remote Desktop</ins>:

Uncheck all the boxes and click accept.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/f59877e2-da56-4767-8cef-54cb4d0fdbe9">

</details>

<details>

<summary>

## ⚙️ Part D: Install Prerequisites

</summary>

### 4. ) Install and Enable IIS in Windows Virtual Machine

To install and enable IIS, right-click **Start** at the bottom-left corner, select **Run**, press **Enter**,**control panel**, and click **OK**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/8e9cc9b1-c20b-409d-867e-22b51ebc421b">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

Select **Programs**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3c279675-4075-4b70-9702-f319b73c7131">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

Select **Turn Windows Features On or Off**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3ef2747d-3665-48a8-9796-a482fd275039">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

Enable and Expand the **Internet Information Services (IIS)** and **World Wide Web Services** folders then check **all the Boxes** within this feature's folder.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ece03bc2-ec8a-4392-b658-b98b771be30b">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>

*While still inside the World Wide Web Service folder:*

Expand the **Application Development Features** folder and enable **CGI**. Collapse the **Application Development Features** folder and go back inside the **World Wide Web Service** folder.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7e2097ad-9abe-4db1-8f70-80c60d46548f">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

*Back inside the World Wide Web Service folder:*

Enable and expand the **Common HTTP Features** folder and check **All Boxes** within this feature's folder, then click **OK** when done.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/914c53a4-0fc9-45a5-9c9c-663e210b4828">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

When it's done enabling you can close it out.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c42e5f4f-43d5-4ef7-812a-d6cced5d7741"><br>

<br>
<br>
<br>

### 5. ) Open Microsoft Edge to Test IIS

Skip and uncheck any prompts Microsoft edge gives you when opening.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1e5c7aa4-97dd-4c8d-a09d-c9cafddda685"><br>

<br>
<br>
<br>

<ins>Testing IIS on Microsoft Edge</ins>:

Browse to **127.0.0.1**. If you don't see the image displayed below then try uninstalling and reinstalling IIS

***To Uninstall and Reinstall IIS** simply uncheck and disable everything you did when opening the IIS folder.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/7c2dae78-f8bb-40ba-9f73-b24d60b25c91">

<br>
<br>
<br>

### 6. ) Download PHP Manager for IIS

Open [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) in a separate tab and set up a split screen as shown below for easy access throughout the lab. Double-click **PHP ManagerForIIS_v1.5.0.msi** and click the **...** Dots in the upper right of your screen next to the 'Share' button, then select **Open in new window**.

*I've found this method to be the quickest and most reliable way to ensure a successful download on the first attempt, avoiding multiple tries.* 

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ced7d37b-baf3-4cb4-b165-a35a7185937a">

<br>
<br>
<br>

<ins>Downloading PHP Manager for IIS</ins>:

Click **Download anyway**

*You can either wait for it to pop up when its done loading or click the **...** Dots in the upper right corner of your screen then click **Downloads**. As well, you can go to **File Eplorer**, navigate to your **Downloads**, then select **PHP Manager**. Sometimes the file doesn’t pop up after downloading, so I’m showing you both methods to access it.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/a5b48037-ee60-470d-99bb-c08ce2027c9c">

<br>
<br>
<br>

<ins>Downloading PHP Manager for IIS</ins>:

Open the **PHP Manager** download and click **Next**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/d259bf88-439b-42cc-9375-166f003d8808">

<br>
<br>
<br>

<ins>Downloading PHP Manager for IIS</ins>:

Select **I Agree** and click **Next**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/9199a0ea-972d-455c-9408-5365677ed221">

<br>
<br>
<br>

<ins>Downloading PHP Manager for IIS</ins>:

Click **Close**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/ac09a285-6c4a-4ae0-8c33-2098d337d6f6">

<br>
<br>
<br>

### 7. ) Download Rewrite Module

Double-click **rewrite_amd64_en-US.msi** and open the download. Check the **I accept the terms in the License Agreement* box, click **Install**, then **Finish**.

*Download Rewrite Module the same way you did for PHP Manager*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/4dc65b4d-1b9e-455d-9045-f52b74fad6bd">

<br>
<br>
<br>

### 8. ) Create Directory C:\PHP

Now we will create the PHP directory inside File Explorer so that the ticketing system's PHP files can be stored and executed correctly.

Open **File Explorer** > **This PC** > **Windows (C:)**. Right-click the **empty space under the files** and click **New** then select **Folder**. Name the folder **PHP** and press **Enter**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d22ce8c2-06e5-4c52-b4c4-e6a0209efbc9">

<br>
<br>
<br>

<ins>Creating PHP Directory</ins>:

You should see your new **PHP Directory** inside your **Windows (c:) Drive** when your done.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1b5f5158-5e53-4950-8907-a23d7bd42c05">

<br>
<br>
<br>

### 9. ) Download php-7.3.8 and Unzip it into the Directory (C:\PHP) you just created

Download **php-7.3.8-nts-Win32-VC15-x86.zip** and go to **File Explorer** > **This PC** > **Downloads**. Right-click **php-7.3.8-nts-Win32-VC15-x86.zip** and select **Extract All**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/f850a7c2-2107-4113-9934-099ddeb63a12">

<br>
<br>
<br>

<ins>Download php-7.3.8 and Unzip it into the Directory (C:\PHP) you just created</ins>:

Click **Browse**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/557f2ee5-5215-4f94-ab3e-4b1e64f625a0">

<br>
<br>
<br>

<ins>Download php-7.3.8 and Unzip it into the Directory (C:\PHP) you just created</ins>:

Go to **This PC** > **Windows (C:)** > **PHP** and click **Select Folder**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3b00bffe-4b2b-4a8d-9777-7dfcff1a4fd9">

<br>
<br>
<br>

<ins>Download php-7.3.8 and Unzip it into the Directory (C:\PHP) you just created</ins>:

Click **Extract**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/bd6f48c3-9c8c-45bf-a96a-b01e47f70184">

<br>
<br>
<br>

<ins>Verify the php-7.3.8 made it into the PHP Directory</ins>:

Go back to **This PC** > **Windows (C:)** > **PHP**

*The **php.7.3.8** file is now inside the **PHP directory**.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/c6511b61-033a-46ff-9714-50b664e19c73"><br>

<br>
<br>
<br>

### 10. ) Download VC_redist.x86.exe

Download and open **VC_redist.x86.exe** then check the **I agree to the license terms and conditions** box and click **Install**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/170a61c1-fe3c-419f-8059-269bf6a5455c"><br>

<br>
<br>
<br>

<ins>Download VC_redist.x86.exe for IIS</ins>:

When it is done installing you can **Close** it.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/57eb8907-d6da-4abc-b39b-5d945d62c55f"><br>

<br>
<br>
<br>

### 11. ) Download MySQL 5.5.62

Download and open **MySQL 5.5.62** and click **Next**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/44a36637-43cc-4fcb-9d9b-6eb64c4315a4"><br>

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

Check the **I accept the terms in the License Agreement** box and click **Next**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1a768122-511d-44ef-a428-8a4dce09c2f9"><br>

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

Select **Typical Setup** and click **Next**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/14c18df3-e9ee-4cf9-a0e7-d2631f3beedf"><br>

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

Click **Install**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/f09cc5cc-9262-4951-b2ef-82d39e43ab70">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

Check the **Launch the MySQL Instance Configuration Wizard** box and click **Finish**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/110fd673-4225-4d28-968b-d4f0535e39b2">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

Click **Next**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/61f88e18-96bf-4991-9ad1-1222abf6cd00">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

Select **Standard Confirguration** and click **Next**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/16837f9b-9535-4306-8b45-93a1c984e611">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

Match your screen with the image below and click **Next**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/bcf52378-fb29-4fe8-8d2a-7ce1657bf457">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

Type **the password you used to log into remote desktop** and click **Next**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/cec6d46c-46d7-4db1-a897-deee162df7c8">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

When it's done configuring click **Finish**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/bccc6a00-de77-4266-a7f3-e5c12eb30c1b">

<br>
<br>
<br>

### 12. ) Open IIS as an Administrator and Register PHP from within IIS

**Run IIS as an administrator**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/a4190c4b-6bfe-4185-91f8-a141afcc24f5">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

Open **PHP Manager**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/44aefc87-57e7-4c5a-8087-b0d5548c57d1">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

Select **Register new PHP version** and click the box with the **three dots**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c9cc72d0-35ac-478c-8378-073a0378b976">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

Follow the path **This PC** > **Windows (C:)** > **PHP** and select **php-cgi** then click **Open**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/12b3b793-20da-4d32-bd71-8fbb3798019a">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

Click **OK**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/bf4becfe-54d8-40e7-9f36-195476f484ee">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

Click the **Home icon** in the upper right corner of IIS Window.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ae80d892-4d1d-4665-83d0-6e4605a2a7c4">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

**Restart IIS** to register the new PHP version.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7c0012c9-4c31-42a0-bfc2-4911bc46dae3">

</details>

<details>

<summary>

## ⚙️ Part E: Install osTicket

</summary>

### 13. ) Install osTicket v1.15.8

Download **osTicket** then open file explorer and follow the path: **This PC** > **Downloads** > **osTicket--v1.15.8**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/52102f4a-e0da-449e-844e-0117394c61a7">

<br>
<br>
<br>

<ins>Install osTicket</ins>:

Open a second file explorer and follow the path: **This PC** > **Windows (C:)** > **inetpub** > **wwwroot**

Drag and drop the **upload** folder from the first file explorer into the **wwwroot** that's inside the second file explorer.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/54aa0527-e724-48f3-898c-0c1797462f43">

<br>
<br>
<br>

<ins>Install osTicket</ins>:

Right-click the **upload** folder you put in the second file explorer and rename it to **osTicket**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/a92db299-809a-40c2-b194-9ba4b6f01f6b">

<br>
<br>
<br>

<ins>Install osTicket</ins>:

Spell the folder name exactly as **osTicket** (capital **T**, everything else lowercase) to avoid breaking hardcoded paths, file references, and configuration dependencies that are in the core PHP files, configuration files (`ost-config.php`), and web server settings.

*If osTicket isn't spelled correctly it will not work when we go to use.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/2f19fba0-01d9-413c-97b3-8fc1b71c78f2">

<br>
<br>
<br>

### 14. ) Refresh the osTicket site in your browser and observe the changes

Open **IIS as an administrator**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/c9e6f828-a8e4-4087-be9a-c257ac61efbf">

<br>
<br>
<br>

<ins>Refresh the osTicket site in your browser and observe the changes</ins>:

Click **Restart** so the changes you made can update.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7c0012c9-4c31-42a0-bfc2-4911bc46dae3">

<br>
<br>
<br>

<ins>Refresh the osTicket site in your browser and observe the changes</ins>:

Inside PHP Manager go to **Sites** > **Default Web Site** > **osTicket** and click **Browse: 80 (http)**

*Observe the features currently enabled and disabled within the osTicket browser. After enabling additional extensions in the next step, you’ll notice a few more features marked as enabled.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b3e46f6b-749d-4fec-a936-3231950c0228">

<br>
<br>
<br>

### 15. ) Enable Extensions for osTicket

Inside PHP Manager go to **Sites** > **Default Web Site** > **osTicket** and double-click **PHP Manager**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/d8d229e0-b240-4d9e-a330-752da0a27c6e">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

Click **Enable or Disable Extensions**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3b9e68b0-bc9c-4c13-b91e-337c98b91844">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

Right-click **php_imap.dll** and **Enable** the extension.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/fb7ac977-81e9-41b7-a397-34b53643734c">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

Right-click **php_intl.dll** and **Enable** the extension.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/fc6242b4-4676-4d9a-8432-8b7b728dcda4">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

Right-click **php_opache.dll** and **Enable** the extension.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/063d7e76-b27c-454f-b2ff-eed9ed49343d">

<ins>Enable Extensions for osTicket</ins>:

Verify all your extensions were enabled. You should see the 3 extensions you enabled in the enabled section of PHP extensions.

  - php_imap.dll
 
  - php_intl.dll

  - php_opache.dll

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d07178ce-15be-4b69-af43-f9c5107d5bb7">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

Refresh the **osTicket in your browser** and observe the changes. Refresh **IIS Manager** and click **Browse:80 (http)**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/bc60f3d9-52eb-40db-931b-4de82d184253">

<br>
<br>
<br>

### 16. ) Rename: ost-config.php

Open file explorer and follow the path: **This PC** > **Windows (C:)** > **inetpub** > **wwwroot** and open **osTicket**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/b38819f3-c9e7-4c11-a6e0-f39d3de4f4ee">

<br>
<br>
<br>

<ins>Rename: ost-config.php</ins>:

Scroll all the way down in the **include** folder and open the **include** folder.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/3f8b1c3c-01c9-46a2-a23e-5336a441bfd3">

<br>
<br>
<br>

<ins>Rename: ost-config.php</ins>:

Rename **ost-sampleconfig.php** to **ost-config.php**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/c0e4ab41-43ce-4591-8454-4eae38bec613">

<br>
<br>
<br>

17. ) Assign Permissions To: ost-config.php

Go to the **ost-config.php** PHP file **Properties**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/94df787f-4506-47ae-bc96-4bcc1d8bd9a0">

<br>
<br>
<br>

<ins>Assign Permissions To: ost-config.php</ins>:

Go to the **Security** tab, select **Advanced**, **Disable Inheritance**, and **Remove all inherited permissions from this object**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b80a7030-5965-471d-a583-09df1697d833">

<br>
<br>
<br>

<ins>Assign Permissions To: ost-config.php</ins>:

In the Permission Entry window for ost-config.php: **Add** > **Select a principal** > Add: **Everyone** > **Check Names** > **OK**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/415292b6-fd23-4f4c-a781-1f45c2d4727f">

<br>
<br>
<br>

<ins>Assign Permissions To: ost-config.php</ins>:

Select **Full Control** *(make sure all boxes are checked as seen in the image below)* > **OK** > **OK** again

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/164a3e42-9c4a-4363-9742-0fd445f68d93">

<br>
<br>
<br>

### 18. ) Restart IIS Manager and Continue Setting Up osTicket in the Browser

Click **Restart** then **Continue**. 

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1132dfa8-668a-4180-a0bf-a78108e571ff">

<br>
<br>
<br>

<ins>Continue Setting up osTicket in the browser</ins>:

  - Helpdesk Name: `Helpdesk`

  - Default Email: `firstname@helper.com`

  - First Name: *AnythingYouWantJustRememberIt*

  - Last Name: *AnythingYouWantJustRememberIt*

  - Email Address: `firstname@gmail.com`

  - Username: *AnythingYouWantJustRememberIt*

  - Password: *AnythingYouWantJustRememberIt*

*Before finishing the setup you need to download HiediSQL first, so go to the next. We'll come back to this after, leave it as is.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/25255d72-3702-4528-9c1a-180bd627eac6">

<br>
<br>
<br>

### 19. ) Download and Install HeidiSQL

Download and open **HiediSQL**, select **I accept the agreement**, and click **Next** until you reach the **Ready to Install** window.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/b9122a6b-f4c2-4055-95f8-86951eab4e8b">

<br>
<br>
<br>

<ins>Installing HeidiSQL</ins>:

Select **Install** > **Finish** > **Skip**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/0411ef50-139c-47df-8316-a93dbe99e028">

<br>
<br>
<br>

<ins>Installing HeidiSQL</ins>:

- User: `root`

- Password: `The one you created earlier`

Click **Open** to connect to the session.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/51779cfc-4be7-4a12-8a82-944298bc67bd">

<br>
<br>
<br>

### 20. ) Create a Database for osTicket called `osTicket`

Right-click: **Unnamed** > Select: **Create new** > Select: **Database**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1ff3b586-e13e-43e6-9bf4-35e5bc921f57">

<br>
<br>
<br>

<ins>Create a Database for osTicket called **osTicket**</ins>:

Name of Database: **osTicket** (*Spell check before continuing - capital **T** lowercase everything else*)

Click **OK** when finished.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/8c806266-acbb-492c-a24b-e33bee43957f">

<br>
<br>
<br>

### 21. ) Finish Setting up osTicket in the browser

- MySQL Database: `osTicket`

- MySQL Username: `root`

- MySQL Password: `The one you created earlier`

- Click: `Install Now`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/6fe660ac-3e26-4c95-aa79-ef671d26c8fe">

<br>
<br>
<br>

<h2 align="center">Congragulations! osTicket is officially installed.. but we're not finished yet!</h2>

<h4 align="center">Continue to the next part to finish this lab</h4>

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/7f4988fb-ea09-4432-b689-dedfe5b96449">

</details>

<details>

<summary>

## ⚙️ Part G: Clean Up Resources

</summary>

### 22. ) Clean Up Resources

*Browse to your help desk login page:* `http://localhost/osTicket/scp/login.php`

Before logging in we need to do 2 Things: Delete the **setup** folder inside the osTicket folder and change file permissions for **ost-config.php** by setting it's permissions to **Read only**.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b9d87a44-1ed6-4cab-aa7f-bc5d1cac736f">

<br>
<br>
<br>

<ins>Cleaning Up Resources: Deleting **setup** folder inside osTicket</ins>:

First, delete the **setup** file folder inside the osTicket folder.

Follow the path: **This PC** > **Windows (C:)** > **inetpub** > **wwwroot** > **osTicket**

*ONLY DELETE THE **setup** FILE FOLDER - NOT THE WHOLE THING*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/6698c705-e677-4ab2-a88c-5bc268dd3ec3">

<br>
<br>
<br>

<ins>Change File Permissions for **ost-config.php** to **Read Only**</ins>:

Follow the path: **This PC** > **Windows (C:)** > **inetpub** > **wwwroot** > **osTicket** > **include** > **ost-config.php**

Scroll all the way down and go to the **ost-config.php** PHP file properties.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/a532e9ec-56e1-44a6-a8e1-7e02bf41ef61">

<br>
<br>
<br>

<ins>Change File Permissions for **ost-config.php** to **Read Only**</ins>:

To change the file permissions for **ost-config.php** to **Read-Only**** follow the path: **Security** > **Advanced** > **Edit**

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/2a6d1252-bbe4-40e9-ad8d-f95e948e9d53">

<br>
<br>
<br>

<ins>Change File Permissions for **ost-config.php** to **Read Only**</ins>:

Check the **Read** and **Read & execute** permissions. Uncheck **Full Control**, **Modify**, and **Write** permissions then click **Apply**, **OK**, **OK** again.

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c3e6a61a-383a-48e1-a867-795dce74c678">

<br>
<br>
<br>

### 23. ) Login To: http://localhost/osTicket/scp/login.php

- Username: *`The one you used in Part E: Step 21`*

- Password: *`The one you used in Part E: Step 21`*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1b7c8e91-5375-40d9-90c2-45c2fcf7aef1">

<br>
<br>
<br>

<h2 align="center">Now you are successfully inside osTicket!</h2>

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/ef1ee657-b978-4494-acb7-7a4e3585acca">

<br>
<br>
<br>

### Here is the End Users osTicket URL for the next lab that builds off this one:

- http://localhost/osTicket/ 

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/e5bb86f6-de48-47f3-bcb5-97cbb620e6d8">

</details>

<h2 align="center">Final Thoughts</h2>

This lab demonstrated the prerequisites and installation process of the osTicket helpdesk ticketing system, leveraging tools such as Microsoft Azure, IIS, and Remote Desktop to set up a virtual environment. By completing each step, from configuring the virtual machine to installing and enabling necessary components, we successfully deployed osTicket.

With the installation complete, we can now focus on configuring osTicket to ensure it is tailored to our organization’s needs. This involves setting up roles, departments, teams, agents, and users, as well as defining Service Level Agreements (SLAs). These configurations are crucial for streamlining ticket management, ensuring efficient workflows, and enabling the system to properly route and track support requests.

To continue the osTicket tutorial series, proceed to the next lab on [post-installation and configuration for osTicket](https://github.com/vincentchachere/Ticket-Lifecycle).

Thank you for following along with this project. Your time and effort in learning and implementing these concepts are greatly appreciated.

☎️ For questions or to connect you can reach me at: www.linkedin.com/in/vincentchachere
