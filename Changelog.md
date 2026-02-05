# Changes to rhel10CIS

## 1.0.1 - Based upon CIS official 1.0.1

- Thanks to Eugene@Frequentis for feedback
- Updated bootloader_password to bootloader_hash variable and context added
- disruption is high set back to default false
- fs.suid_dumpable template moved to correct control 1.5.4 from 1.5.3
- 6.2.2.1.2 updated logic as systemd/journald-upload.conf doesn't exist on clean install
- 5.4.1.1 description updated and disruption high added to control
- 2.3.2 - updated rhel10cis_time_synchronization_servers variables and updated template
- README updated to explain workstation controls and variable overrides
- 6.3.4.8 added logic as augenrules not always present on some OS
- fixed typos in levels aligned with benchmark
- 1.3.1.8 tidied up
- thanks to thulium-drake boot password hash Added passlib dependency in readme requirements
- tidy up tags on tasks/main.yml

- Fixes from Public RHEL9CIS PR 425
- 3.1.1
  - Added better sysctl logic to disable IPv6
  - Added option to disable IPv6 via sysctl (original method) or via the kernel
- 1.1.1.11 - comments in script updated
- 1.4.2 - efi boot options no longer required so removed
- 1.5.9 & 10 - template updated
- 2.1.4 kea services updated
- 5.1.2 - logic update
- 6.3.3.8 - updated auditd rule for NetworkManager and title updated
- 6.3.3.33 & 34 - updated rule logic

## 1.0.0 - Based upon CIS official 1.0.0

- updated to audit config
- max-concurrent option added
- auditd warning added as task
- latest workflows
- Added CCI references
- relabel added to selinux - new variable added

## 0.1.5

- run_audit logic update
- improvements to 5.3.3.x logic for rhel10 and ansible-core 2.19 compatibility.
- thanks to @piratesecurity
  - /boot/efi mount settings 1.4.2
- thanks to @stevehayes
  - audit files permissions
- pre-commit update

## 0.1.4

pre-commit updates
6.2.3.3 updated path for journald.conf

thanks to @DianaMariaDDM
- Improvements in defaults main
- typo fixes
thanks to @chrispipo
- rsyslog ordering
#thanks to @polski-g
- gdm logic for graphical desktop

## 0.1.3

Aligned with public RHEL9 fixes
- 5.4.2.5 - Enhancement for none existing directories thanks to @DianaMariaDDM
- 6.3.4.5 - fixed audit file permissions inline thanks to @DianaMariaDDM
- 6.3.3.5 - added missing locations for audit
- Added fix for yescrypt and root password check thanks to miso321

## 0.1.2

Update to audit_only to allow fetching results
resolved false warning for fetch auditq
Improved documentation and variable compilation for crypto policies

## 0.1.1 RHEL10 - updates

Thanks to @polski-g several issues and improvements added
Improved testing for 50-redhat.conf for ssh
5.1.x regexp improvements
Improved root password check
egrep command changed to grep -E

## 0.1 RHEL10BETA - expected CIS benchmark
