<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Prerequisites and Installation

In this lab, we set up the osTicket helpdesk system by completing its prerequisites and installation. Using tools like Microsoft Azure, IIS, and Remote Desktop, we prepare a virtual environment, configure necessary components, and install osTicket step-by-step.

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
- Download & Install [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
  - Install/Enable IIS in Windows
  - Enable Extensions for osTicket
  - Rename: ost-config.php
  - Assign Permissions To: ost-config.php
  - Create a database for 'osTicket'
- Clean Up Resources
- Change File Permissions

## Installation Files

- https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<details>

<summary>

## ⚙️ Part A: Create a Resource Group

</summary>

### 1. ) Create a Resurce Group

*For assistance on creating Virtual Machines and Resource Groups go to my other lab [here](https://github.com/vincentchachere/virtual-machine)

<ins>Input the following Information</ins>:

- Resource Group Name: `RG-osTicket`

- Region: `(US) West US 3`

- Click: `Review + Create`

- Click: `Create`

*Double-check spelling when creating resources (e.g., resource groups, virtual machines). Names, regions, and similar inputs cannot be edited after creation. Errors may require deleting and restarting your work.*

<p align="center">
<img width="800" alt="E2C30B0C-FA81-4329-8F23-DBB018C41018" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/4829d10a-d483-4c28-93a1-64034a6e0cf3">

</details>

<details>

<summary>

## ⚙️ Part B: Create a Virtual Machine

</summary>

### 2. ) Create a Virtual Machine inside the Resource Group

<ins>Input the following Information</ins>:

*Fill in everything displayed in the image below.*

- Select Resource Group Name: `RG-osTicket` (The one you created in Part A: Step 1)

- Virtual Machine Name: `vm-osticket` (all lowercase)

- Region: `(US) West 3`

- Image: `Windows 10 Pro, version 22H2 - ×64 Gen2`

- Size: `Standard_D45_v3 - 4 vcpus, 16 GiB memory ($140.16/month)`

- Username: `vincentchachere` (this can be whatever you want - just remember it)

- Password: `whatever-you-want` (just remember it)

- Check: The `Licensing` Box

- Select: `Review and Create`

- Click: `Create`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/4081f85f-969f-44ba-b922-173a14e9ac78">
<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d2ce647d-88fe-440a-9a34-387d4cc3b56d">

</details>

<details>

<summary>

## ⚙️ Part C: Remote Desktop into your Virtual Machine

</summary>

### 3. ) Connect your Virtual Machine to Remote Desktop

*For assistance on connecting Virtual Machines to Remote Desktop go to Step 5 on [this lab](https://github.com/vincentchachere/virtual-machine)*

- Username: `vincentchachere` (whatever you created in Part B: Step 2)

- Password: `Your Password` (whatever you created in Part B: Step 2)

- Click: `Continue`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ccaac932-e865-4110-a96e-96d18b5b3cd0">

<br>
<br>
<br>

<ins>Connect your Virtual Machine to Remote Desktop</ins>:

- Uncheck: `All Boxes`

- Click: `Accept`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/f59877e2-da56-4767-8cef-54cb4d0fdbe9">

</details>

<details>

<summary>

## ⚙️ Part D: Install Prerequisites

</summary>

### 4. ) Install and Enable IIS in Windows Virtual Machine

<ins>Once inside your Virtual Machine we'll need to Install and Enable IIS by doing the following</ins>:

  - Right-Click: `Start` in the bottom left corner of your screen

  - Select: `Run`

*Or you could just type `run` inside the search bar and press `Enter`*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/6f279019-c2f3-4446-b4f1-76e5cf798e2b">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

- Type In: `Control Panel`

- Click: `OK`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/789188b7-01d1-45b8-a805-bbd6ff0594aa">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

  - Select: `Programs`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3c279675-4075-4b70-9702-f319b73c7131">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

  - Select: `Turn Windows Features On or Off`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3ef2747d-3665-48a8-9796-a482fd275039">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:
                              
  - Enable and Expand: `Internet Information Services (IIS)`
 
  - Enable and Expand: `World Wide Web Services`

    - Check: `All Boxes` within this feature's folder

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ece03bc2-ec8a-4392-b658-b98b771be30b">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>

*While still inside the World Wide Web Service folder:*

  - Expand: `Application Development Features` folder

  - Enable: `CGI`

  - Collapse: `Application Development Features` folder

  - Go Back Inside: `World Wide Web Service` folder

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7e2097ad-9abe-4db1-8f70-80c60d46548f">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

*Back inside the World Wide Web Service folder:*

  - Enable and Expand: Common HTTP Features

  - Check: `All Boxes` within this feature's folder
 
  - Click: `OK`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/914c53a4-0fc9-45a5-9c9c-663e210b4828">

<br>
<br>
<br>

<ins>Install and Enable IIS in Windows Virtual Machine</ins>:

- Wait for it to load...

- When that's done loading..

- Click: `Close`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c42e5f4f-43d5-4ef7-812a-d6cced5d7741"><br>

<br>
<br>
<br>

### 5. ) Open Microsoft Edge to Test IIS

*Skip all the prompts it gives you when opening Microsoft edge*

- Open: `Microsoft Edge` Internet Browser

- Click: `Start without your data`

- *Uncheck the Box*

- Clcik :`Conirm and Continue`

- Click: `Continue without this data`

- Uncheck: `the Box`

- Click: `Confirm and start browsing`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1e5c7aa4-97dd-4c8d-a09d-c9cafddda685"><br>

<ins>Testing IIS on Microsoft Edge</ins>:

- Type: `127.0.0.1` into the browser

  - If you do not see the image displayed below then try uninstalling and reinstalling IIS

*The **How To Uninstall and Reinstall Instructions** are directly underneath the image below.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/7c2dae78-f8bb-40ba-9f73-b24d60b25c91">

*<ins>To Uninstall and Reinstall IIS do the following</ins>:*

- *Right-Click: `Start` > Click: `Run`*

- *Type In: `Control` > Click: `Programs`*

- *Click: `Turn Windows on or off`*

- *Uncheck: `IIS` > *Uncheck:* `World Wide Web Services`*

- *Uncheck: `Application Development Features` (Inside World Wide Web Services)*

- *Uncheck: `CGI` (Application Development Features)*

- *Uncheck: `Common HTTP Feautures` (Inside World Wide Web Services)*

- *Uncheck: `HTTP Redirection` (Inside Common HTTP Feautures)*

- *Uncheck: `WebDAV Publishing` (Inside Common HTTP Feautures)*

<br>
<br>
<br>

### 6. ) Download PHP Manager for IIS

*Open the installation files in a separate tab and set up a split screen as shown below for easy access throughout the lab.*

- Open: [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

- Double-Click: `PHP ManagerForIIS_v1.5.0.msi`

- Click: The `...` Dots in the upper right of your screen next to the 'Share' button

- Click: `Open in new window`

*I've found that this method is the quickest and most reliable way to ensure a successful download on the first attempt, avoiding multiple tries.* 

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ced7d37b-baf3-4cb4-b165-a35a7185937a">

<br>
<br>
<br>

<ins>Downloading PHP Manager for IIS</ins>:

- Click: `Download anyway`

*You can either wait for it to pop up when its done loading or click the **...** Dots in the upper right corner of your screen then click **Downloads**. As well, you can go to **File Eplorer**, navigate to your **Downloads**, then select **PHP Manager**.*

*Sometimes the file doesn’t pop up after downloading, so I’m showing you both methods to access it.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/a5b48037-ee60-470d-99bb-c08ce2027c9c">

<br>
<br>
<br>

<ins>Downloading PHP Manager for IIS</ins>:

- Open: the `PHP Manager` download

- Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/d259bf88-439b-42cc-9375-166f003d8808">

<br>
<br>
<br>

<ins>Downloading PHP Manager for IIS</ins>:

- Select: `I Agree`

- Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/9199a0ea-972d-455c-9408-5365677ed221">

<br>
<br>
<br>

<ins>Downloading PHP Manager for IIS</ins>:

- Click: `Close`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/ac09a285-6c4a-4ae0-8c33-2098d337d6f6">

<br>
<br>
<br>

### 7. ) Download Rewrite Module

*Download Rewrite Module the same way you did for PHP Manager*

- Double-Click: `rewrite_amd64_en-US.msi`

- Open: the `rewrite_amd64_en-US.msi` download

- Check: the `I accept the terms in the License Agreement` box

- Click: `Install`

- Click: `Finish`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/4dc65b4d-1b9e-455d-9045-f52b74fad6bd">

<br>
<br>
<br>

### 8. ) Create Directory C:\PHP

- Go To: `File Explorer` > `This PC` > `Windows (C:)`

- Right-Click: The `empty space under the files`

- Go To: `New`

- Click: `Folder`

- Type In: `PHP`

- Press: `Enter`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d22ce8c2-06e5-4c52-b4c4-e6a0209efbc9">

<br>
<br>
<br>

<ins>Creating PHP Directory</ins>:

*You should see your new PHP Directory inside your Windows (c:) Drive when your done.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1b5f5158-5e53-4950-8907-a23d7bd42c05">

<br>
<br>
<br>

### 9. ) Download php-7.3.8 and Unzip it into the Directory (C:\PHP) you just created

- Download: `php-7.3.8-nts-Win32-VC15-x86.zip`

- Go To: `File Explorer` > `This PC` > `Downloads`

- Righ-Click: `php-7.3.8-nts-Win32-VC15-x86.zip`

- Select: `Extract All`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/f850a7c2-2107-4113-9934-099ddeb63a12">

<br>
<br>
<br>

<ins>Download php-7.3.8 and Unzip it into the Directory (C:\PHP) you just created</ins>:

- Click: `Browse`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/557f2ee5-5215-4f94-ab3e-4b1e64f625a0">

<br>
<br>
<br>

<ins>Download php-7.3.8 and Unzip it into the Directory (C:\PHP) you just created</ins>:

- Go To: `This PC` > `Windows (C:)` > `PHP`

- - Click: `Select Folder`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3b00bffe-4b2b-4a8d-9777-7dfcff1a4fd9">

<br>
<br>
<br>

<ins>Download php-7.3.8 and Unzip it into the Directory (C:\PHP) you just created</ins>:

- Click: `Extract`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/bd6f48c3-9c8c-45bf-a96a-b01e47f70184">

<br>
<br>
<br>

<ins>Verify the php-7.3.8 made it into the PHP Directory</ins>:

- Go Back To: `This PC` > `Windows (C:)` > `PHP`

*You will now see the **php.7.3.8** file inside the PHP directory, as shown in the image below.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/c6511b61-033a-46ff-9714-50b664e19c73"><br>

<br>
<br>
<br>

### 10. ) Download VC_redist.x86.exe

- Download and Open: `VC_redist.x86.exe`

- Check: the `I agree to the license terms and conditions` Box

- Click: `Install`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/170a61c1-fe3c-419f-8059-269bf6a5455c"><br>

<br>
<br>
<br>

<ins>Download VC_redist.x86.exe for IIS</ins>:

*When it is done installing..*

- Click: `Close`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/57eb8907-d6da-4abc-b39b-5d945d62c55f"><br>

<br>
<br>
<br>

### 11. ) Download MySQL 5.5.62

- Download and Open: `MySQL 5.5.62`

  - Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/44a36637-43cc-4fcb-9d9b-6eb64c4315a4"><br>

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

- Check: the `I accept the terms in the License Agreement` box

- Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1a768122-511d-44ef-a428-8a4dce09c2f9"><br>

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

- Select: `Typical Setup`

- Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/14c18df3-e9ee-4cf9-a0e7-d2631f3beedf"><br>

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

- Click: `Install`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/f09cc5cc-9262-4951-b2ef-82d39e43ab70">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

- Check: the `Launch the MySQL Instance Configuration Wizard` box

- Click: `Finish`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/110fd673-4225-4d28-968b-d4f0535e39b2">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

- Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/61f88e18-96bf-4991-9ad1-1222abf6cd00">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

- Select: `Standard Confirguration`

- Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/16837f9b-9535-4306-8b45-93a1c984e611">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

- Make sure your screen matches the image below and once you verify that it does..&darr;

- Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/bcf52378-fb29-4fe8-8d2a-7ce1657bf457">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

- Type In: `The password you used to log into remote desktop.`

  - Click: `Next`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/cec6d46c-46d7-4db1-a897-deee162df7c8">

<br>
<br>
<br>

<ins>Download MySQL 5.5.62 for IIS</ins>:

*When it's done configuring..*

- Click : `Finish`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/bccc6a00-de77-4266-a7f3-e5c12eb30c1b">

<br>
<br>
<br>

### 12. ) Open IIS as an Administrator and Register PHP from within IIS

- Search: `IIS`

- Right-Click: `IIS`

- Select: `Run as Administrator`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/a4190c4b-6bfe-4185-91f8-a141afcc24f5">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

- Double-Click: `PHP Manager`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/44aefc87-57e7-4c5a-8087-b0d5548c57d1">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

- Click: `Register vew PHP version`

- Click: the `...` box

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c9cc72d0-35ac-478c-8378-073a0378b976">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

- Follow this path: `This PC` > `Windows (C:)` > `PHP`

- Select: `php-cgi`

- Click: `Open`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/12b3b793-20da-4d32-bd71-8fbb3798019a">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

- Click: `OK`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/bf4becfe-54d8-40e7-9f36-195476f484ee">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

- Click: the `Home` icon in the upper right corner of IIS Window

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ae80d892-4d1d-4665-83d0-6e4605a2a7c4">

<br>
<br>
<br>

<ins>Open IIS as an Administrator and Register PHP from within IIS</ins>:

- Click: `Restart`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7c0012c9-4c31-42a0-bfc2-4911bc46dae3">

</details>

<details>

<summary>

## ⚙️ Part E: Install osTicket

</summary>

### 13. ) Install osTicket v1.15.8

- Download: `osTicket`

- Open File Explorer and Go To: `This PC` > `Downloads` > `osTicket--v1.15.8`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/52102f4a-e0da-449e-844e-0117394c61a7">

<br>
<br>
<br>

<ins>Install osTicket</ins>:

- Open: A Second `File Explorer`

- In The Second File Explorer Go To: `This PC` > `Windows (C:)` > `inetpub` > `wwwroot`

- Drag and Drop: `upload` from the first File Explorer into the `wwwroot` that's inside the second File Explorer

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/54aa0527-e724-48f3-898c-0c1797462f43">

<br>
<br>
<br>

<ins>Install osTicket</ins>:

- Right-Click: `upload` (*the **upload** that is in the new File Explorer you just opened*)

- Click: `Rename`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/a92db299-809a-40c2-b194-9ba4b6f01f6b">

<br>
<br>
<br>

<ins>Install osTicket</ins>:

- Type In: `osTicket`

- Press: `Enter`

*Spell the folder name exactly as **osTicket** (capital **T**, everything else lowercase) to avoid breaking hardcoded paths, file references, and configuration dependencies that are in the core PHP files, configuration files (`ost-config.php`), and web server settings.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/2f19fba0-01d9-413c-97b3-8fc1b71c78f2">

<br>
<br>
<br>

### 14. ) Refresh the osTicket site in your browser and observe the changes

- Open: `IIS` <ins>as an Administrator</ins>

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/c9e6f828-a8e4-4087-be9a-c257ac61efbf">

<br>
<br>
<br>

<ins>Refresh the osTicket site in your browser and observe the changes</ins>:

- Click: `Restart`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7c0012c9-4c31-42a0-bfc2-4911bc46dae3">

<br>
<br>
<br>

<ins>Refresh the osTicket site in your browser and observe the changes</ins>:

- Inside PHP Manager Go to: `Sites` > `Default Web Site` > `osTicket`

- Click: `Browse*: 80`

*Observe the features currently enabled and disabled within the osTicket browser. After enabling additional extensions in the next step, you’ll notice a few more features marked as enabled.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b3e46f6b-749d-4fec-a936-3231950c0228">

<br>
<br>
<br>

### 15. ) Enable Extensions for osTicket

- Inside PHP Manager Go to: `Sites` > `Default Web Site` > `osTicket`

- Double-Click: `PHP Manager`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/d8d229e0-b240-4d9e-a330-752da0a27c6e">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

- Click: `Enable or Disable Extensions`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3b9e68b0-bc9c-4c13-b91e-337c98b91844">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

- Right-Click: `php_imap.dll`

- Click: `Enable`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/fb7ac977-81e9-41b7-a397-34b53643734c">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

- Right-Click: `php_intl.dll`

- Click: `Enable`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/fc6242b4-4676-4d9a-8432-8b7b728dcda4">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

- Right-Click: `php_opache.dll`

- Click: `Enable`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/063d7e76-b27c-454f-b2ff-eed9ed49343d">

<ins>Enable Extensions for osTicket</ins>:

*Verify all your extensions were enabled*

- You should see the 3 following extensions in the `enabled` section:

  - php_imap.dll
 
  - php_intl.dll

  - php_opache.dll

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d07178ce-15be-4b69-af43-f9c5107d5bb7">

<br>
<br>
<br>

<ins>Enable Extensions for osTicket</ins>:

- Refresh: the `osTicket in your browser` and observe the changes

- Refresh: `IIS Manager`

- Click: `Browse*:80 (http)`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/bc60f3d9-52eb-40db-931b-4de82d184253">

<br>
<br>
<br>

### 16. ) Rename: ost-config.php

- Open File Explorer and Go To: `This PC` > `Windows (C:)` > `inetpub` > `wwwroot`

- Double-Click: `osTicket`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/b38819f3-c9e7-4c11-a6e0-f39d3de4f4ee">

<br>
<br>
<br>

<ins>Rename: ost-config.php</ins>:

*Scroll all the way down within the **include** folder*

- Double-Click: `include`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/3f8b1c3c-01c9-46a2-a23e-5336a441bfd3">

<br>
<br>
<br>

<ins>Rename: ost-config.php</ins>:

- Right-Click: `ost-sampleconfig.php`

  - Click: `Rename`

  - Rename: `ost-sampleconfig.php`
 
  - To: `ost-config.php`
 
  - Press: `Enter` when done typing in the name

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/c0e4ab41-43ce-4591-8454-4eae38bec613">

<br>
<br>
<br>

17. ) Assign Permissions To: ost-config.php

- Right-Click: `ost-config.php`

- Click: `Properties`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/94df787f-4506-47ae-bc96-4bcc1d8bd9a0">

<br>
<br>
<br>

<ins>Assign Permissions To: ost-config.php</ins>:

- Click: `Security`

- Click: `Advanced`

- Select: `Disable Inheritance`

- Click: `Remove all inherited permissions from this object`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b80a7030-5965-471d-a583-09df1697d833">

<br>
<br>
<br>

<ins>Assign Permissions To: ost-config.php</ins>:

- Click: `Add` > `Select a principal` > Enter the Object Name: `Everyone` > Click: `Check Names`

- Click: `OK`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/415292b6-fd23-4f4c-a781-1f45c2d4727f">

<br>
<br>
<br>

<ins>Assign Permissions To: ost-config.php</ins>:

- Select: `Full Control` *(make sure all boxes are checked as seen in the image below)*

- Click: `OK`

- Click: `OK` again

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/164a3e42-9c4a-4363-9742-0fd445f68d93">

<br>
<br>
<br>

### 18. ) Restart IIS Manager and Continue Setting Up osTicket in the Browser

- Click: `Restart`

- Click: `Continue` 

<p align="center">
<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1132dfa8-668a-4180-a0bf-a78108e571ff">

<br>
<br>
<br>

<ins>Continue Setting up osTicket in the browser</ins>:

  - Helpdesk Name: `Helpdesk`

  - Default Email: `firstname@helper.com`

  - First Name: *AnythingYouWant* (*just remember it*)

  - Last Name: *AnythingYouWant* (*just remember it*)

  - Email Address: `firstname@gmail.com`

  - Username: *AnythingYouWant* (*just remember it*)

  - Password: *AnythingYouWant* (*just remember it*)

*Before finishing the setup you need to download HiediSQL first, so go to the next. We'll come back to this after, leave it as is.*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/25255d72-3702-4528-9c1a-180bd627eac6"><br>

<br>
<br>
<br>

### 19. ) Download and Install HeidiSQL

- Download: `HiediSQL`

- Open: `HiediSQL`

- Select: the `I accept the agreement`

- Click: `Next` until you reach the **Ready to Install**

- 

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/b9122a6b-f4c2-4055-95f8-86951eab4e8b"><br>

<br>
<br>
<br>

<ins>Installing HeidiSQL</ins>:

- Click: `Install`

- Click: `Finish` then..

- Click: `Skip`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/0411ef50-139c-47df-8316-a93dbe99e028"><br>

<br>
<br>
<br>

<ins>Installing HeidiSQL</ins>:

- User: `root`

- Password: `The one you created earlier`

- Click: `Open` to connect to session

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/51779cfc-4be7-4a12-8a82-944298bc67bd"><br>

<br>
<br>
<br>

### 20. ) Create a Database for osTicket called `osTicket`

- Right-Click: `Unamed`

- Click: `Create new`

- Click: `Database`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1ff3b586-e13e-43e6-9bf4-35e5bc921f57"><br>

<br>
<br>
<br>

<ins>Create a Database for osTicket called **osTicket**</ins>:

- Type In: `osTicket` be sure to type it in exactly like that (*capital **T** lowercase everything else*)

- Click: `OK`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/8c806266-acbb-492c-a24b-e33bee43957f"><br>

<br>
<br>
<br>

### 21. ) Continue Setting up osTicket in the browser

- MySQL Database: `osTicket`

- MySQL Username: `root`

- MySQL Password: `The one you created earlier`

- Click: `Install Now`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/6fe660ac-3e26-4c95-aa79-ef671d26c8fe"><br>

<br>
<br>
<br>

#### Congratulations! Hopefully osTicket is installed with no errors, but we are not finished just yet!

*Go to the next part to continue finishing this lab*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/7f4988fb-ea09-4432-b689-dedfe5b96449"><br>

</details>

<details>

<summary>

## ⚙️ Part G: Clean Up Resources

</summary>

### 22. ) Clean Up Resources

- Browse to your help desk login page: `http://localhost/osTicket/scp/login.php`

<ins>Before logging in we need to do 2 Things</ins>:

- Clean Up Resources

  - 1st Thing - Delete: c:\inept\wwwroot\osTicket\\*`setup`*

- Change File Permissions

  - 2nd Thing - Set Permissions to `Read` <ins>only</ins> for: This PC > inetpub > wwwroot > osTicket > include > *`ost-config.php`*

<ins>Scroll down to `Step 37.B` for further instruction</ins>

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/94a00827-144e-435d-abaa-f2b052d6cb74"><br>

<br>
<br>
<br>

<ins>Clean Up Resources</ins>:
  
  - Delete: c:\inept\wwwroot\osTicket\`setup`

    - ONLY DELETE THE `setup` PART - NOT THE WHOLE THING

*Go To: `Part H: Change File Permissions` for the 2nd Thing*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1fcc1edd-c8da-406e-aaee-495acdd2ab82"><br>

</details>

<details>

<summary>

## ⚙️ Part H: Change File Permissions

</summary>

<ins>2nd Thing: Set Permissions to `Read` only for `ost-config.php`</ins>:

  - File Explorer: This PC > inetpub > wwwroot > osTicket > include > *`ost-config.php`*

    - Right-Click: *`ost-config.php`*
 
    - Select: `Properties`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/a532e9ec-56e1-44a6-a8e1-7e02bf41ef61"><br>

<br>
<br>
<br>

### 38.A ) Change File Permissions

<ins>2nd Thing Set Permissions to `Read` only for `ost-config.php`</ins>:

- Go To: `Security` > `Advanced` > `Edit`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/251d87d6-5fec-4133-a470-113d61ee3905"><br>

<br>
<br>
<br>

### 38.B ) Change File Permissions

<ins>2nd Thing: Set Permissions to `Read` only for `ost-config.php`</ins>:

- Only Check: `Read` and `Read & execute` 

  - Uncheck: `Full Control`

  - Uncheck: `Modify`

  - Uncheck: `Write`

- Click: `Apply`

- Click: `Ok`

- Click: `Ok`

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/bd4424a4-45d3-4b57-8190-7c900d90c374"><br>

***

### 39.A ) Login To: http://localhost/osTicket/scp/login.php

- Username: *`The one you created at Step 34.A and the one you used at Step 35.H`*

- Password: *`The one you created at Step 34.A and the one you used at Step 35.H`*

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/1b7c8e91-5375-40d9-90c2-45c2fcf7aef1"><br>

***

### 39.B ) Now you are successfully inside osTicket! Congrats!

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/ef1ee657-b978-4494-acb7-7a4e3585acca"><br>

***

### 40. ) End Users osTicket URL:

- http://localhost/osTicket/ 

<p align="center">
<img width="800" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/e5bb86f6-de48-47f3-bcb5-97cbb620e6d8"><br>

***

☎️ For any questions, or just to connect, you can message me at: www.linkedin.com/in/vincentchachere

</details>
