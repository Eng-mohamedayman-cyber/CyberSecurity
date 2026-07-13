## 🖥️ Joining a Client Machine to a Domain
When you add a computer to Active Directory, you transition its management style from a traditional Workgroup (managed locally) into a centralized Domain environment.
------------------------------

## 1️⃣ Network Requirements & Prerequisites
Before attempting to join a machine to the domain, you must verify three essential baseline settings on the client machine:

* Network Connectivity: The client machine (e.g., WIN10-PC) and the Domain Controller (DC) must be physically or virtually connected via the same network switch.
* IP Address Configuration: The client must be assigned a manual (static) IP address within the exact same subnet range as the server (e.g., Server: 192.168.1.2 / Client: 192.168.1.30).
* Critical DNS Setup: The client's Preferred DNS Server must point directly to the Domain Controller's IP address. Networks do not understand domain names (like test.local); they only understand IPs. The DNS server acts as the translator to locate the Active Directory authentication services.

------------------------------
## 2️⃣ What Happens Behind the Scenes? (The AAA Process)
When you type the domain name and click join, an authentication prompt asks for administrative credentials. Active Directory executes a security model known as AAA in the background:

* A - Authentication: The system uses the Kerberos protocol to check if the user account and password exist and match inside the Active Directory database.
* A - Authorization: The system checks if this user is allowed to join machines to the domain.
* Privilege Rule: A Domain Administrator can join an unlimited number of computers. However, any standard domain user is permitted to join a maximum of 10 computer accounts by default.
* A - Accounting (Object Checks): The Domain Controller verifies that the computer name is completely unique across the entire network. It ensures no duplicate computer, group, or user shares the exact same name.

------------------------------
## 3️⃣ Where Does the Computer Go in Active Directory?

* Default Container: Once the connection is approved, the new machine object automatically populates inside a default system folder named the Computers Container.
* Best Practice: The default "Computers" folder is a static container, meaning you cannot apply Group Policies (GPOs) to it. Administrators must manually move the computer object from this container into a custom Organizational Unit (OU) to manage its security policies.

------------------------------
## 4️⃣ Client Sign-In Methods (Post-Reboot)
After a successful join, the machine will prompt a restart. Users can now sign in using three distinct syntax formats depending on the target destination:

   1. FQDN Format (Full Name): username@domain.local (e.g., m.zohdy@test.local).
   2. NetBIOS Format (Legacy Standard): DOMAIN\username (e.g., TEST\m.zohdy).
   3. Local Machine Format: If an IT administrator needs to log back into the local computer account rather than the domain, they type: .\username (e.g., .\it-admin).


