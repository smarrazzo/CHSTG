# Assess System Behavior in Hibernation State

|ID          |
|------------|
|CHSTG-BOOT-02|

## Summary

This control aims to determine whether the system is currently in a hibernation state by observing its behavior while having direct access to the device.

## Test Objectives
- Identify if the system is in hibernation mode
- Differentiate hibernation state from sleep and powered off states

## How to Test
1. Observe the device indicators:
   - Power LED typically off
   - Screen off
   - No fan activity
   - No peripheral LED activity

2. Press the power button once.

3. Determine system behavior:
   - If the system restores the previous session after a longer startup time → hibernation state
   - If the system starts a fresh boot → powered off state
   - If the system resumes instantly → sleep state

4. Document the observed behavior.

## Remediation
Disable hibernation mode in system power management settings when it is not required, in order to prevent recovery of sensitive data from disk.
