# Assess Thunderbolt-Based DMA Attack Feasibility

|ID          |
|------------|
|CHSTG-DMA-01|

## Summary

Thunderbolt interfaces provide external access to the high-speed PCIe bus. This control evaluates the feasibility of performing Direct Memory Access (DMA) attacks through these ports. By exploiting the plug-and-play nature of Thunderbolt, an attacker can connect a malicious device to read or write system memory without needing to disassemble the hardware. This is particularly critical when a device is left unattended in a sleep state (S3 or Modern Standby), as it may allow for the extraction of encryption keys or the injection of malicious code into the kernel.

## Test Objectives
- Verify if the system's Thunderbolt ports permit unauthorized DMA access.
- Assess the ability to read system RAM for sensitive data extraction (e.g., credentials, encryption keys).
- Assess the ability to write to system RAM to manipulate the OS kernel or escalate privileges.

## How to Test
This test must be performed on a live system without internal physical access, focusing on external ports.

### Prerequisites
- Ensure that any anti-DMA protections identified in the **Firmware Security** section (e.g., IOMMU, VT-d) are either disabled or under investigation for bypass.

### Hardware Setup
Depending on the Thunderbolt version available on the target (Thunderbolt 2, 3, or 4), use the appropriate adapter chain to connect a malicious FPGA card:
1.  **FPGA DMA Card:** Use a device such as a **PCIeSquirrel**.
2.  **For Thunderbolt 3/4:** Use an **e-GPU adapter/dock** to bridge the PCIe card to the USB-C/Thunderbolt port.
3.  **For Thunderbolt 2 (Legacy):** Use a chain of adapters: **PCIe to ExpressCard** -> **ExpressCard to Thunderbolt 2 (Mini DisplayPort)**.
4.  **Cross-Generation:** If necessary, use a **Thunderbolt 2 to Thunderbolt 3** adapter.

### Software Execution
Utilize **PCILeech** to verify memory access:
- **Verify Read Access:** Execute the following command to check if the RAM can be read (necessary for memory dumping):
    `pcileech testmemread`
- **Verify Write Access:** Execute the following command to check for random write access to the RAM (necessary for code injection):
    `pcileech testmemrandwrite`

## Remediation
- **Firmware/BIOS Level:** Enable **VT-d** (Intel Virtualization Technology for Directed I/O) or **AMD-Vi**. Configure Thunderbolt Security Levels to **User Authorization (SL1)** or **Secure Connect (SL2)** to prevent unauthorized DMA devices from connecting.
- **Operating System Level:** Enable **Kernel DMA Protection** (in Windows) or ensure IOMMU is strictly enforced (in Linux) to isolate memory spaces for external peripherals.
- **Pre-boot Security:** Disable Thunderbolt/PCIe "Option ROMs" and pre-boot DMA access in the BIOS settings.