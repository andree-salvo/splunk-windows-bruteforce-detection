# Incident Report - Windows Brute-Force Authentication

## Alert

Windows Brute Force - Multiple Failed Logins

## Summary

Multiple failed authentication attempts were detected against the
Windows account `soc_bruteforce`.

The authentication attempts originated from the Kali Linux lab system
and generated multiple Windows Security Event ID 4625 events.

## Investigation

The source IP was identified through the Windows `Source Network Address`
field.

Splunk was used to correlate repeated authentication failures against
the same account.

Additional searches were performed for:

- Event ID 4624 - Successful Logon
- Event ID 4740 - Account Lockout

No successful authentication was identified following the failed
authentication attempts.

## Classification

**True Positive**

The detection correctly identified password-guessing behavior.

## Disposition

Authorized security testing performed in an isolated home lab.

## Impact

No impact.

No account compromise occurred.

## MITRE ATT&CK

**T1110.001 - Password Guessing**

## Recommended Production Response

If this activity occurred in a production environment:

1. Investigate the source IP.
2. Determine whether the source is authorized.
3. Review successful authentications following the failures.
4. Investigate other accounts targeted by the source.
5. Review account lockout activity.
6. Reset credentials if compromise is suspected.
7. Block malicious sources when appropriate.
8. Escalate confirmed compromise according to incident response procedures.