# RHEL 10 CIS

## Configure a RHEL 10 machine to be [CIS](https://www.cisecurity.org/cis-benchmarks/) compliant

### NOTE THIS IS NOT OFFICIAL AS NOT YET RELEASED BY CIS - BASED ON RHEL9

#### Based on [CIS RedHat Enterprise Linux 9 Benchmark v2.0.0](https://www.cisecurity.org/cis-benchmarks/)

---

![Org Stars](https://img.shields.io/github/stars/ansible-lockdown?label=Org%20Stars&style=social)
![Stars](https://img.shields.io/github/stars/ansible-lockdown/RHEL10-CIS?label=Repo%20Stars&style=social)
![Forks](https://img.shields.io/github/forks/ansible-lockdown/RHEL10-CIS?style=social)
![followers](https://img.shields.io/github/followers/ansible-lockdown?style=social)
[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/AnsibleLockdown.svg?style=social&label=Follow%20%40AnsibleLockdown)](https://twitter.com/AnsibleLockdown)


![Discord Badge](https://img.shields.io/discord/925818806838919229?logo=discord)

![Release Branch](https://img.shields.io/badge/Release%20Branch-Main-brightgreen)
![Release Tag](https://img.shields.io/github/v/release/ansible-lockdown/RHEL10-CIS)
![Release Date](https://img.shields.io/github/release-date/ansible-lockdown/RHEL10-CIS)

[![Main Pipeline Status](https://github.com/ansible-lockdown/RHEL10-CIS/actions/workflows/main_pipeline_validation.yml/badge.svg?)](https://github.com/ansible-lockdown/RHEL10-CIS/actions/workflows/main_pipeline_validation.yml)

[![Devel Pipeline Status](https://github.com/ansible-lockdown/RHEL10-CIS/actions/workflows/devel_pipeline_validation.yml/badge.svg?)](https://github.com/ansible-lockdown/RHEL10-CIS/actions/workflows/devel_pipeline_validation.yml)
![Devel Commits](https://img.shields.io/github/commit-activity/m/ansible-lockdown/RHEL10-CIS/devel?color=dark%20green&label=Devel%20Branch%20Commits)

![Issues Open](https://img.shields.io/github/issues-raw/ansible-lockdown/RHEL10-CIS?label=Open%20Issues)
![Issues Closed](https://img.shields.io/github/issues-closed-raw/ansible-lockdown/RHEL10-CIS?label=Closed%20Issues&&color=success)
![Pull Requests](https://img.shields.io/github/issues-pr/ansible-lockdown/RHEL10-CIS?label=Pull%20Requests)

[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit)](https://github.com/pre-commit/pre-commit)

![License](https://img.shields.io/github/license/ansible-lockdown/RHEL10-CIS?label=License)

---

### Community

Join us on our [Discord Server](https://www.lockdownenterprise.com/discord) to ask questions, discuss features, or just chat with other Ansible-Lockdown users.

---

## Caution(s)

This role **will make changes to the system** which may have unintended consequences. This is not an auditing tool but rather a remediation tool to be used after an audit has been conducted.

- Testing is the most important thing you can do.

- Check Mode is not supported! The role will complete in check mode without errors, but it is not supported and should be used with caution. The RHEL10-CIS-Audit role or a compliance scanner should be used for compliance checking over check mode.

- This role was developed against a clean install of the Operating System. If you are implementing to an existing system please review this role for any site specific changes that are needed.

- To use release version please point to main branch and relevant release/tag for the cis benchmark you wish to work with.

- If moving across major releases e.g. v2.0.0 - v3.0.0 there are significant changes to the benchmarks and controls it is suggested to start as a new standard not to upgrade.

- Containers references vars/is_container.yml this is an example and to be updated for your requirements

- Did we mention testing??

---

## Matching a security Level for CIS

It is possible to to only run level 1 or level 2 controls for CIS.
This is managed using tags:

- level1_server
- level1_workstation
- level2_server
- level2_workstation

The control found in defaults main also need to reflect this as this control the testing that takes place if you are using the audit component.

## Coming from a previous release

CIS release always contains changes, it is highly recommended to review the new references and available variables. This have changed significantly since ansible-lockdown initial release.
This is now compatible with python3 if it is found to be the default interpreter. This does come with pre-requisites which it configures the system accordingly.

Further details can be seen in the [Changelog](./ChangeLog.md)

## Auditing (new)

This can be turned on or off within the defaults/main.yml file with the variable run_audit. The value is false by default, please refer to the wiki for more details. The defaults file also populates the goss checks to check only the controls that have been enabled in the ansible role.

This is a much quicker, very lightweight, checking (where possible) config compliance and live/running settings.

A new form of auditing has been developed, by using a small (12MB) go binary called [goss](https://github.com/goss-org/goss) along with the relevant configurations to check. Without the need for infrastructure or other tooling.
This audit will not only check the config has the correct setting but aims to capture if it is running with that configuration also trying to remove [false positives](https://www.mindpointgroup.com/blog/is-compliance-scanning-still-relevant/) in the process.

Refer to [RHEL10-CIS-Audit](https://github.com/ansible-lockdown/RHEL10-CIS-Audit).

## Example Audit Summary

This is based on a vagrant image with selections enabled. e.g. No Gui or firewall.
Note: More tests are run during audit as we check config and running state.

```txt

ok: [rhel10_bios] => {
    "msg": [
        "The audit results are: Count: 800, Failed: 23, Skipped: 4, Duration: 128.649s",
        "",
        "Full breakdown can be found in /opt",
        ""
    ]
}

PLAY RECAP *******************************************************************************************************************************************
rhel10_bios                : ok=20   changed=1    unreachable=0    failed=0    skipped=20   rescued=0    ignored=0
```

## Documentation

- [Read The Docs](https://ansible-lockdown.readthedocs.io/en/latest/)

## Requirements

**General:**

- Basic knowledge of Ansible, below are some links to the Ansible documentation to help get started if you are unfamiliar with Ansible

  - [Main Ansible documentation page](https://docs.ansible.com)
  - [Ansible Getting Started](https://docs.ansible.com/ansible/latest/user_guide/intro_getting_started.html)
  - [Tower User Guide](https://docs.ansible.com/ansible-tower/latest/html/userguide/index.html)
  - [Ansible Community Info](https://docs.ansible.com/ansible/latest/community/index.html)
- Functioning Ansible and/or Tower Installed, configured, and running. This includes all of the base Ansible/Tower configurations, needed packages installed, and infrastructure setup.
- Please read through the tasks in this role to gain an understanding of what each control is doing. Some of the tasks are disruptive and can have unintended consequences in a live production system. Also familiarize yourself with the variables in the defaults/main.yml file.

**Technical Dependencies:**

RHEL/AlmaLinux/Rocky/Oracle 10 - Other versions are not supported.

- Access to download or add the goss binary and content to the system if using auditing
(other options are available on how to get the content to the system.)
- Python3.8
- Ansible 2.12+
- python-def
- libselinux-python

## Role Variables

This role is designed that the end user should not have to edit the tasks themselves. All customizing should be done via the defaults/main.yml file or with extra vars within the project, job, workflow, etc.

## Tags

There are many tags available for added control precision. Each control has it's own set of tags noting what level, what OS element it relates to, if it's a patch or audit, and the rule number.

Below is an example of the tag section from a control within this role. Using this example if you set your run to skip all controls with the tag services, this task will be skipped. The opposite can also happen where you run only controls tagged with services.

```sh
      tags:
      - level1-server
      - level1-workstation
      - scored
      - avahi
      - services
      - patch
      - rule_2.2.4
```

## Community Contribution

We encourage you (the community) to contribute to this role. Please read the rules below.

- Your work is done in your own individual branch. Make sure to Signed-off and GPG sign all commits you intend to merge.
- All community Pull Requests are pulled into the devel branch
- Pull Requests into devel will confirm your commits have a GPG signature, Signed-off, and a functional test before being approved
- Once your changes are merged and a more detailed review is complete, an authorized member will merge your changes into the main branch for a new release

## Known Issues

Almalinux BaseOS, EPEL and many cloud providers repositories, do not allow gpgcheck(rule_1.2.1.2) or repo_gpgcheck (rule_1.2.1.3) this will cause issues during the playbook unless or a workaround is found.

Audit - Running the audit sees an Increased RAM usage, improvements seen when dropping swappiness e.g. 5. Already improved by latest kernel update 6.12.0-55.12.1 as of 19-05-25 - appears to be systemd-userdbd issues

## Pipeline Testing

uses:

- ansible-core 2.12
- ansible collections - pulls in the latest version based on requirements file
- runs the audit using the devel branch
- This is an automated test that occurs on pull requests into devel

## Added Extras

- [pre-commit](https://pre-commit.com) can be tested and can be run from within the directory

```sh
pre-commit run
```

## Credits and Thanks

Massive thanks to the fantastic community and all its members.

This includes a huge thanks and credit to the original authors and maintainers.

Mark Bolwell
