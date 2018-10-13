# Ansible Role: BIG-IP Hardening

Ansible role to automate base BIG-IP hardening, and STIG/SRG configuration.

## Requirements

* Ansible 2.2 or greater

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
  * STIG NET0405 - Call Home Disable
  * STIG NET1665 - Remove default SNMP communities
  * STIG NET0700 - Appliance Mode

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    bigiq_hardening_server: localhost
    bigiq_hardening_server_port: 443
    bigiq_hardening_user: admin
    bigiq_hardening_password: secret
    bigiq_hardening_validate_certs: no
    bigiq_hardening_transport: rest
    bigiq_hardening_timeout: 120

Establishes initial connection to your BIG-IP. These values are substituted into
your ``provider`` module parameter.

    bigip_hardening_sshd_banner: enabled

Specifies whether the SSHD banner should be enabled on the BIG-IP.

    bigip_hardening_sshd_banner_text
    bigip_hardening_sshd_include
    bigip_hadening_sshd_timeout


    bigip_hardening_ntp_servers

Specifies NTP servers to define on the BIG-IP.


## Dependencies

None.

## Example Playbook

    - name: Run hardening tasks on BIG-IP
      hosts: bigip
      vars_files:
        - vars/main.yml
      roles:
        - { role: f5devcentral.bigip_hardening }

*Inside `vars/main.yml`*:

    bigiq_onboard_server: bigiq01.domain.org
    bigiq_onboard_password: secret
    bigiq_onboard_new_root_password: New_Admin_Secret123
    bigiq_onboard_old_root_password: default
    bigiq_onboard_new_admin_password: New_Root_Secret123
    bigiq_onboard_old_admin_password: admin
    bigiq_onboard_master_passphrase: M@sterPassphrase1234
    bigiq_onboard_dns_nameservers:
      - 10.10.10.10
    bigiq_onboard_dns_search:
      - domain.org
    bigiq_onboard_timezone: America/Los_Angeles
    bigiq_onboard_license_key: XXXXX-XXXXX-XXXXX-XXXXX-XXXXXXX

## License

Apache

## Author Information

This role was created in 2018 by [Tim Rupp](https://github.com/caphrim007).

## Credits

This role is based in large part off of the work done by the following
individuals

  * https://github.com/Mikej81/PowerSRG
  * https://github.com/dnkolegov/bigipsecurity

## References

* [STIG NET1639 - Idle Timeouts for Management Access](https://www.stigviewer.com/stig/free_space_optics_device/2013-03-14/finding/V-3014)
* [STIG NET0812 - NTP Configuration](https://www.stigviewer.com/stig/free_space_optics_device/2013-03-14/finding/V-23747)
* [STIG NET1645 - SSHD Lockdown](https://www.stigviewer.com/stig/wlan_bridge/2011-10-10/finding/V-5612)
* [STIG NET0405 - Call Home Disable](https://www.stigviewer.com/stig/infrastructure_router/2015-09-21/finding/V-28784)
* https://www.stigviewer.com/stig/f5_big-ip_local_traffic_manager_11.x/
