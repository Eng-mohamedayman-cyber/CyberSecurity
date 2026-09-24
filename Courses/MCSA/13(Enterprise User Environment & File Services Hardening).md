# Enterprise User Environment & File Services Hardening (Windows Server 2019)

An advanced technical reference guide detailing the implementation of **Map Network Drives**, **File Server Resource Manager (FSRM)** policies, **Home Folders**, and **Roaming Profiles** in Windows Server 2019, based on the instructional series by Engineer Mohamed Zohdy.

---

## 🗺️ 1. Automated Storage Mapping: Map Network Drives
To streamline enterprise operations and secure workflows, end-users should not search for UNC network paths manually or use the Run prompt window (`Win + R`), which is typically locked out via Group Policy for security hardening. The optimal method is projecting an authenticated shared network path onto a local logical drive layout letter inside `This PC`.

### A. Client-Side Manual Configuration
* Users access `This PC` ➡️ click the **Map Network Drive** ribbon interface.
* Specify a vacant target **Drive Letter** (e.g., `S:` or `T:`) and type the strict UNC network path of the share: `\\PDC19\Data`.
* Check **Reconnect at sign-in** to force the host OS to automatically remount the shared network resource upon every authentication cycle.

### B. Automated Group Policy Mapping (Industry Best Practice)
To deploy volume maps across specific Organizational Units (OUs) seamlessly without manual host-by-host staging:
1. Launch the **Group Policy Management Console** and create a new GPO named `Map Network Drive Policy` linked to the target OU.
2. Edit the GPO and drill down to: `User Configuration` ➡️ `Preferences` ➡️ `Windows Settings` ➡️ **Drive Maps**.
3. Right-click the interface workspace ➡️ **New** ➡️ **Mapped Drive**.
4. Set the Action flag to **Update**, specify the target letter (e.g., `U:`), and input the explicit corporate UNC share location: `\\PDC19\Data`.
5. Trigger a network refresh on the endpoint workstation using `gpupdate /force` to immediately mount the volume map.

### C. Legacy Scripting Deployment (Logon Scripts)
Can be managed by deploying a custom lightweight command batch process attached to Active Directory user initializations:
* Construct a raw text document, populate it with the directory command block, and save it with an active extension format (**`.bat`**): `map_drive.bat`.
* **Syntax Block:**
  ```cmd
  @echo off
  net use V: \\PDC19\Data /persistent:yes
  ```
* Mount the file structure inside the GPO directory map: `User Configuration` ➡️ `Policies` ➡️ `Windows Settings` ➡️ `Scripts (Logon/Logoff)` ➡️ open **Logon** ➡️ browse and append the batch file resource.

---

## 📊 2. Granular Storage Governance: File Server Resource Manager (FSRM)
**FSRM** is a highly specialized **Role Service** running nested within the foundational `File and Storage Services` enterprise tree framework. Provisioned via Server Manager and orchestrated using administrative **Tools**, FSRM delivers fine-grain tracking, restriction matrices, and metadata visibility over data repositories.

### A. Folder-Level Micro Quotas
Unlike standard NTFS volume-wide quotas that generalize thresholds over entire partitions, FSRM enforces space limits **on specific target directories independently**.
* **Operational Quota Classes:**
  * **Hard Quota:** Restricts and explicitly drops any write commands or disk commits if a user or transaction breaches the designated folder threshold cap (e.g., locking operations at exactly 300 MB).
  * **Soft Quota:** Operates without throwing block warnings or halting write execution loops. It functions purely as an administrative logging mechanism for storage analytics and capacity threshold monitoring.
* **Automated Child Directory Provisioning (Auto-Apply Template):** Best practice dictates standing up a custom storage definition scheme within **Quota Templates** first. When mapping the quota path to an active directory tree, flag the rule as **"Auto-apply template and create quotas on existing and new subfolders"**. This ensures that while the main root folder is monitored, any new sub-directory spawned inside it by individual teams dynamically receives its own independent, isolated 300 MB micro-quota limit instantly.

