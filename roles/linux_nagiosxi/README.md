# Nagios XI Configuration Management on CentOS 9 Stream

Role installs NagiosXI from official RPM and updates all packages.

## Use

```yaml
---
- name: Install NagiosXI
  become: true
  hosts: all
  roles:
    - jacobvhs.unix_conf_management.linux_nagiosxi
```