# Assess Presence of Hibernation File on Unencrypted Partition

|ID          |
|------------|
|CHSTG-DISK-02|

## Summary

Hibernation is a power-saving state where the operating system saves the current contents of the RAM to a file on the hard drive (e.g., `hiberfil.sys` on Windows) before powering off. Because RAM contains sensitive material—including master encryption keys for secondary volumes, user credentials, and active session tokens—the hibernation file becomes a static image of the system's secrets. If this file is stored on an unencrypted partition or if the disk encryption is bypassed, an attacker can extract these keys to compromise the rest of the system.

## Test Objectives
- Locate and identify the hibernation file or swap partition on the target storage media.
- Determine if the hibernation data is stored on a partition that lacks Full Disk Encryption (FDE).
- Verify the accessibility of memory artifacts from the hibernation file without requiring the user's primary secret.

## How to Test
This test involves inspecting the storage configuration of the target device from an external forensic workstation.

### Prerequisites
- The target system must have been placed into a hibernation state (S4) prior to the test.
- The target disk must be connected to a secondary system for offline analysis (refer to the warnings in **CHSTG-DISK-01** regarding PCR invalidation).

### Execution Steps
1.  **Partition Analysis:** Use a disk utility (e.g., `Disk Management`, `GParted`, or `fdisk`) to list all partitions on the target drive.
2.  **Locate Hibernation Data:**
    * **Windows:** Search the root of the system partition (or any visible partition) for the `hiberfil.sys` file.
    * **Linux:** Identify the `swap` partition or swap files that may be used for suspend-to-disk operations.
3.  **Access Check:** Attempt to copy the file or dump the swap partition.
    * **Success Criteria (FAILED):** The test is failed if the hibernation file is found on a partition that does not require a decryption password to be read.
    * **Analysis:** Even if the system partition is encrypted, check if a secondary "Data" partition is unencrypted and contains a relocated hibernation file.

## Remediation
- **Disable Hibernation:** The most effective defense is to disable the hibernation feature entirely to prevent memory images from being written to the disk.
    - *Windows command:* `powercfg -h off`
- **Enforce Full Disk Encryption:** Ensure that the entire disk, including all swap areas and secondary partitions, is protected by strong encryption (e.g., BitLocker or LUKS).
- **Suspend-to-RAM Only:** Configure the system to use only Sleep (S3) or Modern Standby, provided that appropriate memory protections (TME/SME) are active to mitigate cold boot risks.