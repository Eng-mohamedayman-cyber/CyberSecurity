# Introduction to Windows Server Administration

## 1. Fundamental Networking Concepts

### What is a Network?
A network is defined as two or more devices connected together to communicate and share resources.

![img](Image/lan_wan_network_diagram.png)

### Network Types by Geographic Scale :

* LAN (Local Area Network): A network that connects computers and devices within a limited geographical area, such as a single office or building.

* WAN (Wide Area Network): A network that extends over a large geographical distance, connecting multiple LANs together (e.g., The Internet).

### Key Network Devices :

* Router: A device that connects different networks and acts as a gateway between them.
* PC (Personal Computer): A device that consists of both Hardware and Software.
* Operating System (OS): Hardware alone is just "iron". It requires an Operating System to enable communication between the user and the hardware.

---

# 2. Types of Operating Systems 
Operating Systems are broadly divided into two main categories based on their role in the network:

                      [ Operating System ]
                               |
            +------------------+------------------+

            |                                     |
       [ Client OS ]                         [ Server OS ]
     e.g., Windows 8, 10, 11               e.g., Windows Server 2019, 2022, 2025
     Used by end-users/employees.          Used to centrally control computers,
                                           users, and security accounts.

---

# 3. Why Do We Need Networks? (Sharing of Resources)

The primary purpose of implementing a network is Resource Sharing, which can be categorized into three main types:

### A. Data Sharing :

* Without Network : You must use physical USB drives to copy and paste files manually onto each individual computer.
* With Network : You can use centralized File Sharing, allowing all computers to access and use data from one shared location.

### B. Device Sharing :

* Without Network : Every single computer must have its own dedicated peripheral (such as a printer) connected directly to it.
* With Network : Multiple computers can connect to and share a single network printer over the network infrastructure.

### C. Connection Sharing :

* Sharing a single internet connection across all connected devices in the infrastructure.

--- 

# 4. Network Management Models in Microsoft
Microsoft networks are managed and controlled using one of two central environments:

### 1. Workgroup Model (Peer-to-Peer) :

* Scenario: If you need each employee to log in with their username and password at any computer using a Workgroup environment, you must manually create duplicate user accounts on every single computer one-by-one.
* Management: Decentralized; there is no single point of control.

### 2. Domain Model (Client-Server) :

* Scenario: In a Domain environment, you create the user account once on the Windows Server (Active Directory). The user can then log in from any computer on the network.
* Management: Centralized; you can control, manage, and apply policies to all client PCs and user accounts by default from the server.
                            
  Workgroup    -----Join to Domain ------>   Domain

---

# 5. Core Services and Features in Windows Server Domain

When you establish a corporate Domain (for example: test.local), the Windows Server environment hosts a powerful suite of centralized roles and features required to manage an enterprise network :

### A. Identity & Centralized Management : 

* Active Directory : The core directory service used to manage user identities, computer accounts, and access permissions across the network.
* Group Policy : A feature that allows administrators to enforce security settings and manage user/computer configurations remotely.
* ADC (Additional Domain Controller) : A backup or secondary domain controller used to provide high availability and fault tolerance if the primary server fails.
* FSMO (Flexible Single Master Operations) : Specialized roles assigned to domain controllers to handle critical, non-duplicate tasks within the Active Directory forest.

### B. Network Infrastructure Services :

* DNS (Domain Name System) : Resolves human-readable domain names into IP addresses within the local network infrastructure.
* DHCP (Dynamic Host Configuration Protocol) : Dynamically and automatically assigns IP addresses and network configuration configurations to client devices.

### C. Resource & Data Management :

* File Server : Provides a centralized location for storing, organizing, managing, and sharing business files with specific user permissions.
* Print Server : Manages shared network printers, print queues, and driver deployment across the entire corporate infrastructure.
* Backup : Tools used to create copies of critical server data and system states to recover efficiently from disasters or hardware failure.

### D. System Deployment & Virtualization :

* WSUS (Windows Server Update Services) : Allows administrators to manage, test, and distribute the latest Microsoft updates and patches to network computers from a single central console.
* WDS (Windows Deployment Services) : Enables network-based installation of Windows Operating Systems over the network, eliminating the need for physical USB drives or CDs.
* Server Core : A lightweight installation option for Windows Server that runs without a Graphical User Interface (GUI), reducing the attack surface and hardware footprint.
* Hyper-V : Microsoft’s native hypervisor platform used to create and run virtualized testing environments and production servers.
* Remote Services : Tools used by administrators to connect to, configure, and monitor servers securely from any location.

---
