# Assess Extraction of Master Keys via TPM Traffic Analysis

|ID          |
|------------|
|CHSTG-TPM-02|

## Summary

Once the raw physical signals from the TPM bus (SPI or I2C) have been captured, the next step is to perform logical analysis to extract sensitive data. By decoding the communication protocol, an attacker can identify specific TPM commands and responses—such as those related to PCR (Platform Configuration Register) quotes or object unsealing—to intercept the cleartext disk encryption keys as they are transmitted to the CPU. This control evaluates the feasibility of converting captured waveforms into actionable cryptographic material.

## Test Objectives
- Decode the captured SPI or I2C waveforms into human-readable hex data or TPM command structures.
- Identify and isolate the specific exchange where the disk encryption master key is released.
- Successfully extract the Volume Master Key (VMK) or equivalent to prove the vulnerability.

## How to Test
This test follows the physical capture described in **CHSTG-TPM-01** and focuses on the software-based analysis of the traffic logs.

### Software Prerequisites
- **Analysis Software:** Use tools such as **Logic2** (for Saleae) or **DSView** (for DreamSourceLab) to process the capture files.
- **Protocol Decoders:** Ensure SPI or I2C decoders are active and correctly configured (e.g., proper Clock polarity and Phase for SPI).

### Analysis Execution
1.  **Load Capture:** Import the high-resolution capture file into **Logic2** or **DSView**.
2.  **Apply Decoders:**
    * For **SPI**: Map the channels to MISO, MOSI, CLK, and CS.
    * For **I2C**: Map the SDA and SCL channels.
3.  **Identify TPM Traffic:** Look for standard TPM 2.0 command patterns. Specifically, search for the `TPM2_Unseal` command or responses following a successful PCR validation.
4.  **Extract Key Material:**
    * Analyze the data packets following the unseal request.
    * Look for a 32-byte (256-bit) or 64-byte sequence that does not change between boots, which often represents the master encryption key.
5.  **Validation:** Use the extracted hex key with offline decryption tools (e.g., `dislocker` for BitLocker or `cryptsetup` for LUKS) to verify if it successfully mounts the encrypted partition.

Example:  
![BitLocker VMK Extraction](tpm/VMK_Extraction.png)  
Example of interception and decoding of the BitLocker VMK key using a DSLogic U3Pro32 logic analyzer and the DSView software.  


## Remediation
- **Mandatory PIN/Passphrase:** Configure the system to require a **BitLocker PIN** or a LUKS passphrase at pre-boot. This ensures that the TPM does not release the master key onto the bus until the user has provided a second factor of authentication.
- **TPM 2.0 Bus Encryption:** Enable "Parameter Encryption" features if supported by the motherboard and OS (e.g., Windows 11 with supported hardware), which encrypts the sensitive data as it travels between the TPM and the CPU.
- **Firmware Updates:** Ensure the BIOS/UEFI and TPM firmware are up to date to support the latest security protocols and bus protection mechanisms.