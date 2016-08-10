# bigip-hardening

Ansible role to automate base BIG-IP hardening, and STIG/SRG configuration

## Requirements

This role requires Ansible 2.1 or higher and platform requirements are listed in the
metadata file.

## Resolutions

STIG, SRG, CVE, NIST SP 800-53r4 Controls, and General Hardening Resolved with
this role:

  * NIST SP 800-53r4 - Password Strength Policy — IA-5(1)
  * NIST SP 800-53r4 - Usage banner — AC-8
  * NIST SP 800-53r4 - Maximum Failed Login Attempts — AC-7
  * NIST SP 800-53r4 / STIG NET1639 - Idle Timeouts for Management Access — AC-2(5), SC-10
  * NIST SP 800-53r4 - Session Locking and Termination — AC-11, AC-12 (Advice-only block)
  * NIST SP 800-53r4 / STIG NET0812 - NTP Configuration — AU-8(1,2)
  * STIG NET1645 - SSHD Lockdown
  * STIG NET0405 - Call Home Disable.
  * STIG NET1665 - Remove default SNMP communities
  * STIG NET0700 - Appliance Mode

## Role Variables
The variables that can be passed to this role and a brief description about them are
as follows.


```

```

## Credential storage

Because this role includes usage of credentials to access your BIG-IP, I
recommend that you supply these variables in an ansible-vault encrypted
file.

This can be supplied out-of-band of this role

## Credits

This role is based in large part off of the work done by the following
individuals

  * https://github.com/Mikej81/PowerSRG
  * https://github.com/dnkolegov/bigipsecurity