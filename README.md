<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Prerequisites and Installation
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br/>

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

## Operating Systems Used

- Windows Windows 10 (21H2)

## List of Prerequisites

- Connect to your Virtual Machine with Remote Desktop
- Install / Enable IIS in Windows
- Install Web Platform Installer
- Install osTicket v1.15.8
- Download and Install HeidiSQL
- Created database for "osTicket
- Clean up 
- Change File Permissions

<br>

________________________________________________________________________________________________________________________<br>

# 📝 Installation Steps - Part A: Create a 'Resource Group'

<br>

## 1. ) Starting at the 'Home' screen in your Microsoft Azure Portal

- Click: the 'Resource Groups' icon that's already on your home screen or..

- You can Search: 'Resource Groups' and click that one. It will take you to the same place, which is the 'Resource Groups Default Directory'

<img width="1511" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/d273a110-a34c-4707-8a06-058d12c11cc5"><br>

 >**NOTE: You can make a 'Resource Group' at the same time you create a VM. I just wanted to show you how to do it step-by-step.**

***

<br>
 
## 2. ) Click 'Create' to start your resource group

- Or..

- You can click the blue 'Create' in the middle of the screen as well, and it will take you to the same place.
 
<img width="1511" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/56fec2c9-0ba3-4e35-8c26-6bc6e7e6313b"><br>

***

<br>

## 3. ) Next, we'll input the following:

- Resource Group Name: RG-osTicket

- Region: (US) West US 3

- *Scroll Down*

 >**ATTENTION: Double check spelling when creating anything (resource groups, virtual machines, etc.) or you will have to delete all your work and start over, because the information you input will NOT be able to be able to be edited once it's created (name, region, etc.)**

<img width="1511" alt="E2C30B0C-FA81-4329-8F23-DBB018C41018" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/4829d10a-d483-4c28-93a1-64034a6e0cf3"><br>

***

<br>

## 4. ) Now, let's click 'Review + Create'

- Dont worry about the 'Tags' section, we don't need that part for this lab.

- The 'Tags' section is used for organizational purposes.

<img width="1511" alt="F462BC66-31ED-444E-A61B-CD02C75151FD" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/22252a11-ece8-4e38-873c-f6faf00efe29"><br>

 >**NOTE: We have NOT finished creating the resource group yet by clicking 'Review + Create'. Microsoft Azure let's you double check (review) the information you input before finalizing (creating) your resource group. It also does this for virtual machines, so make it a habit to double check the information you type in, so that you don't have to erase everything you end up creating, because of one wrong letter.**

***

<br>

## 5. ) Finally, we review and create!

- Look over the resource group information.

- Verify its all correct.

- Click 'Create' to bring alive our first resource group!

<img width="1511" alt="6353AD56-C708-4D3D-ABEB-7C29A8E42E5F" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/2f2d3265-2f3f-457f-a710-1be04c7d9545"><br>

***

<br>

## Congrats!

### 6. ) You're done creating you're Resource Group!

- You should see the 'Successfully Ceated Resource Group Notification' in the top right corner of your screen.

- Click 'Refresh' if you dont see your Resource Group, then..

- Click your resource group 'RG-osTicket' to enter into the next part of this lab.

<img width="1509" alt="3C89D03C-0D84-4484-BFD6-79D2FBDF9012" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/e2981d35-3f56-4b35-a47d-d2dafd1600a6"><br>

 >**NOTE: Whenever you create a resource group or virtual machine and DO NOT see it in your Azure Portal in its correct location, there's two solutions to this:**

 >**First, refresh your Resource Group Default Directory (Search: Resource Group and you'll be in that section), and if that's unsuccessful..**

 >**Go through the steps again in this lab and if it doesn't let you create a resource group with the name 'RG-osTicket' (the name you originally typed in for the resurce group), then that's how you know the Resource Group is created, you will just have to wait a little longer and refresh your Resource Group Default Directory.**

________________________________________________________________________________________________________________________<br>

# 📝 Installation Steps - Part B: Create a 'Virtual Machine'

<br>

## 7. ) Now, for this second part we will create a 'Virtual Machine' inside the resource group we just created.

- So type into the searh bar 'Virtual Machine' and select it to continue.

<img width="1511" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/f81d1869-9805-40b1-b4b9-76aa85c0f751"><br>

***

<br>

## 8. ) Click one of the 'Create' buttons to start creating your Virtual Machine

<img width="1509" alt="3C89D03C-0D84-4484-BFD6-79D2FBDF9012" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/d2a8f586-58ac-4bea-99e8-919410d8d839"><br>

 >**Note: This is called your 'Virtual Machine Default Directory'**

***

<br>

## 9. ) Now we can put in key information for our Virtual Machine

- Select your subscription

- Resource Group Name: RG-osTicket (the one you created)

- Virtual Machine Name: vm-osticket (all lowercase)

- Region: (US) West 3 

- Availability Options: No infrastructure redundancy required

- Security Type: Standard

- Image: Windows 10 Pro, version 22H2 - ×64 Gen2

- Leave the 'VM Architecture' & 'Run with Azure Sport Discount' parts toward the bottom alone.

- *Scroll Down once completed*

<img width="1511" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/0f114991-5378-4dfa-ac2d-cbded1d74006"><br>

***

<br>

## 10. ) As before, we will fill in the following:

- Size: 

- Username: 

- Password:

- Public Inbound Ports:

- Select Inbound Ports: 

- *Check the Box*

- Go ahead and click 'Review and Create'

 >**h**

<img width="1511" alt="isolated" src="https://github.com/vincentchachere/osticket-prereqs/assets/161680745/d25401ce-e384-4511-a592-9747b8bc9be9"><br>

***

<br>

## 11. ) 

- 

- 

- 

 >**h**

<img width="1511" alt="isolated" src="

***

<br>