### B. File Screening Policies
An essential data security tool designed to prevent non-business file dumping, maintain system optimization, and eliminate redundant multimedia data traffic flows inside internal routing frames.
* **Active Screening:** Evaluates files during active memory writes. If an endpoint attempts to drop or compile an unauthorized block, FSRM cancels the operation, throwing an explicit permission failure notification to the client machine.
* Built-in default blocking templates can be assigned to instantly exclude entire categories like **Audio and Video Files** (`.mp3`, `.mp4`) and system execution vectors (**Executable Files** like `.exe`).
* Custom extensions can be appended using explicit wildcard syntax expressions (e.g., inputting `*.pdf` within an isolated File Group definition block to completely deny PDF processing policies over a specified secure workspace).

### C. Advanced Storage Analytics Reporting
Generates comprehensive database intelligence matrices compiled natively into interactive, responsive layout sheets (**Dynamic HTML**).
* **Large Files Inventory:** Actively crawls target folder hierarchies to log data exceeding specific parameters (e.g., identifying objects larger than 10 MB). The resultant report details the absolute file path, exact file footprints, and tracks the initiating account profile identifier (e.g., `Mohamed Zohdy`). This allows administrators to audit and catch users attempting to bypass File Screening blocks by manually changing massive raw video container extensions into a plaintext file format (`.txt`).
* Additional diagnostic options include **Least Recently Accessed** tables to index stale, forgotten files for archival cleanup.

---

## 📂 3. Managed User Profiles: Home Folders & Roaming Profiles

### A. Isolated Home Folders
Provides every domain employee with a completely private, network-hosted drive workspace. In locked-down terminal environments where local physical flash memory devices are blocked via device installation policies, the Home Folder acts as a corporate replacement for personal scratchpad data tracking.
1. Establish a root volume directory structurally named `Home` on the file server.
2. Share the root directory as an administrative hidden asset by appending a dollar sign directly to the net string: **`Home$`**.
3. Grant **Full Control** sharing permissions to `Domain Users`. Within NTFS Security parameters, strip all standard top-level inheritance parameters down completely (**Disable Inheritance**) and map absolute system control parameters to the explicit target tracking variable profile of the **Creator Owner**.
4. Open the Active Directory Users and Computers console, multi-select the desired user accounts ➡️ **Properties** ➡️ **Profile** tab.
5. Under the **Home Folder** grouping block, check **Connect**, bind a preferred network drive mapping identifier (e.g., `Z:`), and reference the target hidden share using the system environmental lookup macro string: `\\PDC19\Home$\%username%`.
6. Upon committing changes, Active Directory automatically parses the variable, auto-generates a distinct directory folder matching each account's exact username on the storage disk, and hardens file permissions so that only that specific owner can browse its contents. When users (such as `Mohamed Zohdy` or `Salma Mohamed`) complete domain logon, their unique `Z:` workspace mounts natively, completely locked away from coworkers' view.

### B. Ubiquitous Environments: Roaming Profiles
By default, Windows creates user environmental tracking profiles (Desktop configurations, My Documents folders, AppData tracking, Downloads) locally on the endpoint workstation's storage hardware. Activating **Roaming Profiles** forces the operating system to host these configurations on the network, causing a user's exact workspace to seamlessly move and reconstitute across any device terminal inside the enterprise architecture upon authentication.

1. Provision a root network storage asset named `Roaming`, share it as hidden (`Roaming$`), grant full user sharing privileges, and isolate local safety structures exclusively to the folder builder.
2. Access the target account inside Active Directory, navigate to the **Profile** tab, and in the **Profile path** parameter block, map the network execution target using the user string lookup macro: `\\PDC19\Roaming$\%username%`.
3. **Operational Mechanics and Synchronization:** The moment an employee commits a logoff directive (**Sign out**), the host OS intercepts the routine and triggers a complete data synchronization loop, processing a direct **Upload** of all desktop modifications, cookies, and directory updates up onto the file server. When that user authenticates at a completely different office workstation next morning, the host system fetches the centralized image block from the server during initialization to build their native environment identically.
4. **⚠️ High-Priority Network Architecture Warning:** Network architects should explicitly avoid rolling out Roaming Profiles broadly to all organizational layers without scrutiny. Syncing massive user desktop files and browser directory profiles during intense morning logons and evening logoffs generates massive, compounding spikes in internal **Network Traffic**, which can severely strain throughput bounds and result in unacceptable, bottlenecked endpoint boot and shutdown delay cycles.
