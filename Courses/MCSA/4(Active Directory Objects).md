إليك ملخصاً احترافياً وشاملاً لمحتوى الفيديو باللغة الإنجليزية، ليوضح كيفية إدارة الكائنات (Objects) الأساسية داخل الدليل النشط، متناسقاً تماماً مع سياق وتنسيق ملاحظاتك التقنية السابقة:
## 🗂️ Active Directory Objects Management (ADUC)
To manage network resources centrally, Windows Server utilizes the Active Directory Users and Computers (ADUC) console ([0:23](https://www.youtube.com/watch?v=QvMkATl2yho&t=23s)). This console is accessed via Server Manager ➔ Tools ➔ Active Directory Users and Computers ([0:42](https://www.youtube.com/watch?v=QvMkATl2yho&t=42s)). It handles the fundamental structural objects of your domain environment ([0:23](https://www.youtube.com/watch?v=QvMkATl2yho&t=23s)).
------------------------------
## 1️⃣ Organizational Units (OUs)
An Organizational Unit (OU) acts like a logical folder used to group and organize active directory objects (Users, Groups, Computers) based on company departments (e.g., HR, Finance, Sales, IT) ([1:30](https://www.youtube.com/watch?v=QvMkATl2yho&t=90s)).

* Why use OUs?
* Organization: Simplifies the structure of your network infrastructure ([2:26](https://www.youtube.com/watch?v=QvMkATl2yho&t=146s)).
   * Group Policy Application: Allows network administrators to link specific Group Policies (GPOs) directly to a department (e.g., blocking USB access exclusively for the HR department) ([2:33](https://www.youtube.com/watch?v=QvMkATl2yho&t=153s)).
* Best Practice: Create separate sub-OUs under main departments to segregate users from machines (e.g., creating IT-Users and IT-Computers under an IT parent OU) ([3:23](https://www.youtube.com/watch?v=QvMkATl2yho&t=203s)).

------------------------------
## 2️⃣ User Accounts
Creating a user account provides domain credentials for employees to authenticate and log in to network workstations ([3:57](https://www.youtube.com/watch?v=QvMkATl2yho&t=237s)).

* Creation Steps: Right-click the target OU ➔ New ➔ User ([3:57](https://www.youtube.com/watch?v=QvMkATl2yho&t=237s)).
* Naming Conventions: Use standard formats to prevent duplications, such as Firstname.Lastname (e.g., mohamed.zohdy) ([4:36](https://www.youtube.com/watch?v=QvMkATl2yho&t=276s)).
* Password Policies & Controls:
* User must change password at next logon: Forces the user to update their initial complex setup password during their first sign-in ([5:25](https://www.youtube.com/watch?v=QvMkATl2yho&t=325s)).
   * Password never expires: Overrides the default security policy which normally expires passwords every 42 days ([6:27](https://www.youtube.com/watch?v=QvMkATl2yho&t=387s)).
   * Account is disabled: Used as a security best practice instead of deleting an account if an employee leaves the company, keeping their historic data attributes intact ([6:49](https://www.youtube.com/watch?v=QvMkATl2yho&t=409s)).

------------------------------
## 3️⃣ Security Groups
Groups are objects used to compile multiple user accounts together to assign common network permissions or policies at once instead of doing it individually ([8:04](https://www.youtube.com/watch?v=QvMkATl2yho&t=484s)).

* Creation Steps: Right-click the OU ➔ New ➔ Group (e.g., HR-Group) ([8:04](https://www.youtube.com/watch?v=QvMkATl2yho&t=484s)).
* Adding Members: Highlight multiple user accounts ➔ Right-click ➔ Add to a group ➔ Search for the target group name ([8:22](https://www.youtube.com/watch?v=QvMkATl2yho&t=502s)).
* Default Status: Every newly created domain user is automatically assigned as a member of the built-in Domain Users group ([9:05](https://www.youtube.com/watch?v=QvMkATl2yho&t=545s)).
* Copying Efficiency (Templates): If you right-click an existing group member and select Copy to create a new employee account, the new account automatically inherits all group memberships from the original user ([9:23](https://www.youtube.com/watch?v=QvMkATl2yho&t=563s)).

------------------------------
## 4️⃣ Computer Accounts

* Workstations: Represents any local physical or virtual system that has joined the domain network environment ([11:06](https://www.youtube.com/watch?v=QvMkATl2yho&t=666s)).
* Default Directory: When any client machine joins the domain, its computer object is automatically generated and nested inside the default Computers container folder unless specified otherwise ([11:22](https://www.youtube.com/watch?v=QvMkATl2yho&t=682s)).
* Domain Controllers (DCs): Primary servers running Active Directory roles are stored separately inside a dedicated system folder named Domain Controllers ([11:06](https://www.youtube.com/watch?v=QvMkATl2yho&t=666s)).

------------------------------
هل ترغب في الانتقال إلى موضوع ربط الأجهزة بالدومين (How to Join a Machine to a Domain) بناءً على ما نوه إليه المحاضر للمرة القادمة ([11:37](https://www.youtube.com/watch?v=QvMkATl2yho&t=697s))؟

