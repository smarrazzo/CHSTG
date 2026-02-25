# Assess Disk Decryption on Another System

|ID          |
|------------|
|CHSTG-DISK-04|

## Summary

This control evaluates the final impact of a successful key extraction by attempting to decrypt the target disk on a non-native system. Once the master encryption keys (BitLocker, LUKS, etc.) are obtained via DMA, cold boot, or TPM sniffing, the attacker can move the disk to a different machine to bypass all native operating system security measures. Mounting a BitLocker-encrypted Windows drive on a Linux environment is a classic example, as it allows the attacker to entirely ignore NTFS Access Control Lists (ACLs) once the volume is decrypted.

## Test Objectives
- Verify that the encryption keys or material retrieved in previous audit steps are valid and sufficient for full data access.
- Demonstrate that the target disk can be decrypted on a different platform or hardware environment.
- Assess the ability to bypass filesystem-level permissions (ACLs) through cross-platform mounting.

## How to Test
This test is conducted after the target disk has been identified as encrypted and the necessary keys have been extracted.

### Prerequisites
- Access to the target disk (connected via USB adapter or secondary port).
- Extracted encryption keys (e.g., FVEK for BitLocker or Master Key for LUKS).
- A secondary system running an alternative OS (e.g., a Linux forensic workstation).

### Execution Steps
1.  **Disk Connection**: Connect the target drive to the secondary Linux system.
2.  **Identify Partition**: Use `lsblk` or `blkid` to identify the encrypted partition (e.g., `/dev/sdb1`).
3.  **Attempt Decryption**:
    - **For BitLocker**: Use a tool like **dislocker** with the extracted key material:
        `dislocker -V /dev/sdb1 -k <EXTRACTED_KEY_FILE> -- /mnt/tmp`
    - **For LUKS**: Use **cryptsetup**:
        `cryptsetup open --type plain --key-file <EXTRACTED_KEY_FILE> /dev/sdb1 decrypted_volume`
4.  **Mounting**: Mount the decrypted loop device to a local directory:
    `mount -o loop /mnt/tmp/dislocker-file /mnt/target_data`
5.  **Access Verification**: Browse the directories.
    * **Success Criteria (FAILED)**: The test is failed if the drive mounts and files (especially protected user profiles) are accessible and readable.

## Remediation
Because this vulnerability is the result of compromised encryption keys, there is no direct remediation for the decryption process itself once the keys are lost. The security posture must focus on preventing the upstream key extraction:
- **Prevent Key Leakage**: Strengthen protections against DMA attacks, cold boot, and TPM bus sniffing as detailed in the **CHSTG-DMA**, **CHSTG-MEM**, and **CHSTG-TPM** nodes.
