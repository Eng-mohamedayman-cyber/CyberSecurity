# Virtualization

* Normally, the hardware has only one operating system.
* So, we create a new layer between the OS and the HW called a hypervisor.
* From the hypervisor, we can create many virtual machines. There are two famous types of hypervisors: VMware from VMware company, and Hyper-V from Microsoft.

## To create a virtual machine, we need:
1. Memory (RAM)
2. Storage (Disk)
3. CPU (Processor)
4. Network

* The physical hardware is called the host, which has the RAM, storage, CPU, and network. We allocate (cut) from the physical resources to give to the virtual machine. We connect the virtual machine using a virtual switch.

---

# Types of Hypervisors :
Hypervisors are divided into two main categories based on where they are installed:

### Type 1 (Bare-Metal Hypervisor):

* Description: Installed directly on the physical hardware with no operating system underneath.
* Advantage: Highly efficient and used in enterprise data centers and servers.
* Examples: VMware ESXi, Microsoft Hyper-V (Server edition), and Proxmox VE.

### Type 2 (Hosted Hypervisor):

* Description: Installed as an application on top of an existing operating system (like Windows, macOS, or Linux).
* Advantage: Great for testing, development, and personal learning on your laptop.
* Examples: VMware Workstation, Oracle VirtualBox, and VMware Fusion.

---

# Key Virtualization Terms

### Host OS:
The primary operating system running directly on the physical hardware (used in Type 2).
### Guest OS:
The operating system running inside the virtual machine (VM).
### Snapshot:
A feature that saves the exact current state of a VM, allowing you to roll back if a failure or virus occurs.
### VHD / VMDK: 
Virtual Hard Disk formats used to store the VM's files and data.
