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



