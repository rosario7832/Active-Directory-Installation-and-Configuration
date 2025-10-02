# Active-Directory-Installation-and-Configuration

## Network Configuration

1. Click on the **network icon** in the taskbar and select:  
   **Change adapter options**.

2. Check both network adapters to identify:  
   - **Internet-connected network**: if the IP address is in the range `10.0.2.x`.  
   - **Internal network**: if the IP address is `169.254.196.79`.  

3. For the internal network, manually set the IP address:  
IP Address: 172.16.0.1
Subnet Mask: 255.255.255.0
Default Gateway: (leave blank)
DNS: 127.0.0.1

4. It is recommended to **rename both network connections** for easier administration:  
- Internet-connected network → **Internet**  
- Internal network → **Internal**

## Rename the PC

1. Right-click on **Start** → **System** → **Rename this PC**.  
2. Enter a descriptive name, for example:  
DomainController or DC
3. Restart the virtual machine for the changes to take effect.

# Active Directory Configuration on Windows Server

## 1. Open Server Manager
- In the **Dashboard**, click on **Add roles and features**.

## 2. Installation Wizard
- Click **Next** until you reach the **Server Roles** section.  
- Select **Active Directory Domain Services (AD DS)**.
  
<img src="https://i.imgur.com/mjz1whS.png" height="55%" width="60%"/> 

- Accept any additional features if prompted, then click **Next**.

## 3. Confirmation and Installation
- Review the configuration.  
- Click **Install**.  
- The process may take several minutes.

## 4. Promote the Server to Domain Controller
- Once the installation is complete, a notification will appear in **Server Manager**.  
- Click on **Promote this server to a domain controller**.

<img src="https://i.imgur.com/VQp31S0.png" height="55%" width="60%"/> 

- Choose one of the options:  
  - **Add a new forest** (if this is the first installation).  
  - **Add a domain to an existing forest** (if a domain already exists).  
- Define the **domain name** (e.g., `mydomain.com`).
- **Set the Directory Services Restore Mode (DSRM) password**. This password is required for restoring Active Directory in recovery mode.  

## 5. Finalize and Restart
- Complete the wizard steps.  
- The server will automatically restart to apply the changes.

# Creating a New Administrator User in Active Directory

## 1. Initial Login
- After restarting Windows, a new user called **MYDOMAIN/Administrator** will be created.  
- Log in with this user.
<img src="https://i.imgur.com/cFNvnol.png" height="55%" width="60%"/>

## 2. Create a New Administrator Account
1. Go to: **Start > Windows Administrative Tools > Active Directory Users and Computers**.  
2. Within Active Directory, create a **Organizational Unit (OU)**:  
   - Right-click on **mydomain.com** and select **New > Organizational Unit**.  
   - Name the new OU **_ADMINS**.
<img src="https://i.imgur.com/yhcc2OC.png" height="45%" width="60%"/>
## 3. Create a New User
1. Right-click on the **_ADMINS** folder > **New > User**.  
<img src="https://i.imgur.com/TCjKENg.png" height="45%" width="50%"/>
2. Fill in the required information and assign a password.  
<div style="display: flex; gap: 10px; align-items: center;">
  <img src="https://i.imgur.com/oha74hS.png" height="300px"/>
  <img src="https://i.imgur.com/8QO56wQ.png" height="300px"/>
</div>

3. The user will appear in the right-hand panel, but it does not yet have administrator privileges.

## 4. Make the User an Administrator
1. Right-click on the new user and select **Properties**.  
2. In the **Member Of** tab, add the user to the **_ADMINS** group.
<img src="https://i.imgur.com/5nGYnCU.png" height="55%" width="60%"/>

## 5. Log in with the New Administrator Account
1. Log out of the current session.  
2. Select **Other user**.  
3. Enter the credentials of the new administrator account.  

> You now have your own domain administrator account.



