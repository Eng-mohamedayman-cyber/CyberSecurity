# Enterprise Windows Server & Group Policy (GPO) Implementation Lab

This repository contains the documentation, configuration details, and scripts for a comprehensive **Windows Server** administration lab. The project demonstrates practical skills in **Active Directory Domain Services (AD DS)**, Network Infrastructure, Security Compliance, and **Group Policy Management** within an enterprise environment.

## 🚀 Project Overview
The objective of this lab is to build a secure, centralized domain environment for a fictional company, implementing strict access controls, security policies, and automated desktop environments tailored to different organizational departments (**HR, Sales, IT**).

## 🛠️ Infrastructure & Network Configuration
* **Domain Name:** `mohamed.local`
* **Domain Controller (DC) Name:** `DC`
* **Static IP Address:** `192.168.1.2`
* **Client Machine:** `PC-01` (IP: `192.168.1.23` joined to `mohamed.local`)

## 📂 Active Directory Directory Service (AD DS) Structure
Implemented a structured Organizational Unit (OU) hierarchy to manage users and resources effectively:
* **OUs Created:** `HR`, `Sales`, `IT`
* **User & Group Management:** 
  * Created sample user accounts within their respective department OUs.
  * Created dedicated security groups for each department (`HR-Group`, `Sales-Group`, `IT-Group`) and nested users accordingly.

## 🔒 Group Policy Objects (GPOs) Implemented

### 1. Security & Account Policies
* **Password Policy:** Enforced password change every 90 days, minimum password length of 4 digits (no complexity required), and history tracking to remember the last 2 passwords.
* **Account Lockout Policy:** Account locks out for 60 minutes after 5 consecutive failed login attempts.
* **Windows Firewall:** Configured an inbound rule via GPO to allow **ICMP (Ping) traffic** across all domain computers for network troubleshooting.

### 2. Desktop Environment & Restrictive Policies
* **Desktop Standardization:** Forced a corporate fixed background wallpaper for all domain users.
* **Control Panel Restrictions:** Removed "Programs and Features" from the Control Panel specifically for the `HR` OU.
* **System Hardening:**
  * Removed "Properties" from the *This PC* context menu.
  * Disabled **Command Line (cmd)** and **Run prompt** for `HR` and `Sales` users.
* **Task Manager Access:** Blocked Task Manager for all domain users using an enforced policy, with an explicit exclusion for the `IT team`.

### 3. Peripheral Control & Exclusions
* **Removable Storage Policy:** Disabled all external storage access (USB drives) for `HR` and `Sales` users.
* **Security Exception:** Created an exclusion rule to allow the `HR Manager` to use external storage for business continuity.

### 4. Preferences & Client Deployment
* **Web Shortcuts:** Deployed an internet shortcut URL on all HR users' desktops pointing to `http://hrapp.mohamed.local` with a custom icon.
* **Local Admin Management:** Utilized GPO Preferences to create a local administrator account named `itadmin` on all domain computers and added the `IT-Group` to the local Administrators group.

## 📸 Verification & Screenshots

* Active Directory OU Hierarchy: `![AD Structure](images/ad-structure.png)`
* Group Policy Management Console: `![GPMC](images/gpmc.png)`
* Client Verification (PC-01): `![Client Verification](images/client-pc.png)`
