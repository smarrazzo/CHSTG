# Assess Anti-Tamper Bypass Feasibility

|ID          |
|------------|
|CHSTG-PHY-04|

## Summary

This control aims to assess whether existing physical anti-tamper mechanisms could be bypassed when physical access to the device is available. The objective is to evaluate the robustness of the implemented protections and determine their resistance to destructive or semi-destructive manipulation.

## Test Objectives
- Evaluate resilience of physical anti-tamper mechanisms
- Assess whether protections rely solely on simple mechanical or electrical triggers
- Determine overall bypass feasibility under realistic physical attack scenarios

## How to Test
1. Identify previously detected anti-tamper mechanisms (e.g., intrusion switches, kill switches, conductive pads, tamper traces).

2. Analyze their mechanical and electrical design characteristics:
   - Location within the chassis
   - Dependency on mechanical pressure or electrical continuity
   - Integration with firmware detection logic

3. Assess potential attack categories at a high level:
   - Destructive approaches (physical damage to chassis while maintaining sensor state)
   - Semi-destructive manipulation of detection components
   - Electrical continuity manipulation in the case of conductive pads

4. Evaluate:
   - Required skill level
   - Required tooling
   - Likelihood of visible damage
   - Probability of successful bypass without triggering detection

5. Document the overall feasibility level (Low / Medium / High).

## Remediation
Not applicable.