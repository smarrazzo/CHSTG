# Assess Extraction of Master Encryption Keys from Memory Dump

|ID          |
|------------|
|CHSTG-MEM-04|

## Summary

Once a memory dump has been acquired (via DMA, Cold Boot, or other methods), the focus shifts to forensic analysis to locate and extract cryptographic secrets. Volatile memory is a prime target because it frequently stores Full Disk Encryption (FDE) keys, such as the BitLocker Full Volume Encryption Key (FVEK) or LUKS master keys, in plain text to allow the processor to perform real-time encryption and decryption of disk traffic. This control evaluates the ability of an attacker to use forensic tools to retrieve these keys and subsequently decrypt the system's storage offline.

## Test Objectives
* Analyze the physical memory dump to identify structures associated with BitLocker, LUKS, or other encryption providers.
* Extract master encryption keys or key schedules from the RAM image using forensic frameworks.
* Validate the utility of the extracted material by attempting to decrypt the target disk volume.

## How to Test
This test is performed on a forensic workstation using a memory image acquired in previous steps. No direct access to the target hardware is required during the analysis phase.

### Prerequisites
- A full physical RAM dump (e.g., `.raw`, `.bin`, or `.dmp`) obtained via controls like **CHSTG-MEM-01** or **CHSTG-DMA-05**.
- Forensic tools installed, such as **Volatility 3**, **Rekall**, or specialized scripts like `find-aes`.

### Execution Steps
1.  **Analyze Dump Metadata:** Use **Volatility 3** to identify the operating system and kernel version associated with the dump to ensure the correct symbols are used.
2.  **Search for Encryption Keys:**
    * **Automated Scanning:** Run plugins designed to find AES key schedules or specific encryption metadata:
        - For Windows/BitLocker: Use tools or plugins that scan for "FVE" (Full Volume Encryption) headers or AES-256 schedules.
        - For Linux/LUKS: Search the kernel memory space for the master key material used by `dm-crypt`.
3.  **Manual Forensic Search:** If automated tools fail, use `strings` or hex editors to look for key-related patterns or known structures in memory regions associated with disk drivers.

## Remediation
- **Hardware-Level Encryption:** Enable **Intel Total Memory Encryption (TME)** or **AMD Transparent SME (TSME)** to encrypt the entire system memory at the hardware level, rendering dumped data unreadable without the hardware-bound key.
- **Memory Scrambling:** Ensure the BIOS/UEFI has memory scrambling enabled to disrupt the physical data patterns of keys in DRAM.
- **Key Protection:** Configure the Operating System to use "TPM + PIN" protectors. This ensures the master key is only loaded into memory after the user provides a secret, reducing the window of opportunity for cold boot or DMA extraction.
