# Verify Presence of Full Disk Encryption

|ID          |
|------------|
|CHSTG-DISK-01|

## Summary

The first line of defense for data at rest is Full Disk Encryption (FDE). This control aims to verify if the primary storage medium (SSD/HDD) is protected by technologies such as BitLocker, LUKS, FileVault. Identifying the presence of encryption is a prerequisite for subsequent tests involving key extraction or offline data manipulation.

## Test Objectives
- Confirm whether the disk volume is encrypted or if data is stored in plaintext.
- Identify the specific encryption technology and version in use.
- Determine if the data is accessible when the drive is removed from its native environment.

## How to Test
This test focuses on verifying the encryption status by attempting to access the data from an external system.

### Prerequisites
- Access to the storage medium (e.g., via a maintenance hatch or external drive bay) without performing a full system disassembly.

### Execution Steps
1.  **Disk Removal/Connection:** Connect the target disk to a secondary forensic workstation or another computer using a USB-to-NVMe/SATA adapter. 
    * **CRITICAL WARNING:** Do **not** attempt to boot a Live OS (USB) on the target hardware itself to perform this check. Doing so can modify the **TPM Platform Configuration Registers (PCRs)**, which may invalidate the integrity check and prevent the original OS from booting later, effectively blocking further audit tests.
2.  **Mount Attempt:** On the secondary system, use disk management tools to inspect the partition.
    * **Windows:** Use `diskmgmt.msc` or `manage-bde -status`.
    * **Linux:** Use `lsblk` and `blkid` to check for `crypto_LUKS` or unknown file system types.
3.  **Validation:**
    - If the system prompts for a password/recovery key and identifies a known encryption header, the disk is encrypted.
    - If the partitions mount automatically and files are readable, the disk is **not** encrypted.

## Remediation
- **Enable Encryption:** Activate Full Disk Encryption (e.g., BitLocker on Windows, LUKS on Linux) for all system and data partitions.
- **Pre-Boot Authentication:** Ensure the encryption requires a strong secret (PIN, passphrase, or hardware key) before the OS boot process begins.
