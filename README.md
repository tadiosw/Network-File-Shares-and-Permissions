
---

# Network File Shares and Permissions  
<p align="center">  
<img src="https://i.imgur.com/AeiqMDZ.png" alt="Traffic Examination"/>  
</p>  

This tutorial provides an overview of setting up shared network files and configuring permissions on Windows 10.  

## Environments and Technologies Used  

- Microsoft Azure (Virtual Machines/Domain Controller/Client Machine)  
- Remote Desktop  
- Shared Network Files  

## Operating Systems Used  

- Windows 10 (21H2)  

---

### Setting Up Shared Network Files & Permissions  

In this lab, we will create shared network folders and configure access permissions. These folders will be set up on the **DC-1** virtual machine, and only specific users will have access based on the assigned permissions.  

#### **Step 1: Create Shared Folders**  
1. On the **DC-1** machine, navigate to the **C:/ drive**.  
2. Create the following four folders:  
   - **read-access**  
   - **read/write-access**  
   - **no-access**  
   - **accounting**  

<p>  
<img src="https://i.imgur.com/k70dozS.png" height="80%" width="80%" alt="Creating Folders"/>  
</p>  

#### **Step 2: Configure Folder Permissions**  
Once the folders are created, we need to share them on the network so that **Client-1** can access them. Assign the following permissions:  

- **read-access** → Set to **read-only** for domain users.  
- **read/write-access** → Allow **read and write** access for domain users.  
- **no-access** → Grant **read and write** permissions to **domain admins only**.  

<p>  
<img src="https://i.imgur.com/wcpB5Ex.png" height="80%" width="80%" alt="Setting Permissions"/>  
</p>  
<p>  
<img src="https://i.imgur.com/hku11Pt.png" height="80%" width="80%" alt="Folder Properties"/>  
</p>  

#### **Step 3: Test Access from Client-1**  
1. Log into the **Client-1** machine using a standard user account.  
2. Attempt to access the shared folders.  
3. Verify that the assigned permissions work as expected.  

<p>  
<img src="https://i.imgur.com/CGQ8yaO.png" height="80%" width="80%" alt="Testing Access"/>  
</p>  
<p>  
<img src="https://i.imgur.com/f9TldBO.png" height="80%" width="80%" alt="Access Permissions Check"/>  
</p>  

#### **Step 4: Create a Security Group for Restricted Access**  
1. On the **DC-1** machine, open **Active Directory Users and Computers (ADUC)**.  
2. Create a new security group called **"Accountants"**.  
3. Assign specific users to this group.  
4. Configure the **"accounting"** folder to allow access only to members of the **Accountants** group.  

<p>  
<img src="https://i.imgur.com/QADy92Z.png" height="80%" width="80%" alt="Creating Security Group"/>  
</p>  
<p>  
<img src="https://i.imgur.com/BUm3L2Q.png" height="80%" width="80%" alt="Setting Folder Permissions"/>  
</p>  
<p>  
<img src="https://i.imgur.com/fH8fU7b.png" height="80%" width="80%" alt="Verifying Group Access"/>  
</p>  

Now, only users who are part of the **Accountants** security group can access the **"accounting"** folder. If a standard user requires access, they must be added to this group.  

This concludes the tutorial on setting up shared network files and permissions. 🎯
