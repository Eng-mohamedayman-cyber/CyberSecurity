# Introduction to Linux

Kali Linux is an open-source, Debian-based operating system designed for cybersecurity tasks like penetration testing, digital forensics, and reverse engineering.

## Key Facts to Know:
* Interface: Kali is not very different from Windows in its visual style.
* Undercover Mode: If you are in public and want to look normal, run the command Kali-undercover to instantly switch the interface to a Windows style.
* Case Sensitivity: Unlike Windows, Kali can have two files with the exact same name in the same folder if the capital letters differ (e.g., test.txt and Test.txt are two different files).
* Why Use the Terminal?: Most security tools are built for the command line (shell), and it runs much faster than using a graphical interface (GUI).

## Steps to Download Kali (Virtual Machine)

1. Open your browser and go to: https://kali.org.
2. Click on Download.
3. Choose Virtual Machine.
4. Select your hypervisor software (e.g., VMware or VirtualBox).
5. Once downloaded, verify the file integrity by checking its hash with this command:
```bash
shasum -a 256 <File-Name>
```

## Linux File System Layout

### The system is organized into specific directories, each serving a unique purpose:
* / : Root — The starting point and foundation of the entire file system.
* /tmp/ : Temporary — Stores temporary files that are completely deleted when the system reboots.
* /bin/ : Binaries — Contains essential programs and commands needed to run the system.
* /sbin/ : System Binaries — Similar to /bin/ but contains administrative commands for the system.
* /etc/ : Editable Text Configuration — Used to view and change configurations for system services.
* /usr/bin/ : User Binaries — The standard folder where your installed applications are stored).
* /usr/share/ : Shared Data — Contains shared application tools, scripts, and documentation.

## Basic File & Directory Commands

* pwd : Print Working Directory — Shows the exact folder you are currently standing in.
* ls : List — Displays all files and folders in your current location.
* cd : Change Directory — Moves you into a different folder.
* cd .. : Step Back — Moves you up one folder level.
* cd - : Last Step — Takes you back to the very last folder you were in.
* mkdir : Make Directory — Creates a brand new folder.
* cp : Copy — Copies files or folders to a new location.
* mv : Move — Moves or renames files and folders.
* rm : Remove — Deletes files or folders.
* clear (or Ctrl + L) : Cleans up your terminal screen to give you a fresh view.

## Help & Documentation Commands

### If you run into a tool you don't know, use these commands to understand it:

* man <tool_name> : Opens the complete manual book for that specific tool.
* <tool_name> --help : Displays a quick, short summary of how to use the tool.
* whatis <tool_name> : Gives you a single-sentence definition of what the tool does.
* apropos <keyword> : Searches through all manuals for any tools matching that keyword.

## Network, Editing, & Monitoring Commands

* ifconfig (or ip a) : Displays your network interface details and your current IP address.
* echo : Prints out text directly on the screen.
* nano : A very simple text editor used to create or edit text files within the terminal.
* cat : Reads and displays the entire contents of a text file on your screen without opening it.
* sudo : Stands for "Superuser Do" — runs a single command with admin/root privileges.
* su : Switches your current identity to the system administrator (root user).
* which : Locates the exact system path where a specific command or tool is stored.
* locate : Quickly finds a file across your system by its name.
* find : Performs a deeper, more advanced search for files inside specific directory structures.
* updatedb : Updates the system database so that the locate command works accurately.
* top : Displays active hardware usage like RAM and CPU (similar to Task Manager in Windows).
* ps : Lists the processes and programs that are currently running in the background.
* Ctrl + C : Kill — Instantly stops any command or tool currently running.

## User & Service Management

### Account Administration:

* sudo adduser <name_user> : Creates a new user profile on the system.
* passwd : Changes the password for your current account.
* sudo usermod -aG sudo <name_user> : To add user in special permission group

### Managing System Services (SSH & Apache Web Server):

#### SSH Service (Secure Remote Access):

* sudo service ssh status (Checks if SSH is running or stopped).
* sudo systemctl enable ssh (Sets SSH to start automatically when the PC boots).
* sudo systemctl start ssh (Starts the SSH service right now).

#### Apache2 Service (Local Web Server):

* sudo service apache2 status (Checks the web server status).
* sudo systemctl enable apache2 (Sets the web server to launch automatically at boot).
* sudo systemctl start apache2 (Starts the web server right now).

## Package Management (Installing & Updating)

* sudo apt update: Updates your package lists to see which tools have new updates available.
* sudo apt upgrade: Installs the latest available updates for all your system files and apps.
* sudo apt install <app_name> : Downloads and installs a new tool from the internet.
* apt-cache search <app_name> : Searches the official app repository to see if a tool exists.
* apt show <app_name> : Shows full details and information about an app before installing it.
* sudo apt remove <app_name> : Uninstalls an app but keeps its settings files saved on your PC.
* sudo apt remove --purge <app_name> : Completely wipes out an app along with all its configuration settings.
* dpkg -i <file_name.deb> : Installs a local .deb application file that you downloaded manually.
* git clone <url> : Downloads a complete tool directory or source code repository from GitHub.
* wget <url> : Downloads any single file directly from the internet via its direct link.

