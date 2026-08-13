# 🖥️ Local Users & Groups After Joining a Domain

When a workstation joins an Active Directory domain, it undergoes significant security changes regarding its internal Local Accounts and Global Domain Accounts. Understanding this behavior is essential for standard administration and security management.

---

## 1️⃣ Local Administrator vs. Domain Administrator

Before joining the domain, the machine relies strictly on its built-in database (SAM file) for authentication. Once it transitions to the domain, a vital permission shift occurs:

* **The Privilege Injection**: Active Directory automatically adds the Domain Admins group of your domain into the workstation's local Administrators group.
* **The Result**: Any user account that is a member of the Domain Admins group automatically gains full local administrative control over that workstation (e.g., changing system settings or troubleshooting hardware) without needing to know the machine's local password.

---

## 2️⃣ Managing Local Users & Groups Post-Join

Administrators often need to view or manage these hidden local credentials.

* **Accessing the Console**: On the client machine, open the Run dialog (Win + R), type `lusrmgr.msc`, and press Enter. This brings up the Local Users and Groups management snap-in.
* **Security Risk (The Local Admin Trap)**: If users are left with local administrator privileges on their devices, they can technically bypass security rules, install unauthorized software, or uninstall monitoring tools.
* **Best Practice**: Keep standard users as part of the local Users group instead of the Administrators group. This locks down the operating system and prevents unauthorized configuration changes.

---

## 3️⃣ Restricting Domain Users via Group Policies (GPO)

To enforce strict workspace compliance across all company computers, network engineers do not modify local options manually on every PC. They apply configurations globally via Group Policies (GPOs) from the Domain Controller:

* **Locking Device Parameters**: Administrators use GPOs to completely hide or disable properties menus (Properties) so users cannot change network adapters or device drivers.
* **Mass Storage Restrictions**: GPOs are utilized to block physical USB ports across the entire organization to prevent data leaks or virus spreads, applying this restriction evenly even if the user attempts to act as a local administrator.

---

## 4️⃣ Administrative Workarounds & Emergency Access

If an IT support engineer needs to work on a machine during a network disconnection or Active Directory outage, they can still authenticate locally:

* **Using LAPS**: In modern production environments, it is recommended to implement LAPS (Local Administrator Password Solution). LAPS automatically randomizes, rotates, and stores unique local administrator passwords for every domain machine safely inside Active Directory.
* **Sign-in Format**: To bypass domain authentication and force the device to log into its internal local database, the technician types the login format: `.\Administrator` or `[ComputerName]\Administrator`.
