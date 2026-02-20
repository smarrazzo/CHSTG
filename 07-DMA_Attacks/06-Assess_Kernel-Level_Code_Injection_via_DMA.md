# Assess Kernel-Level Code Injection via DMA

|ID          |
|------------|
|CHSTG-DMA-06|

## Summary

Once Direct Memory Access (DMA) read/write capabilities are confirmed, an attacker can bypass Operating System (OS) security boundaries by injecting code directly into the kernel. This attack allows for the execution of unsigned code with the highest possible privileges without interacting with the OS login screen or needing local credentials. This control evaluates the risk of a full system takeover (e.g., obtaining a SYSTEM shell on Windows or root access on Linux) via external or internal PCIe-based ports.

## Test Objectives
- Demonstrate the ability to inject and load a malicious kernel-mode driver (KMD) into system memory.

## How to Test
This test must be performed on a live system using an established DMA connection (via Thunderbolt or PCIe slots) without full disassembly of the device.

### Prerequisites
- A successful DMA read/write connection verified by `pcileech testmemread` and `pcileech testmemrandwrite`.
- Anti-DMA protections in the BIOS and Kernel must be disabled to confirm the vulnerability.

### Software Execution
Utilize **PCILeech** to perform the kernel injection:

1.  **Load the Kernel Module:** Run the appropriate command for the target Operating System to load the Kernel Memory Device (KMD) into RAM:
    * **Windows 11:** `pcileech kmdload -kmd WIN11_X64`
    * **Linux:** `pcileech kmdload -kmd LINUX_X64_48`
2.  **Capture the Memory Address:** If successful, the command will return a specific memory address (e.g., `0x7ffff000`). This address is required for subsequent commands.

## Remediation
- **Firmware/BIOS Level:** Enable **Intel VT-d** or **AMD-Vi** (IOMMU) to enforce strict hardware-level memory isolation.
- **Operating System Level:** Enable **Kernel DMA Protection** to prevent the OS from allowing DMA for unauthorized or untrusted devices.
 **Configuration:** Ensure the OS is configured to block unsigned drivers and that Secure Boot is enforced to protect the integrity of the boot chain.