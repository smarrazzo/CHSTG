# Assess DMA Attacks via Other PCIe Slots (A, B, E Key)

|ID          |
|------------|
|CHSTG-DMA-03|

## Summary

Many modern laptops and desktops contain internal M.2 slots for expansion modules such as WiFi, Bluetooth (A or E Keys), or Cellular/WWAN (B Key). These slots are often routed directly through the PCIe bus. This control evaluates whether these secondary PCIe interfaces can be exploited to perform Direct Memory Access (DMA) attacks. By replacing an internal module with a malicious FPGA device using an adapter chain, an attacker can potentially bypass operating system security boundaries to read or modify system memory.

## Test Objectives
- Determine if non-storage PCIe-based slots (A, B, or E keys) are subject to DMA protection policies.
- Verify the ability to execute unauthorized memory reads or writes through these specific interfaces.
- Evaluate if the system firmware or operating system effectively isolates these peripherals using IOMMU/VT-d.

## How to Test
This test targets internal slots that are accessible through maintenance panels or easily removable covers without requiring a full system teardown.

### Prerequisites
- Ensure that Anti-DMA protections (e.g., IOMMU, VT-d) identified during the **Firmware Security** assessment are disabled to establish a baseline, or leave them enabled to test their effectiveness.

### Hardware Setup
1.  **Target Power:** Ensure the target system is completely **powered off**.
2.  **Malicious Device:** Prepare an FPGA-based DMA card, such as a **PCIeSquirrel**.
3.  **Adapter Chain:** Connect the hardware in the following order to bridge the different slot types:
    * **PCIeSquirrel** (PCIe-1x) -> **PCIe-1x to M.2 M-Key Adapter** -> **M-Key to [A, B, or E] Key Adapter**.
4.  **Connection:** Remove the existing module (e.g., WiFi card) and insert the adapter chain into the target slot.

### Software Execution
1.  **Power On:** Boot the target system and wait for the operating system to load completely.
2.  **Verify Read Access:** On the attacker's machine, use **PCILeech** to check for memory read capabilities:
    `pcileech testmemread`
3.  **Verify Write Access:** Use the following command to check for memory write capabilities:
    `pcileech testmemrandwrite`

## Remediation
- **Firmware/BIOS Level:** Enable **Intel VT-d** or **AMD-Vi** (IOMMU) to enforce memory isolation for all PCIe devices, including those in M.2 expansion slots.
- **Operating System Level:** Enable **Kernel DMA Protection** to ensure the OS manages peripheral memory access and prevents DMA for unauthorized or untrusted devices.
- **Physical Security:** Ensure that internal expansion slots are not easily accessible by using tamper-evident labels or security screws on access panels.