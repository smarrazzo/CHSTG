# Assess System Behavior in Sleep State

|ID          |
|------------|
|CHSTG-BOOT-01|

## Summary

This control aims to determine whether the system is currently in a sleep state by observing its behavior while having direct access to the device.

## Test Objectives
- Identify if the system is in sleep mode
- Differentiate sleep state from powered off state

## How to Test
1. Observe the device indicators:
   - Power LED behavior (blinking or steady low-power state)
   - Screen status
   - Fan activity
   - Peripheral LEDs (keyboard, network, etc.)

2. Interact with the system:
   - Press a keyboard key
   - Move the mouse or touchpad
   - Briefly press the power button

3. Determine system state:
   - If the system resumes quickly → sleep state
   - If a full boot sequence starts → powered off state

4. Document the observed behavior.

## Remediation
Disable sleep mode or require authentication on wake in system power management settings to prevent unauthorized access to an active session.
