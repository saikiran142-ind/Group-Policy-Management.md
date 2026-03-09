# Group-Policy-Management.md

## 🛡️ Group Policy SOP: How to Block USB Storage Devices

In an enterprise environment, blocking USB ports is a critical security measure to prevent unauthorized data transfer and malware infections. This guide explains how to enforce this via Group Policy (GPO).

---

### 🛠️ Step 1: Accessing Group Policy Management
1. Press `Win + R`, type **`gpmc.msc`**, and hit **Enter**.
2. Expand your Forest and then your **Domain** (e.g., `company.local`).

### 🛠️ Step 2: Creating a New GPO
1. Right-click on the **Group Policy Objects** folder.
2. Select **New** and name it **`Block_USB_Policy`**.
3. Click **OK**.

### 🛠️ Step 3: Editing the Policy Settings
1. Right-click the newly created `Block_USB_Policy` and select **Edit**.
2. Navigate to the following path:
   `Computer Configuration` > `Policies` > `Administrative Templates` > `System` > `Removable Storage Access`.
3. In the right pane, locate **"All Removable Storage classes: Deny all access"**.
4. Double-click it, select **Enabled**, then click **Apply** and **OK**.

### 🛠️ Step 4: Linking the GPO to the Domain/OU
1. Go back to the main **Group Policy Management** window.
2. Right-click on your **Domain** or a specific **OU** (Organizational Unit).
3. Select **"Link an Existing GPO..."**.
4. Select **`Block_USB_Policy`** from the list and click **OK**.

### 🛠️ Step 5: Enforcing the Policy on Client PCs
To apply the changes immediately on a user's computer without waiting for the background refresh:
1. Open **Command Prompt (CMD)** as Administrator.
2. Run the command:  
   `gpupdate /force`

---

### 🔍 Verification (How to check if applied):
- Insert a USB drive into the client PC; Windows should show an **"Access Denied"** message or the drive will not appear in File Explorer.
- Run `gpresult /r` in CMD to see if the `Block_USB_Policy` is listed under "Applied Group Policy Objects".

---
