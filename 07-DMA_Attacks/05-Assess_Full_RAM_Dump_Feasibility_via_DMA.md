# Assess Full RAM Dump Feasibility via DMA

|ID          |
|------------|
|CHSTG-DMA-05|

## Summary

Once Direct Memory Access (DMA) has been successfully established through an external or internal port (as tested in CHSTG-DMA-01 through CHSTG-DMA-03), the next critical step is evaluating the ability to perform a full forensic acquisition of the system's volatile memory. A full RAM dump allows an attacker to perform offline analysis to extract sensitive information such as encryption keys (BitLocker, LUKS), user credentials, and active session tokens. This control focuses on the technical execution of a memory dump using specialized hardware and software.

## Test Objectives
- Verify the ability to bypass OS-level memory protections to read the entire physical address space.
- Successfully acquire a forensic image of the RAM for offline analysis.
- Confirm that the acquired dump size matches the physical RAM capacity of the target system.

## How to Test
This test assumes a successful hardware setup has already been established using a DMA-capable device (e.g., PCIeSquirrel) connected via Thunderbolt or an M.2/PCIe slot.

### Prerequisites
- A successful DMA connection must be active (verified by `pcileech testmemread`).
- Sufficient storage space on the attacker's machine to hold the resulting memory file (e.g., 16GB of storage for 16GB of target RAM).

### Software Execution
Utilize **PCILeech** to perform the memory acquisition:
1.  **Initiate the Dump:** Run the following command on the attacker's machine:
    `pcileech dump`
2.  **Monitor the Process:** PCILeech will begin reading physical memory and writing it to a file. 
3.  **Verification:** * The process should result in a file with a `.raw` extension.
    * Check the file size to ensure it corresponds exactly to the amount of physical RAM installed in the target system.
    * Example: A system with 32GB of RAM should produce a 32GB `.raw` file.

## Remediation
- **Firmware/BIOS Level:** Enable **Intel VT-d** or **AMD-Vi** (IOMMU) to enforce strict memory isolation and prevent unauthorized peripherals from accessing the full physical memory map.
- **Operating System Level:** Enable **Kernel DMA Protection** to ensure the operating system maintains control over DMA-capable devices and restricts their access to specific, authorized memory regions.
- **Pre-boot Security:** Implement a pre-boot authentication (PBA) mechanism to ensure the system does not boot into an environment where DMA can be exploited before the user is authenticated.