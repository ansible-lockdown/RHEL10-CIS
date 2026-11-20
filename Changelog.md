# Changes to rhel10CIS

## CIS Benchmark 1.0.1
## November 2026 - QA fixes

- README rendered from the common template
- audit binary syver v0.16.0
- audit_bin_verify_signature: optional sqv check of the signed syver checksums
- 5.2.4: playbook user lock check matches the exact username
- 5.2.4: lock and password asserts skipped for users in rhel10cis_sudoers_exclude_nopasswd_list (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/129) - Thank you @presleydc
- 3.2.x: modprobe install and blacklist lines matched per item
- 5.3.2.1.1, 5.3.2.1.2: faillock.conf regexp matches existing deny and unlock_time lines
- 1.1.2.1.x: rhel10cis_tmp_svc defaults to auto - detects tmp.mount or fstab
- 1.1.2.1.x: tmp.mount enabled when managed by systemd
- /tmp remount busy warning sets reboot required
- boot type detected before the pre-remediation audit
- container discovery guarded when virtualization_type is undefined
- injected facts replaced with ansible_facts
- route flush handlers no longer write /etc/sysctl.conf
- auditd immutable rules change requests a reboot
- 98-auditd_exception.rules excludes only the listed users
- 5.3.2.2.x pam capture and 6.2.1.1 tagged patch
- check_mode false on read-only discovery tasks
- rhel10cis_force_user_maxdays and rhel10cis_force_user_mindays passed to the audit
- audit summary reports not run in check mode
- automated and manual tags on all controls
- 5.3.1.1 tagged automated
- company name MindPoint Group - A Quantum Sky Company
- 5.4.2.7: system accounts selected by UID below UID_MIN or 65534 (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/131) - Thank you @bunnywkwk
- 5.4.2.7, 5.4.2.8: account names matched exactly
- 5.4.2.7: playbook user and accounts already on nologin or false skipped
- interactive users exclude /usr/bin/false and match whole account names
- 5.4.1.1: PASS_MAX_DAYS discovery min and max order fixed
- 5.4.1.x, 5.4.2.8, 7.2.2: user module never creates a home directory
- 7.2.2: empty password accounts locked per user
- 1.6.x: crypto policy applied when the module is missing from the current policy
- 6.2.4.1: lastlog, wtmp, btmp file classes match the benchmark list
- 5.3.1.1: authselect select keeps features enabled on the current profile
- 2.1.18: nginx-plus removed with nginx, mask covers either package (as RHEL9-CIS issue https://github.com/ansible-lockdown/RHEL9-CIS/issues/483) - Thank you @JoannaSeen
- 1.4.2: every file in /boot/grub2 set root:root 0600, no files created
- 5.4.3.3: login.defs UMASK line set without rewriting comments
- 7.2.8: default ACLs skip home directories that do not exist
- authselect handlers flushed after 5.3.x
- 1.1.1.11: discovery script runs in check mode
- 1.1.2.x.1: missing separate partition warnings fire
- 5.4.2.2, 5.4.2.3: GID 0 discovery awk quoting fixed
- 5.4.2.2: removed accounts dropped from the captured user lists
- 5.4.1.5: existing user list matches password hashes
- 5.4.1.6: current date computed in a shell
- 5.3.2.1.1, 5.3.2.1.2: pam_faillock argument removal keeps the control field
- 5.3.2.1.3: even_deny_root and root_unlock_time removed in one run
- 5.3.2.4.2 - 5.3.2.4.4: pam_unix remember, hash and use_authtok edits ported from RHEL9-CIS
- 5.2.2: !use_pty removed from sudoers files
- 5.4.3.1: nologin lines in /etc/shells commented out
- 7.2.7: duplicate group names read from the group database
- 7.2.8: excess permissions removed from existing home directories
- 7.1.5 - 7.1.8: shadow and gshadow files mode 0000
- 1.2.1.3: per-OS repo_gpgcheck override uses rhel10cis_enable_repogpg
- 5.3.2.2.x, 5.3.2.3.x: pwquality and pwhistory option removal keeps the control field and line tail
- 5.3.2.2.3: all inline complexity options removed in one run
- 5.3.2.3.3: use_authtok added to pam_pwhistory
- 5.2.6: timestamp_timeout matched with spaces and negative values
- 5.2.4: empty exclude list handled
- 1.5.1: hard core lines in limits.d commented out
- 1.5.x: sysctl.conf keys matched at the start of the line
- 1.5.8: randomize_va_space key
- 1.3.1.2: SELinux disable arguments removed from every boot entry with grubby
- 1.3.1.2, 6.2.1.3: file edits skipped when the file is absent
- 4.1.4: zone target set per active zone, only where the target is ACCEPT (as RHEL9-CIS)
- 2.3.3: chronyd -u root removed
- 3.1.2: wireless adapter check uses find output
- 5.4.2.2: GID 0 account names matched exactly
- 5.4.2.5: root PATH checks read the PATH value
- 6.2.1.2: tmpfiles override read from /etc
- 6.2.1.3: journald.conf path
- 6.2.1.4: rsyslog stopped only when installed
- 6.2.2.1.2: insertafter matches the [Upload] section
- 6.2.2.1.4: systemd-journal-remote package checked
- 6.3.1.1: audit-libs package checked
- 6.3.4.x: audit tools mode u-x
- 7.1.11: sticky bit set per directory
- 7.1.13: SGID removed with SUID
- 7.1.x: relative symbolic file modes
- crypto policy module checked against the allowed list
- NO-SSHETM removed from the allowed crypto policy modules
- initrd rebuilt when its sysctl files differ from the system (rhel10cis_disruption_high)
- rhel10cis_os_enable_repogpg holds the OS default, rhel10cis_enable_repogpg can be set in inventory
- rhel10cis_disruption_high, rhel10cis_enable_repogpg and rhel10cis_rhel_default_repo passed to the audit
- rhel10cis_xinetd_server and rhel10cis_xinetd_mask removed
- no_log on bootloader password and /etc/shadow reads
- unused templates and Remounting /boot/efi handler removed
- community.crypto removed from requirements and meta
- GitHub Actions pinned to release tags, actions.lock and dependabot added
- README tracking tags aligned
- 5.3.1.5: missing pam_unix entries reported as a warning (as RHEL9-CIS)
- 7.2.9: dot file owner matched on the exact home directory
- crypto policy discovery runs for every crypto control, not only 1.6.1
- NO-SSHWEAKCIPHERS module follows rhel10cis_rule_5_1_6
- 5.1.5: Banner change validated and restarts sshd
- 5.1.x: sshd_config settings inserted before Include and Match
- 5.1.x: sshd_config regexps match active lines only
- sshd config file touch idempotent
- 4.1.4: no-op permanent zone task removed
- 5.4.1.5: INACTIVE default matched exactly
- 5.4.3.3: weak umask values in /etc/profile.d tightened
- 5.4.2.6: /root/.bashrc umask set
- 7.2.8: home directories created for interactive users only
- 5.4.2.7: accounts set to nologin dropped from the interactive user list
- 5.3.2.2.x: pwquality cleanup removes active lines only, gated on rhel10cis_disruption_high
- 5.3.2.3.2: enforce_for_root regexp
- 5.3.2.4.1: nullok removed from pam_unix lines only
- 5.3.1.1: check mode safe without the custom profile
- 50-pwcomplexity.conf: stray pragma line removed
- handlers: ignore_errors removed from sysctl flush and grub2 handlers
- 7.2.4 - 7.2.6: unused pwck -r pipe removed
- 60-disable_ipv6.conf: VLAN interface names written with /
- 7.1.11: df errors no longer fail the sticky bit discovery
- authselect, system shell, dot file and NOPASSWD exclusion settings passed to the audit
- molecule: stale 3.1.2 override and sysctl.conf touch removed
- molecule scenarios run the audit
- vars/CentOS.yml aligned with the other OS files
- 1.2.2.1: package metadata refreshed before updating
- 5.4.3.3: compliant symbolic umask values left unchanged

## CIS Benchmark 1.0.1
## October 2026 - QA fixes

- auditd: privileged commands discovery pipefail line join fixed
- auditd: excluded mounts now applied to privileged commands discovery
- 1.8.6: WaylandEnable written inside the [daemon] section
- 5.4.2.5: root PATH lookup falls back when sudo fails in containers
- 7.1.13: SUID/SGID find expression corrected (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/123) - Thank you @baka-yuki
- 7.1.12: missing space before the exclude path (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/123) - Thank you @baka-yuki
- 1.1.1.11: discovery script exits 0 when no modules found (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/124) - Thank you @nisseblankendaal
- 5.4.2.6: /root/.bash_profile mode aligned with 7.2.9 (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/122) - Thank you @baka-yuki
- 5.3.2.2.x: pam.d glob removed from pwquality conf search (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/121) - Thank you @baka-yuki
- 6.3.3.34: query_module rule only where the syscall is supported (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/120) - Thank you @baka-yuki
- 6.3.3.3: sudo log rule uses rhel10cis_sudolog_location (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/120) - Thank you @baka-yuki
- 6.2.1.x: journald tasks run for both syslog options (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/114) - Thank you @rajsshah86
- 6.2.1.4: systemd-journald no longer stopped when using rsyslog (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/114) - Thank you @rajsshah86
- 6.2.2.2: ForwardToSyslog set to no when using journald
- 6.2.4.1: rhel10cis_logfile_perms_exclude leaves matching log files unchanged (addresses https://github.com/ansible-lockdown/RHEL10-CIS/issues/91) - Thank you @skullbringer
- audit binary switched from goss to syver v0.13.0
- prelim_goss_available renamed prelim_audit_bin_available
- README audit section describes syver
- 6.2.x: rhel10cis_journald_config and rhel10cis_rsyslog_config configure each logging system independently - Thank you @skullbringer
- 6.2.2.x: journald controls only run when journald is configured
- 6.2.2.2: skipped when rsyslog is also configured
- 6.2.1.4: skipped when both logging systems are configured
- 6.2.3.5: mail.none restored to the catch-all messages rule
- 6.2.3.8: logrotate covers the log files 6.2.3.5 configures
- benchmark header added to changelog

## August 2026 - QA pass: handler, sysctl and default fixes

- Fixed /tmp mount options never applying - remount_tmp.yml flattened so every task carries listen thanks to @rajsshah86 public issue #112
- Fixed runtime sysctl drift never being corrected and added 60-fs_sysctl.conf to the POST reload
- Removed coredump replace tasks that commented out the RPM-owned /usr/lib vendor file each run thanks to @mindrb public issue #108
- Route flush moved to handlers so it only fires when sysctl config changes thanks to @goegol public issue #115
- Reload sysctl now defined before the route flush handlers so config is applied before the cache is flushed
- nfs_server and rpc_server now default true so the masking tasks actually run
- Corrected level tags for 1.2.1.3, 1.3.1.6 and 2.1.19 against the v1.0.1 benchmark
- Rebuilt vars/is_container.yml against v1.0.1 rule numbering - all 58 toggles were stale
- Audit variables moved from vars/audit.yml to defaults/main/audit.yml so they can be overridden
- Fixed auditd handler guards, exception template path, and added failed_when to greps that fail on no match
- README updates and updated contributing and contributors

## July 2026

- actions workflow update version
- Updated location that goss is taken from goss-org moved to krameff
- Fixed ansible dot notation missed last time
- auditd immutable check fix and handler logic
- thanks to @defnotyujine
  - rhel10cis_loopback_firewall_zone fixed for 4.1.6
  - tmp mount handler changed to import_tasks

issues:
thanks to @mindrb
- #104 tags on user check in main.yml
- #106 conditional logic not correct
- #108 missing notifies when changing conf files 1.5.x and values that don't adhere to standards to be commented out where docs advise

## June 2026 - QA pass: tag, toggle, and hygiene fixes

- Fixed 6 CIS level/profile tag mismatches against v1.0.1 recommendations (1.1.2.5.1, 1.8.5, 2.1.11, 2.1.20, 3.3.2.1, 6.3.3.22) - includes a `level2- workstation` typo (stray space) on 6.3.3.22
- **Behavior change**: `rhel10cis_nfs_server` and `rhel10cis_rpc_server` now default to `false` (was `true`, contradicting `*_mask: true` on the same services - services were configured to be both kept running and masked simultaneously)
- Removed a dead `notify:` on 6.3.3.10 referencing a non-existent "update auditd" handler (correct handler is "Restart auditd")
- Removed `export_badges_public.yml` and `update_galaxy.yml` from `.github/workflows/` - these are public-mirror-only workflows and should not exist in this private repo
- Fixed LICENSE copyright casing (`Mindpoint` -> `MindPoint`)
- Rebranded README Twitter badge to X (`x.com/AnsibleLockdown`)
- Added `prompt.md` and `test_inv` patterns to `.gitignore`
- Minor README grammar fix
- molecule added
- ansible_facts context change from ansible_facts.distribution to ansible_facts['distribution']
- Moved prelim tasks to control areas for easier management
- vars containing warning moved to actual task
- container vars file now a variable
- enable multiple line in the audit template
- 2.1.x service and pkgs logic vars now in vars/main.yml enabled a more agnostic OS approach going forward
- 5.4.3.3 thanks to @mboeker public pr #99 for raising this
- aide improvements thanks to @thuliumdrake
- 6.2.2 addressed some controls thanks to public issue #98 and @mboeker

## April 2026 - Common alignment and CIS validation (`rhel10`)


# 1.0.1 - June updates

- Updated logic on mount checks
- Updated tmp handler
- Connecting User logic updated
- Removed upcoming deprecation warning for ansible core modules - Use `ansible_facts["fact_name"]` (no `ansible_` prefix) instead.
- Ansible_vars_goss renamed to lockdown_audit.yml
- Updated collections/requirement.yml to use source now for core 2.16 or later
- Ansible core version minimum now 2.16 inline with other repos

# 1.0.1 - Additional public updates

thanks to @aaronk1
#85
#86
#86

Thanks to @defnotyujine
public PR 100

# 1.0.1 - April 2026 updates

- Tidy up and improve command and shell modules
- 3.2.x linting updated permissions
- Updated content in 6.2.3.8
- Thanks to @mindrb
  - #76 6.2.3.7 removed second condition not part of CIS
  - #77 & #78 - 6.2.3.3 - moved to drop in file as better practice
  - #79 root password check
- bootloader update rule 1.4.1 thanks to @skullbringer in the discord community
- 7.1.12 and 7.1.13 - fixed logic and ordering
- 2.1.x improved logic for stopped/disable/masked

# 1.0.1 - March 26 updates
- Common file updates
- De-duped company
- titles aligned
- meta aligned

- thanks to @defnotujine
  - #70 tags for acl 7.2.8
  - #72 3.2.3 correct level added

- thanks to @mindrb
  - #62 config aide enhancement
  - #63 typo in 5.1.1
  - #64 tmp.mount enhancement
  - #65 tidy up modprobe blacklisting
  - #68 6.2.3.8 package name typo fix
  - #69 use passwd rule fixed
  - #71 tuning chrony rules and new optional start variable
  - #72 rhel10cis_remove_kernel_discovery_script

## 1.0.1 - Based upon CIS official 1.0.1

2026 FEB QA Updates

- Fixed repeated word typos in defaults/main.yml and task names (5.3.2.2.5)
- Fixed missing apostrophe in 99-finalize.rules.j2 template
- Fixed subject-verb agreement in defaults/main.yml and goss template comments
- Fixed undefined variable references:
  - 5.3.1.5 - rhel10cis_authselect dict access corrected to rhel10cis_authselect_custom_profile_name
  - 5.4.1.3 - rhel10cis_pass dict access corrected to rhel10cis_pass_warn_age
  - tmp.mount.j2 - corrected rule variable references to rhel10cis_rule_1_1_2_1_x
- Added missing rhel10cis_uses_root variable definition to defaults
- Fixed register variable naming: discover_wireless_adapters renamed to discovered_wireless_adapters
- Fixed multiple consecutive spaces and grammar in comments across defaults, tasks, templates, and vars
- Fixed "can must" grammar error in AIDE cron schedule comments
- Removed 5.3.2.x controls from defaults/main
- Typo on task 1.5.8: Fix rhel10cis_rule_1_5_1 to rhel10cis_rule_1_5_8
- Add rule "Ensure rpcbind services are not in use" via 2.1.11
- 1.5.1 added missing * thanks to @christoffer-appe
- 6.3.3.33 and .34 fixed spacing in templates thanks to @christoffer-appe

Improvements Jan 2026

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

Fixes from Public RHEL9CIS PR 425

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
