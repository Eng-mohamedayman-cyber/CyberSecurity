إليك ملخصاً احترافياً وشاملاً لمحتوى الفيديو باللغة الإنجليزية المتناسقة تماماً مع أسلوب ملاحظاتك التقنية، ليوضح كيفية إعداد خدمة الدليل النشط وتحويل السيرفر العادي إلى متحكم نطاق:
## 🌐 Promoting Windows Server to a Domain Controller (Active Directory Setup)
By default, a newly installed Windows Server operates as a normal standalone machine ([0:38](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=38s)). To transform it into a Domain Controller (DC) so you can centrally manage and control your network, you must install and configure the Active Directory role ([0:25](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=25s)).
------------------------------
## 1️⃣ Step 1: Installing the AD-DS Role

* Navigation: Open Server Manager, then click on Manage ➔ Add Roles and Features ([2:26](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=146s)).
* Installation Type: Choose Role-based or feature-based installation and select your server ([2:42](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=162s)).
* Role Selection: Check the box for Active Directory Domain Services (AD DS) ([3:03](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=183s)).
* Features: A pop-up window will appear asking to include mandatory management features (e.g., Group Policy Management Console); click Add Features ([3:03](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=183s)).
* Execution: Proceed to the end and click Install (this role does not require an immediate system restart) ([3:55](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=235s)).

------------------------------
## 2️⃣ Step 2: Configuring the Domain Controller (Promotion)
Once the role installation finishes, a notification banner (a yellow warning triangle) will appear at the top of Server Manager ([4:17](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=257s)). Click on it and select "Promote this server to a domain controller" ([4:17](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=257s)).
## 🔹 Deployment Configuration

* Deployment Operation: Select Add a new forest (since this is the very first domain in your network architecture) ([5:32](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=332s)).
* Root Domain Name: Enter an internal naming convention, usually formatted as yourcompany.local (e.g., test.local) ([5:53](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=353s)).

## 🔹 Domain Controller Options

* Functional Levels: Define the Forest & Domain Functional Levels ([6:26](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=386s)). This sets the minimum Windows Server OS version allowed for any future DCs inside this network environment ([6:35](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=395s)).
* Capabilities: DNS Server and Global Catalog (GC) options are checked by default for the first domain tree ([7:37](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=457s)).
* DSRM Password: Set a complex Directory Services Restore Mode (DSRM) password, which is critical for restoring Active Directory backups later ([7:57](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=477s)).

## 🔹 Additional Options & Paths

* NetBIOS Name: The system auto-generates this prefix (e.g., TEST from test.local) to simplify user log-ons ([8:23](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=503s)).
* Database Paths: Active Directory relies on two essential data repositories ([8:58](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=538s)):
* NTDS: Contains the primary database file (ntds.dit) storing network object accounts ([9:12](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=552s)).
   * SYSVOL: Stores system group policies, scripts, and replication configurations ([9:23](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=563s)).

------------------------------
## 3️⃣ Step 3: Prerequisites Check & Verification

* The wizard automatically performs a Prerequisite Check to ensure proper network prerequisites are met (such as verifying a statically configured IP address) ([10:13](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=613s)).
* If all validation checks pass successfully, click Install ([10:26](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=626s)).
* The server will automatically restart to apply changes ([11:40](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=700s)).

------------------------------
## 🔐 Post-Promotion Sign-In
After rebooting, the local administrator account scales up into a domain administrative credential ([12:33](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=753s)). You will log in using the domain syntax format: NETBIOS\Administrator (e.g., TEST\Administrator) ([12:23](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=743s)).
You will notice new management snap-ins added under Server Manager ➔ Tools, primarily Active Directory Users and Computers, which is used to manage organizational units, user accounts, and machines ([12:57](https://www.youtube.com/watch?v=TcTqBwWu5O0&t=777s)).
------------------------------
هل ترغب في أن نلخص شرح استخدام أداة Active Directory Users and Computers لتجهيز الملاحظة القادمة، أم ننتقل إلى موضوع آخر؟

