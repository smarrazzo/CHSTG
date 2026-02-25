# Assess PCIe NVMe (M-Key) DMA Attack Feasibility

|ID          |
|------------|
|CHSTG-DMA-02|

## Summary

This control evaluates the risk of Direct Memory Access (DMA) attacks through the M.2 NVMe (M-Key) slot. While typically internal, these slots are often accessible via maintenance hatches or during quick physical access scenarios. Because NVMe drives communicate directly over the PCIe bus, an attacker can replace the storage drive with a malicious DMA-capable device to read or write system memory. This attack is performed by "cold-plugging" the device while the system is powered off and then booting into the operating system.

## Test Objectives
- Verify if the system's M.2 NVMe slot allows unauthorized DMA access to system memory.
- Determine if sensitive data (e.g., RAM dumps) can be extracted via the M-Key interface.
- Evaluate the effectiveness of system-level DMA protections when a malicious device is present at boot time.

## How to Test
This test focuses on scenarios where the NVMe port is accessible (e.g., via an easy-access panel) without full disassembly of the system.

### Prerequisites
- Ensure that Anti-DMA protections identified in the **Firmware Security** node (such as IOMMU or VT-d) are disabled to establish a baseline for the attack.

### Hardware Setup
1.  **Target Power:** Ensure the target system is completely **powered off**.
2.  **Malicious Device:** Use an FPGA-based DMA card, such as a **PCIeSquirrel**.
3.  **Adapter:** Connect the DMA card to the system using a **PCIe-1x to M.2 M-Key adapter**.
4.  **Connection:** Insert the adapter/card assembly into the target system's NVMe slot.

### Software Execution
1.  **Power On:** Turn on the target system and allow it to boot completely into the operating system.
2.  **Verify Read Access:** On the attacker's machine (connected to the DMA card), use **PCILeech** to check if the RAM can be read:
    `pcileech testmemread`
3.  **Verify Write Access:** Check for random read/write capabilities:
    `pcileech testmemrandwrite`

## Remediation
- **Firmware/BIOS Level:** Enable hardware-level memory isolation features, such as **Intel VT-d** or **AMD-Vi** (IOMMU), to prevent peripherals from accessing unauthorized memory regions.
- **Operating System Level:** Enable **Kernel DMA Protection** (e.g., on Windows 10/11) to ensure the OS manages and restricts DMA for all PCIe devices.
- **Physical Security:** Use tamper-evident seals or specialized screws on maintenance hatches to detect or prevent unauthorized access to internal M.2 slots.