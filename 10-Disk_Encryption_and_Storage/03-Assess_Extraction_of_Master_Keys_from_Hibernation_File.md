# Assess Extraction of Master Keys from Hibernation File

|ID          |
|------------|
|CHSTG-DISK-03|

## Summary

The hibernation file is a compressed snapshot of the system's volatile memory (RAM) saved to the persistent storage. Because disk encryption keys must reside in RAM for the operating system to perform real-time data processing, these keys are inevitably written to the hibernation file (`hiberfil.sys` on Windows or the `swap` partition on Linux) when the system enters an S4 state. This control focuses on the forensic analysis of that file to extract cryptographic material, allowing an attacker to decrypt partitions offline.

## Test Objectives
- Perform an offline analysis of the hibernation or swap data to identify encryption metadata.
- Search for and extract master keys such as the Volume Master Key (VMK), Full Volume Encryption Key (FVEK), or LUKS master keys.
- Validate the extracted keys by successfully decrypting and mounting the associated encrypted volumes.

## How to Test
This test is conducted on a forensic workstation using the hibernation file or swap dump acquired during previous disk analysis steps (refer to **CHSTG-DISK-02**).

### Prerequisites
- A copy of the target system's hibernation file (e.g., `hiberfil.sys`) or a raw dump of the swap partition.
- Forensic tools capable of processing hibernation files, such as **Volatility 3**, **Hibernation Recon**, or specialized decompression scripts.

### Execution Steps
1.  **Decompression:** Hibernation files are typically compressed or header-wrapped by the OS. Use a tool to convert the file into a standard "raw" memory image format.
2.  **Key Scanning:**
    - **Automated Scan:** Run specialized plugins (e.g., `windows.bitlocker` in Volatility) to scan the memory image for BitLocker FVEK or VMK structures.
    - **Manual Analysis:** Search for AES key schedules or LUKS master key headers within the address space associated with disk driver buffers.

## Remediation
- **Disable Hibernation:** The most effective remediation is to completely disable the hibernation feature to ensure that no RAM snapshots are ever written to the disk.
    - **Windows:** Execute `powercfg -h off` from an administrative prompt.
    - **Linux:** Disable hibernate/suspend-to-disk targets in `systemd` or remove the swap partition/file requirements.
- **Encrypt Hibernation Data:** If hibernation is required, ensure it is saved strictly within a partition protected by Full Disk Encryption (FDE) with pre-boot authentication.
