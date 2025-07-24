Test plan: Upgrade testing for Ubuntu 24.04 LTS to Ubuntu 24.10

# Table of Contents

1. [Document Information](#1-document-information)  
 1.1 [Author](#11-author)  
 1.2 [Revision history](#12-revision-history)  
 1.3 [Approval process and reviewers](#13-approval-process-and-reviewers)  

2. [Introduction](#2-introduction)  
 2.1 [Overview](#21-overview)  
 2.2 [Scope](#22-scope)  
 2.3 [Project information](#23-project-information)  
 2.4 [Schedule and milestones](#24-schedule-and-milestones)  
 2.5 [Reference material](#25-reference-material)  
 2.6 [Definitions and acronyms](#26-definitions-and-acronyms)  

3. [Testing strategy](#3-testing-strategy)  
 3.1 [Features to be tested](#31-features-to-be-tested)  
 3.2 [Features not to be tested](#32-features-not-to-be-tested)  
 3.3 [Deployment scenarios](#33-deployment-scenarios)  
 3.4 [Testing approach](#34-testing-approach)  

4. [Test environment](#4-test-environment)  
 4.1 [Prerequisites](#41-prerequisites)  
 4.2 [Operating systems](#42-operating-systems)  
 4.3 [Hardware](#43-hardware)  
 4.4 [Software](#44-software)  

5. [Risks and testing constraints](#5-risks-and-testing-constraints)  
 5.1 [Risks and assumptions](#51-risks-and-assumptions)  
  5.1.1 [Risks](#511-risks)  
  5.1.2 [Assumptions](#512-assumptions)  
 5.2 [Testing constraints](#52-testing-constraints)  

6. [Sample high-level test cases for upgrade testing (ordered by test technique and priority)](#6-sample-high-level-test-cases-for-upgrade-testing-ordered-by-test-technique-and-priority)

# 1. Document Information

## 1.1 Author
| Author             | Email                       | Date       |  
|--------------------|-----------------------------|------------|
| Rosa Micaela Serra | serra.rosamicaela@gmail.com | 05-05-2025 |

## 1.2 Revision history
| Author             | Date       | Version | Description                              |
|--------------------|------------|---------|------------------------------------------|
| Rosa Micaela Serra | 05-05-2025 | 0.1     | Initial version                          |
| Rosa Micaela Serra | 08-05-2025 | 1.0     | Discussed improving the scope and  identifying possible testing scenarios |
| Rosa Micaela Serra | 10-05-2025 | 2.0     | Final version. Refined test cases, scope and deployment  scenarios                            |

## 1.3 Approval process and reviewers
The document will be reviewed by the QA team and PO. Final approval will be granted based on consensus during scheduled review sessions.

# 2. Introduction

## 2.1. Overview

This test plan defines the approach for testing the upgrade process from Ubuntu 24.04 LTS to Ubuntu 24.10. The primary objective is to ensure that the upgrade completes successfully within a virtualized environment, the system boots without errors, and the upgraded operating system performs as expected across key functionalities.

## 2.2. Scope

- Upgrade of Ubuntu 24.04 LTS to Ubuntu 24.10 performed on a virtual machine using VMware Workstation 17 Pro, version 17.6.3 build-24583834  
- Verification of default system components, drivers, and services after the upgrade completion  
- Verify data integrity post-upgrade  

Out of scope:  
- Fresh installation and migration scenarios

## 2.3. Project information

- Product name: Ubuntu Linux  
- Product version: 24.04 LTS to 24.10 (upgrade)

## 2.4. Schedule and milestones

| Milestone                  | Planned date         |
|---------------------------|----------------------|
| Start of test planning    | 2025-06-25           |
| Test environment setup    | 2025-06-25           |
| Upgrade test execution    | 2025-06-26 to 2025-06-28 |
| Reporting and documentation | 2025-06-29         |

## 2.5. Reference material

- Ubuntu 24.10 Release Notes: https://discourse.ubuntu.com/t/oracular-oriole-release-notes/44878  
- Official Ubuntu Q&A Forum (Ask Ubuntu): https://askubuntu.com/  
- Ubuntu Upgrade Tutorial: https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-before-you-start  

## 2.6. Definitions and acronyms

- LTS: Long Term Support  
- VM: Virtual Machine  
- QA: Quality Assurance  
- CLI: Command Line Interface

# 3. Testing strategy

## 3.1. Features to be tested

- Upgrade process via CLI  
- Preservation of user files and system settings  
- System requirement checks before upgrade (disk space, connectivity)  
- System service startup and recovery post-upgrade  
- Removal of deprecated or obsolete packages  
- Verification of logs for upgrade errors or failures  
- Core component updates (Linux Kernel 6.11, OpenSSL 3.3, systemd v256.5)  
- Desktop and application enhancements (GNOME 47, App center, security center, and updated apps Firefox 130, LibreOffice 24.8 and Thunderbird 128)

## 3.2. Features not to be tested

The following features will not be covered in this test plan:

- Installation or migration processes  
- Third-party software installation post OS upgrade  
- Nvidia Graphics update  
- Server and cloud changes (server software updates and cloud-init 24.3.1)

## 3.3. Deployment scenarios

- Upgrade using VM VMware Workstation 17 Pro, version 17.6.3 build-24583834  
- The virtual machine will be configured with 2 vCPUs, 8 GB RAM and 100 GB disk space, simulating a typical environment  
- Network mode will be NAT or bridged, providing internet access during the upgrade process  
- Internet connectivity is required during the upgrade to fetch update packages and resolve dependencies  
- Snapshots will be taken before and after upgrades to enable rollback and recovery testing

## 3.4. Testing approach

- Perform the upgrade from Ubuntu 24.04 LTS to Ubuntu 24.10 using the CLI  
- Verify that the upgrade completes without errors and the system boots successfully  
- Validate the base OS functionality through smoke tests on core services  
- Document and report any failures encountered during the upgrade process

# 4. Test environment

## 4.1. Prerequisites

- Ubuntu 24.04 LTS must be installed before the upgrade  
- Verify hardware compatibility and ensure that all minimum system requirements are met for a successful upgrade

## 4.2. Operating systems

- Target OS: Ubuntu 24.10 (upgrade from Ubuntu 24.04 LTS)

## 4.3. Hardware

- The configurations of the host machine are:  
  - Memory: 12 GB  
  - Processor: AMD Ryzen 5 3600 6-Core Processor | 3.95 GHz  
  - Hard Disk (SCSI): 446 GB  

- The VM configured to host the OS has the following specifications:  
  - Memory: 8 GB  
  - Processors: 2 cores  
  - Hard Disk (SCSI): 100 GB

## 4.4. Software

- Virtual machine software: VMware Workstation 17 Pro, version 17.6.3 build 24583834  
- Apps tested:  
  - Firefox v130  
  - LibreOffice v24.8  
  - Thunderbird v128  
  - GNOME 47 Desktop Environment  
  - OpenSSL v3.3  
  - Ubuntu utilities  
  - GNOME Accessibility tools

  # 5. Risks and testing constraints

## 5.1. Risks and assumptions

### 5.1.1. Risks

| Risk                                                                 | Mitigation plan                                         | Priority |
|----------------------------------------------------------------------|--------------------------------------------------------|----------|
| Unstable or interrupted internet connection may cause upgrade failure or corruption. | Use a wired connection. Pre-download packages           | High     |
| Upgrading from 24.10 may cause conflicts between existing packages and new ones, breaking services. | Test upgrade in a staging VM, create snapshots and data backup | High     |
| Upgrade failure or interruption may corrupt user data or system settings. | Back up system and user data and avoid using system during upgrade. | High     |
| The snapshot used for rollback might not restore properly, leaving the system unrecoverable | Take multiple snapshots at different stages.            | High     |

### 5.1.2. Assumptions

- The official Ubuntu 24.10 repositories are online, valid, and complete at the time of testing.  
- The test environment mimics real-world configurations closely (same VM specs, dependencies, and network behavior).  
- Adequate disk space and permissions are available for the upgrade and recovery operations.  
- The team has access to root privileges or sudoer permissions to perform critical operations during the upgrade.

## 5.2. Testing constraints

- Limited hardware variety (virtual environment): All testing is being done in one virtual environment (VMware Workstation 17 Pro) using the same hardware. Because of this, the results might not reflect how the upgrade works on real physical computers or in other virtualization tools.  
- Time limitations: The testing will be planned on a short time. This means there might not be enough time to test every possible scenario or configuration.  
- Scope restrictions: As mentioned in the "Out of scope" section, fresh installations, system migrations and installing third-party software after the upgrade won’t be part of the testing plan. This means that any issues related to those areas won’t be detected during this testing phase.  
- CLI-only upgrade focus: This test plan only covers upgrades done using the command line. The upgrade done using the “Software updater” won’t be tested.  
- Manual testing effort: All tests will be done manually, which can take time and may lead to human mistakes.

# 6. Sample high-level test cases for upgrade testing (ordered by test technique and priority)

| Test case Id | Test case description                                                                 | Expected result                                                                                                  | Priority | Testing technique                  |
|--------------|---------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|----------|----------------------------------|
| HLTC-01      | Verify upgrade process initiates correctly via CLI using do-release-upgrade command  | The upgrade begins, packages download, and the installer proceeds without aborting.                             | High     | Upgrade verification testing     |
| HLTC-02      | Verify that the entire upgrade process completes without critical errors or interruptions | The CLI displays a clear message indicating that the upgrade process has completed successfully, without critical failures | High     | Upgrade verification testing     |
| HLTC-03      | Verify system reboots successfully after upgrade completion                          | The system restarts without issues and presents the Ubuntu 24.10 login screen.                                 | High     | Upgrade verification testing     |
| HLTC-04      | Verify network connectivity during the upgrade                                      | Installer maintains stable internet connection throughout package download                                      | High     | Upgrade verification testing     |
| HLTC-05      | Verify CLI prompts user to reboot immediately or later after upgrade completion      | The CLI explicitly prompts the user to reboot immediately or postpone the reboot.                              | Medium   | Upgrade verification testing     |
| HLTC-06      | Verify system logs capture all upgrade steps and errors                             | System logs (e.g., /var/log/dist-upgrade/) contain detailed records of all upgrade phases                       | Medium   | Upgrade verification testing     |
| HLTC-07      | Verify that all existing user accounts can successfully log in                      | Every existing user account can log in without errors using their pre-upgrade credentials                       | High     | Functional test cases            |
| HLTC-08      | Verify that Linux Kernel 6.11 is correctly installed and active                     | uname -r shows a 6.11.x kernel version                                                                           | High     | Functional test cases            |
| HLTC-09      | Verify that the GNOME 47 desktop environment is functional and responsive           | GNOME 47 interface is visible and responsive, UI is fluid                                                       | High     | Functional test cases            |
| HLTC-10      | Verify that pre-installed desktop applications (Firefox, LibreOffice, Thunderbird, Nautilus, Text Editor, Settings) are correctly updated, launch successfully, and maintain interface consistency under GNOME 47 | Applications open without error and reflect intended versions (Firefox ≥ v130, LibreOffice ≥ v24.8, Thunderbird ≥ v128). Interface elements load as per GNOME 47 guidelines | High | Functional test cases            |
| HLTC-11      | Verify that the operating system version is correctly displayed as Ubuntu 24.10 "Oracular Oriole" in system information | "Ubuntu 24.10 Oracular Oriole" is shown in "Settings" > "About" or via lsb_release -a                            | Medium   | Functional test cases            |
| HLTC-12      | Verify network functionality after reboot                                           | Ethernet works as expected and internet browsing functions normally                                             | Medium   | Functional test cases            |
| HLTC-13      | Verify that basic functionality of common peripheral devices (keyboard, mouse, USB drives) is confirmed | Peripherals are detected and operate as expected (e.g., typing, cursor movement, USB drive access)              | Medium   | Functional test cases            |
| HLTC-14      | Verify that OpenSSL 3.3 is correctly installed and that basic cryptographic operations using it are functional | openssl version reports version 3.3.x, and applications using OpenSSL perform correctly                         | Medium   | Functional test cases            |
| HLTC-15      | Verify that all user data (documents, pictures, videos, etc.) remains intact and accessible in their respective directories | All files in /home/username/Documents, /Pictures, etc. remain accessible; file sizes and timestamps unchanged    | High     | Data integrity                  |
| HLTC-16      | Verify that custom user desktop settings, such as wallpaper, themes, and icon sizes, are fully retained post-upgrade | Wallpaper, icon sizes, themes remain intact, and desktop appearance unchanged                                   | Medium   | Configuration testing           |
| HLTC-17      | Verify the full functionality of critical integrated hardware components such as WiFi, Bluetooth, and audio devices after the upgrade | WiFi connects to networks, Bluetooth devices pair and function correctly, and audio playback/recording works without distortion or disconnection | Medium | Compatibility testing           |
| HLTC-18      | Verify that system boot time does not significantly degrade post-upgrade, ensuring a consistent user experience | The time from power-on to a fully loaded desktop is comparable to or faster than the boot time before the upgrade | Medium | Performance testing            |
| HLTC-19      | Verify that common application launch times are not adversely affected after the upgrade, ensuring responsiveness | Applications like Firefox, LibreOffice, or the terminal launch within expected timeframes, similar to their performance before the upgrade | Medium | Performance testing            |
| HLTC-20      | Verify that the firewall status (enabled/disabled) and its configured rules are preserved and remain active post-upgrade, maintaining network security | sudo ufw status shows the same enabled/disabled status and rule set as before the upgrade, and network access adheres to these rules | High | Security testing              |
| HLTC-21      | Verify that essential security updates included in the Ubuntu 24.10 release have been correctly applied and are reflected in the package versions | Package managers (e.g., apt list --upgradable) confirm no critical security updates are pending immediately after the upgrade, and key security-sensitive packages reflect their 24.10 versions | High | Security testing              |
| HLTC-22      | Verify that only superusers can initiate the system upgrade                        | Non-sudo attempt prompts error “Permission denied” or equivalent                                                | High     | Security testing               |
| HLTC-23      | Verify that accessibility tools, such as screen readers, on-screen keyboards, high-contrast themes, and keyboard navigation, continue to function as expected | Enabled accessibility features operate correctly, allowing users to interact with the system as intended       | Medium   | Usability testing             |
| HLTC-24      | Verify the system's error handling and messaging when attempting an upgrade without an active internet connection | The system explicitly and clearly informs the user that an internet connection is required for the upgrade, stopping the process gracefully rather than failing silently or causing data corruption | High | Negative testing              |
| HLTC-25      | Verify the system's behavior and error messages if the upgrade process is interrupted unexpectedly | Upon restart, the system attempts to revert to a stable state (e.g., previous version or recovery mode) or provides clear instructions for manual recovery, rather than becoming unbootable or corrupted | High | Negative testing              |
