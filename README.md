# Windows Brute-Force Attack Detection with Splunk

## Overview

This home lab demonstrates how repeated failed Windows authentication
attempts can be detected and investigated using Splunk.

A Kali Linux VM was used to generate controlled failed authentication
attempts against a Windows test account. Windows Security Event ID 4625
logs were forwarded to Splunk, correlated by source IP and target user,
and used to create a brute-force detection alert.

## Objective

The objectives of this lab were to:

- Generate controlled failed Windows authentication attempts
- Identify Windows Event ID 4625
- Forward Windows Security logs to Splunk
- Detect repeated authentication failures
- Create a Splunk alert
- Investigate whether authentication eventually succeeded
- Map the activity to MITRE ATT&CK

## Lab Environment

| System | Purpose |
|---|---|
| Kali Linux | Attack simulation |
| Windows VM | Target endpoint |
| Splunk Universal Forwarder | Windows log forwarding |
| Splunk Enterprise | SIEM / detection platform |
| VirtualBox | Virtual lab environment |

## Architecture

```text
Kali Linux
    |
    | Repeated failed authentication attempts
    v
Windows VM
    |
    | Windows Security Event ID 4625
    v
Splunk Universal Forwarder
    |
    | TCP 9997
    v
Splunk Enterprise
    |
    +--> Detection
    +--> Alert
    +--> Investigation
