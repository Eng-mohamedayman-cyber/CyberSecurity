## 🗂️ Active Directory Objects Management (ADUC)

To manage network resources centrally, Windows Server utilizes the Active Directory Users and Computers (ADUC) console. This console is accessed via Server Manager ➔ Tools ➔ Active Directory Users and Computers. It handles the fundamental structural objects of your domain environment.
------------------------------

## 1️⃣ Organizational Units (OUs)
An Organizational Unit (OU) acts like a logical folder used to group and organize active directory objects (Users, Groups, Computers) based on company departments (e.g., HR, Finance, Sales, IT).

### Why use OUs?
* Organization: Simplifies the structure of your network infrastructure.
* Group Policy Application: Allows network administrators to link specific Group Policies (GPOs) directly to a department (e.g., blocking USB access exclusively for the HR department)
* Best Practice: Create separate sub-OUs under main departments to segregate users from machines (e.g., creating IT-Users and IT-Computers under an IT parent OU).
------------------------------

## 2️⃣ User Accounts
Creating a user account provides domain credentials for employees to authenticate and log in to network workstations.

* Creation Steps: Right-click the target OU ➔ New ➔ User.
* Naming Conventions: Use standard formats to prevent duplications, such as Firstname.Lastname (e.g., mohamed.zohdy).
* Password Policies & Controls:
* User must change password at next logon: Forces the user to update their initial complex setup password during their first sign-in.
* Password never expires: Overrides the default security policy which normally expires passwords every 42 days.
* Account is disabled: Used as a security best practice instead of deleting an account if an employee leaves the company, keeping their historic data attributes intact.
------------------------------

## 3️⃣ Security Groups
Groups are objects used to compile multiple user accounts together to assign common network permissions or policies at once instead of doing it individually.
* Creation Steps: Right-click the OU ➔ New ➔ Group (e.g., HR-Group).
* Adding Members: Highlight multiple user accounts ➔ Right-click ➔ Add to a group ➔ Search for the target group name.
* Default Status: Every newly created domain user is automatically assigned as a member of the built-in Domain Users group.
* Copying Efficiency (Templates): If you right-click an existing group member and select Copy to create a new employee account, the new account automatically inherits all group memberships from the original user.

------------------------------

## 4️⃣ Computer Accounts

* Workstations: Represents any local physical or virtual system that has joined the domain network environment.
* Default Directory: When any client machine joins the domain, its computer object is automatically generated and nested inside the default Computers container folder unless specified otherwise.
* Domain Controllers (DCs): Primary servers running Active Directory roles are stored separately inside a dedicated system folder named Domain Controllers.
------------------------------
