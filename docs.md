# F5 AWAF Brute Force Protection - Quick Reference

## Core prerequisites

1. BIG-IP Advanced WAF security policy.
2. At least one Login Page.
3. Reliable authentication-success condition.
4. Brute Force Protection enabled.
5. Blocking enforcement when mitigation is required.
6. Response pages configured when required by the selected mitigation.

## Detection dimensions

- Username
- Device ID
- Source IP
- HTTP Session
- Distributed attack correlation

## Quick flow

```mermaid
flowchart LR
R[Login Request] --> L[Login Page Match]
L --> C[Authentication Result]
C -->|Success| A[Allow]
C -->|Failure| T[Tracking]
T --> E[Threshold Evaluation]
E -->|Below Threshold| A
E -->|Threshold Reached| M[Mitigation]
M --> X[Alarm / CAPTCHA / Block]
```
