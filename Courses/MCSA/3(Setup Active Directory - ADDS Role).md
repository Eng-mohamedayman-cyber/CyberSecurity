## 🌐 Promoting Windows Server to a Domain Controller (Active Directory Setup)
By default, a newly installed Windows Server operates as a normal standalone machine. To transform it into a Domain Controller (DC) so you can centrally manage and control your network, you must install and configure the Active Directory role.
------------------------------
## 1️⃣ Step 1: Installing the AD-DS Role

* Navigation: Open Server Manager, then click on Manage ➔ Add Roles and Features.
* Installation Type: Choose Role-based or feature-based installation and select your server.
* Role Selection: Check the box for Active Directory Domain Services (AD DS).
* Features: A pop-up window will appear asking to include mandatory management features (e.g., Group Policy Management Console); click Add Features.
* Execution: Proceed to the end and click Install (this role does not require an immediate system restart).

------------------------------
## 2️⃣ Step 2: Configuring the Domain Controller (Promotion)
Once the role installation finishes, a notification banner (a yellow warning triangle) will appear at the top of Server Manager. Click on it and select "Promote this server to a domain controller".
## 🔹 Deployment Configuration

* Deployment Operation: Select Add a new forest (since this is the very first domain in your network architecture).
* Root Domain Name: Enter an internal naming convention, usually formatted as yourcompany.local (e.g., test.local).

## 🔹 Domain Controller Options

* Functional Levels: Define the Forest & Domain Functional Levels. This sets the minimum Windows Server OS version allowed for any future DCs inside this network environment.
* Capabilities: DNS Server and Global Catalog (GC) options are checked by default for the first domain tree.
* DSRM Password: Set a complex Directory Services Restore Mode (DSRM) password, which is critical for restoring Active Directory backups later.

## 🔹 Additional Options & Paths

* NetBIOS Name: The system auto-generates this prefix (e.g., TEST from test.local) to simplify user log-ons.
### Database Paths: Active Directory relies on two essential data repositories:
* NTDS: Contains the primary database file (ntds.dit) storing network object accounts.
* SYSVOL: Stores system group policies, scripts, and replication configurations.

------------------------------
## 3️⃣ Step 3: Prerequisites Check & Verification

* The wizard automatically performs a Prerequisite Check to ensure proper network prerequisites are met (such as verifying a statically configured IP address).
* If all validation checks pass successfully, click Install.
* The server will automatically restart to apply changes.

------------------------------
## 🔐 Post-Promotion Sign-In
After rebooting, the local administrator account scales up into a domain administrative credential. You will log in using the domain syntax format: NETBIOS\Administrator (e.g., TEST\Administrator).
You will notice new management snap-ins added under Server Manager ➔ Tools, primarily Active Directory Users and Computers, which is used to manage organizational units, user accounts, and machines.
------------
