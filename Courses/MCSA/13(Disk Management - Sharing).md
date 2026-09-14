# Windows Server NTFS (Security) Permissions Guide

---

## 📂 Core Concept: NTFS Permissions vs. Sharing Permissions
While **Sharing Permissions** only control access when users connect over the network, **NTFS Permissions** (configured via the **Security** tab) apply restrictions locally on the server AND across the network. 

* **The Finer Filter:** NTFS permissions act as a secondary, strict filter. Windows calculates the final access level based on the **most restrictive (Effective) permission** between Sharing and NTFS.
* **How to Configure:** Right-click the folder ➡️ Select **Properties** ➡️ Go to the **Security** tab.

---

## 🔑 Types of NTFS Permissions
NTFS provides highly customizable access control entries, with the standard options including:

### 1. Read & Execute
* **Capabilities:** Allows users to view folder contents, open files, and execute applications or scripts within the directory.

### 2. List Folder Contents
* **Capabilities:** Specifically allows users to see the names of files and subfolders within the directory, even if they don't have explicit permission to read the files' data.

### 3. Write
* **Capabilities:** Allows users to create new files and subfolders inside the directory and write data to them.

### 4. Modify
* **Capabilities:** A powerful, standard permission. It encompasses all **Read**, **Write**, and **Execute** privileges, and crucially allows users to **Modify** existing data and **Delete files/folders**.

### 5. Full Control
* **Capabilities:** Grants absolute control over the folder, including the critical ability to change permission ownership and alter the Access Control List (ACL) rules for other users.

---

## 🛡️ Critical NTFS Security Mechanisms

### 🌲 1. Permission Inheritance (Inheritance)
By default, any subfolder or file created inside a parent folder automatically inherits the permissions assigned to the parent.
* **The Practice:** If a folder has inherited permissions that you want to remove, you must first **Disable Inheritance** under the `Advanced Security Settings`. 
* **Options when disabling:** 
  1. *Convert inherited permissions into explicit permissions* (keeps existing rules but allows editing).
  2. *Remove all inherited permissions* (clears the list to start fresh).

### ⛔ 2. Explicit Deny (Deny Rule)
In Windows Server, an explicit **Deny** always overrides an **Allow** permission.
* **Example:** If a user belongs to a group that is *Allowed* to Modify a folder, but that specific user is explicitly *Denied* Write access, they will be blocked completely. 
* **Best Practice:** Use "Deny" sparingly, as it can make auditing permissions complex.

---

## 👥 Advanced Best Practices: Combining Sharing and NTFS
To achieve robust data defense, network administrators combine both layers:
1. **At the Sharing Layer:** Give a broader permission to the security group (e.g., set the Sharing permission to **Change** for the department group).
2. **At the NTFS (Security) Layer:** Filter down access precisely (e.g., set the NTFS permission to **Read** for interns and **Modify** for managers).
3. **The Result:** The system applies the **Most Restrictive** overlap, ensuring total security compliance across the network.

