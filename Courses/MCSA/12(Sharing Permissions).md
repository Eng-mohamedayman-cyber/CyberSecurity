# Windows Server Sharing Permissions Guide

---

## 📂 Core Concept: Folder Sharing
When a server hosts a specific folder (e.g., named `Data`), network users cannot access or browse it until **Folder Sharing** is explicitly enabled across the network.

* **Share Name:** When sharing a folder, you can keep its original name or assign a different alias that appears to network users (e.g., the folder is named `Data` on the server but appears as `HR_Data` to network clients).
* **How to Enable:** Right-click the folder ➡️ Select **Properties** ➡️ Go to the **Sharing** tab ➡️ Click **Advanced Sharing**.

---

## ⚠️ The Ultimate Warning: The Danger of "Everyone"
By default, Windows configures sharing permissions to grant **Read** access to the **Everyone** group.

* **The Risk:** This means any user on the corporate network—or anyone who gains unauthorized access to it—can view and copy your files. 
* **The Correct Action:** You must **Remove** the `Everyone` group immediately and manually specify the exact users or groups allowed to access the data. A lack of awareness regarding this default setting has historically led to critical data leaks and employee terminations.

---

## 🔑 Types of Sharing Permissions
Sharing permissions are categorized into three primary levels:

### 1. Read
* **What it allows:** Users can open files, read their contents, and copy (Copy/Paste) them to their local machines.
* **What it restricts:** Users are strictly blocked from modifying the original file on the server, deleting files, or creating new files and folders.

### 2. Change
* **What it allows:** Includes all **Read** privileges, plus the ability to create new files/folders, modify and save changes (Write/Edit), and **Delete files**.
* **Crucial Note:** Sharing permissions do not provide a standalone "Prevent Deletion" toggle. If you need to allow file modification while preventing deletion, you must configure **Security Permissions (NTFS)** later. NTFS permissions act as a finer filter to precisely slice and dice user access.

### 3. Full Control
* **What it allows:** Includes all privileges from both **Read** and **Change**, plus one highly critical capability: modifying the Access Control List (ACL).
* **The Risk:** Users can **change the folder's permissions entirely**. This allows them to remove the System Administrator or add unauthorized users and grant them access.
* **Recommendation:** Never grant **Full Control** except in absolute necessity and only to highly trusted administrators.

---

## 👥 Best Practice: Role-Based Access Control (RBAC)
* **The Wrong Approach:** Assigning permissions to users individually (User-by-User). This is highly inefficient, difficult to audit, and prone to human error.
* **The Right Approach (RBAC):** Create security groups based on roles or departments (e.g., `HR_Group`) and assign the sharing permissions to the group itself. When a new employee joins, simply add them to the group; they will automatically inherit all necessary permissions without manual reconfiguration.

