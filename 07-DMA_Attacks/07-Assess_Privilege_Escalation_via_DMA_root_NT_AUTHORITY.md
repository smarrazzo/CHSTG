# Assess Privilege Escalation via DMA (root / NT AUTHORITY)

|ID          |
|------------|
|CHSTG-DMA-07|

## Summary

This control focuses on the final stage of a DMA-based attack: gaining full administrative control over the target operating system. By utilizing an existing kernel-mode injection (established in CHSTG-DMA-06), an attacker can bypass all standard authentication and authorization mechanisms. This leads to the execution of arbitrary commands as **NT AUTHORITY\SYSTEM** on Windows or **root** on Linux, representing a total compromise of the system's integrity and confidentiality.

## Test Objectives
- Demonstrate the transition from raw memory access to full OS-level administrative privileges.
- Confirm that security boundaries between user space and kernel space can be entirely neutralized via DMA.
- Verify the ability to spawn interactive privileged shells or execute root-level commands without user interaction.

## How to Test
This test is conducted on a live system with external or easily accessible PCIe/Thunderbolt ports. It requires no internal disassembly of the device.

### Prerequisites
- A successful DMA connection must be established.
- A kernel module (KMD) must already be loaded into the target's RAM (refer to **CHSTG-DMA-06**).
- The memory address of the loaded kernel module must be known (e.g., `0x7ffff000`).

### Software Execution
Using **PCILeech**, execute the following commands based on the target Operating System:

1.  **For Windows (Escalation to SYSTEM):**
    Open a privileged command prompt on the attacker's machine and run:
    `pcileech wx64_pscmd -kmd 0x7ffff000`
    - **Success Criteria:** An interactive command prompt is spawned on the target system running with **NT AUTHORITY\SYSTEM** privileges.

2.  **For Linux (Escalation to Root):**
    Run the following command to execute arbitrary tasks with root privileges:
    `pcileech wx64_exec_root -kmd 0x7ffff000`
    - **Success Criteria:** Commands are executed successfully with a UID of 0 (root).

## Remediation
- **BIOS/UEFI Level:** Enable **Intel VT-d** or **AMD-Vi** (IOMMU) to enforce hardware-based memory isolation, which prevents peripherals from accessing unauthorized memory regions.
- **Operating System Level:** Enable **Kernel DMA Protection** (e.g., Windows 10/11) to ensure the OS restricts DMA for untrusted or newly connected PCIe devices until the system is unlocked.
- **Memory Integrity:** Enable features like **Hypervisor-Protected Code Integrity (HVCI)** to prevent the injection of malicious code into the kernel even if memory access is achieved.