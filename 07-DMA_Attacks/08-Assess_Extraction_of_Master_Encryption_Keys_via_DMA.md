# Assess Extraction of Master Encryption Keys via DMA

|ID          |
|------------|
|CHSTG-DMA-08|

## Summary

The ultimate goal of many DMA attacks is the extraction of Full Disk Encryption (FDE) master keys. Once an attacker has successfully escalated privileges to a root or SYSTEM level using DMA injection (as seen in CHSTG-DMA-07), they can leverage native operating system tools to reveal the encryption protectors or master keys stored in volatile memory. This allows the attacker to decrypt the drive offline or maintain persistent access to the data even if the system is later powered down.

## Test Objectives
- Utilize the privileged access obtained via DMA to retrieve disk encryption master keys or recovery protectors.
- Validate the ability to perform offline decryption of the target storage media using the extracted material.
- Demonstrate the bypass of BitLocker (Windows) or LUKS/dm-crypt (Linux) security through memory manipulation.

## How to Test
This test is the final phase of a DMA exploitation chain. It is performed on the live target system using a privileged shell. No disassembly is required.

### Prerequisites
- A successful privilege escalation to **NT AUTHORITY\SYSTEM** (Windows) or **root** (Linux) must have been achieved via DMA injection (refer to **CHSTG-DMA-07**).
- The target system must have Full Disk Encryption enabled (e.g., BitLocker or LUKS).

### Software Execution
From the privileged shell obtained via **PCILeech**, execute the following commands to extract the keys:

1.  **For Windows (BitLocker):**
    Use the native BitLocker management tool to display the key protectors:
    `manage-bde -protectors -get c:`
    - **Success Criteria:** The command returns the Numerical Password (Recovery Key) or the External Key material.

2.  **For Linux (LUKS/dm-crypt):**
    Use the device mapper setup tool to dump the active encryption keys from the kernel:
    `dmsetup table --showkeys`
    - **Success Criteria:** The command displays the master hex key used for the encrypted volume mapping.

## Remediation
- **Firmware/BIOS Level:** Enable **Intel VT-d** or **AMD-Vi** (IOMMU) to enforce hardware-level memory isolation, preventing unauthorized peripherals from interacting with the system RAM where keys are stored.
- **Operating System Level:** Enable **Kernel DMA Protection** to restrict DMA access for untrusted devices.
- **Encryption Policy:** Implement BitLocker with an **Enhanced PIN** or Startup Key (USB) rather than relying solely on the TPM ("TPM-only" mode), as the PIN/Key is required to release the master key into memory during the boot process.
- **Pre-boot Protections:** Use Pre-Boot Authentication (PBA) to ensure the disk remains encrypted and keys are not loaded into memory until a user is physically present and authenticated.