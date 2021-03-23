---
uid: ReleaseNotes
---

# Release notes

EdgeCmd utility 1.1

## Overview

Edge Data Store (EDS) and PI Adapters have a REST API that allows user interaction. Configuration is one of the most common interactions. This command line tool, EdgeCmd utility, uses this REST API to apply all changes and administration functions to EDS and PI adapters. Specifically, EdgeCmd utility's command line interface uses configuration and administration functions of the REST API, so the user does not need to know the REST routes. EdgeCmd utility thus improves the user experience, facilitates easier scripting experiences and provides built-in help.

For more information, see [EdgeCmd utility](xref:index).

## Fixes and enhancements

### Fixes

The command line syntax and processing of EdgeCmd utility v1.1 has been entirely reworked from scratch, so there are no specific fixes.

### Enhancements

Changes from version 1.0

* A simpler command line syntax is now used.

* A verb (operation) is added to remove ambiguity between reading, writing, adding, removing, or editing.

* Command line arguments no longer require a specific order.

* Reduces the amount of command line arguments by not requiring full path to facets.  For example, for egress (PI Adapters) and storage (EDS), no component ID is required.

* Help output is improved in the following ways:

  * It is more comprehensive for overall program operation.
  * If a PI adapter is available, the help output shows available facets.
  * Available command line arguments are defined.
  * Command line examples are shown in bright color to stand out better.

* The command line syntax uses *-port* instead of *port* to instruct EdgeCmd utility which TCP port to use.  

* Administration support is added to start and stop components, and reset configurations to initial values.

* Diagnostics support is added.

* Support for CSV configuration for data selection, for both reading and writing.  

* No change to actual routes for setting or reading configuration although the PI Adapter's REST API port can no longer be modified through EdgeCmd utility.

## Known issues

There are no known issues at this time.

## System requirements

Refer to [System requirements](xref:SystemRequirements).

## Installation and upgrade

Refer to [Install EdgeCmd utility](xref:InstallEdgeCmdUtility).

## Uninstallation

Refer to [Uninstall EdgeCmd utility](xref:UninstallEdgeCmdUtility).

## Security information and guidance

### OSIsoft’s commitment

Because the PI System often serves as a barrier protecting control system networks and mission-critical infrastructure assets, OSIsoft is committed to (1) delivering a high-quality product and (2) communicating clearly what security issues have been addressed. This release of *EdgeCmd utility* is the highest quality and most secure version of the *EdgeCmd utility* released to date. OSIsoft's commitment to improving the PI System is ongoing, and each future version should raise the quality and security bar even further.

### Vulnerability communication

The practice of publicly disclosing internally discovered vulnerabilities is consistent with the Common Industrial Control System Vulnerability Disclosure Framework developed by the Industrial Control Systems Joint Working Group (ICSJWG). Despite the increased risk posed by greater transparency, OSIsoft is sharing this information to help you make an informed decision about when to upgrade to ensure your PI System has the best available protection.

For more information, refer to [OSIsoft’s Ethical Disclosure Policy (https://www.osisoft.com/ethical-disclosure-policy)](https://www.osisoft.com/ethical-disclosure-policy).

To report a security vulnerability, refer to [OSIsoft's Report a Security Vulnerability (https://www.osisoft.com/report-a-security-vulnerability)](https://www.osisoft.com/report-a-security-vulnerability).

### Vulnerability scoring

OSIsoft has selected the Common Vulnerability Scoring System (CVSS) to quantify the severity of security vulnerabilities for disclosure. To calculate the CVSS scores, OSIsoft uses the National Vulnerability Database (NVD) calculator maintained by the National Institute of Standards and Technology (NIST).  OSIsoft uses High, Medium and Low categories to aggregate the CVSS Base scores. This removes some of the opinion related errors of CVSS scoring.  As noted in the CVSS specification, Base score range from 0 for the lowest severity to 10 for the highest severity.

### Overview of new vulnerabilities found or fixed

This section is intended to provide relevant security-related information to guide your installation or upgrade decision. OSIsoft is proactively disclosing aggregate information about the number and severity of EdgeCmd utility security vulnerabilities that are fixed in this release.

No security-related information is applicable to this release.

## Technical support and resources

Refer to [Technical support and feedback](xref:TechnicalSupportAndFeedback).
