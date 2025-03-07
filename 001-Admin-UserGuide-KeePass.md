# **End-to-End Setup Guide for KeePass with OneDrive (Administrator)**  

This guide provides a **detailed step-by-step** process for setting up **KeePass with OneDrive** as an Administrator. The goal is to **securely store and share** the KeePass database (`.kdbx`) with employees while maintaining **strict access controls**.

---

## **🔹 Step 1: Install Required Software**  

### **1. Install KeePass Password Safe (KeePass 2.x)**  
KeePass is an open-source password manager that stores credentials in an encrypted database.  

#### **Steps to Install KeePass:**
1. **Download KeePass 2.x (Professional Edition)**  
   - 🔗 [KeePass Official Download Link](https://keepass.info/download.html)  
2. Choose the **Installer (.exe) version** and download it.  
3. Double-click the downloaded file to start installation.  
4. Click **Next → Agree to License → Next → Install**.  
5. Click **Finish** to complete the installation.  

---

### **2. Install OneDrive for Desktop**  
OneDrive syncs files securely across multiple devices.  

#### **Steps to Install OneDrive:**
1. **Download OneDrive for Windows:**  
   - 🔗 [OneDrive Official Download Link](https://www.microsoft.com/en-us/microsoft-365/onedrive/download)  
2. Run the **OneDriveSetup.exe** file.  
3. Sign in using your **Microsoft account (company email recommended)**.  
4. OneDrive will create a folder on your PC at:  
   ```plaintext
   C:\Users\Admin\OneDrive\
   ```
5. Verify that OneDrive is **successfully syncing files**.

---

## **🔹 Step 2: Create a Secure KeePass Database**  

Now, we will create a **new KeePass database** (`.kdbx`) to store credentials securely.

### **1. Create a New KeePass Database**
1. **Open KeePass**.  
2. Click **"File" → "New"**.  
3. Select a **location to save the database** (**temporarily store it on your PC** before moving it to OneDrive).  
4. Name the database **Company_Credentials.kdbx**.  
5. Click **Save**.  

### **2. Set a Strong Master Password**  
1. KeePass will prompt you to create a **Master Password**.  
2. Use a **long and complex password** (e.g., at least 16 characters with numbers, symbols, and uppercase/lowercase letters).  
3. Write down the Master Password and **store it securely** (do not share it via email or text).  
4. Click **OK**.  

### **3. (Optional) Use a Key File for Extra Security**  
1. Click **"Create Key File"** in the KeePass setup window.  
2. Save the key file in a **separate location** (USB drive, another folder, or a different cloud storage).  
3. You will need **both the Master Password & Key File** to open KeePass.  

---

## **🔹 Step 3: Move KeePass Database to OneDrive**  

To enable **secure access** for employees, move the KeePass database to OneDrive.

### **1. Create a Secure Folder in OneDrive**
1. Open **OneDrive Folder** on your PC:  
   ```plaintext
   C:\Users\Admin\OneDrive\
   ```
2. Create a new folder:  
   - Right-click → **New → Folder**  
   - Name it **SecureFolder**  

### **2. Move the KeePass Database to OneDrive**
1. Locate your KeePass database (`Company_Credentials.kdbx`) from the temporary location.  
2. Move it to OneDrive Secure Folder:  
   ```plaintext
   C:\Users\Admin\OneDrive\SecureFolder\Company_Credentials.kdbx
   ```
3. **Wait for OneDrive to sync the file** (check for a green checkmark on the file).  

---

## **🔹 Step 4: Configure Secure Sharing for Users**  

Now, we will grant access to employees with **controlled permissions**.

### **1. Share KeePass Database with Employees**
1. **Go to OneDrive Online**:  
   - 🔗 [OneDrive Web Access](https://onedrive.live.com/)  
2. Navigate to **SecureFolder** → **Right-click `Company_Credentials.kdbx`**.  
3. Click **"Share"**.  
4. **Enter employee email addresses** (use work emails only).  
5. **Set Permissions Properly:**  
   - **Viewer (Read-Only)** – Users can view passwords but cannot modify them.  
   - **Editor (Full Access)** – Only for IT/Admins managing passwords.  
6. Click **"Send"** to share access.  

### **2. Enforce Security Settings**
- ✅ **Disable "Anyone with the link can edit"**  
- ✅ **Require sign-in with a Microsoft account**  

---

## **🔹 Step 5: Enable OneDrive Security & Backup**  

### **1. Enable Ransomware Protection**
1. Open **OneDrive Settings** → **Security**.  
2. Enable **"Ransomware Protection"** to prevent unauthorized modifications.  

### **2. Enable File Version History**
1. **Right-click `Company_Credentials.kdbx`** in OneDrive.  
2. Click **"Version history"**.  
3. Ensure **file versioning is enabled** (helps restore previous versions if needed).  

### **3. Automate Daily Backups**
Use **PowerShell** to create automatic daily backups:

```powershell
$source = "C:\Users\Admin\OneDrive\SecureFolder\Company_Credentials.kdbx"
$destination = "C:\Backup\KeePass_Backup_$(Get-Date -Format yyyyMMdd).kdbx"
Copy-Item -Path $source -Destination $destination -Force
```

- Schedule this **PowerShell script** to run **daily** using **Windows Task Scheduler**.  

---

## **🔹 Step 6: Guide Users to Access KeePass Securely**  

Employees must **properly access the KeePass database**.

### **1. Install KeePass & OneDrive on Employee Computers**
1. Employees **install KeePass 2.x** ([Download Here](https://keepass.info/download.html)).  
2. Ensure **OneDrive Sync is Enabled** on their PCs.  

### **2. Open KeePass Database from OneDrive**
1. Open **KeePass 2.x**.  
2. Click **"File" → "Open"**.  
3. Navigate to:  
   ```plaintext
   C:\Users\Employee\OneDrive\SecureFolder\Company_Credentials.kdbx
   ```
4. Select the **database file** and enter the **Master Password**.  
5. ✅ **Now, they can access credentials securely!**  

### **3. Enforce Read-Only Mode for Users**
- Employees should open KeePass in **Read-Only Mode** to prevent accidental edits.  
  - Open KeePass → **File → Open in Read-Only Mode**.  

---

## **🔹 Step 7: Train Employees & Enforce Policies**  

### **1. Conduct a Security Awareness Session**
- ✅ **Never share the Master Password**.  
- ✅ **Avoid downloading the KeePass database to personal devices**.  
- ✅ **Use Auto-Type (`Ctrl + V`) instead of manually copying passwords**.  

### **2. Enable Multi-Factor Authentication (MFA)**
- Ensure all employees **enable 2FA for OneDrive & Microsoft accounts**.  

---

## **📌 Final Thoughts**
By following this **detailed end-to-end setup**, you can ensure:  
✅ **Secure password management**  
✅ **Controlled employee access**  
✅ **Regular backups & data protection**  

🚀 **Your KeePass database is now safely managed with OneDrive!**
