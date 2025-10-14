# Changes to rhel10CIS


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
