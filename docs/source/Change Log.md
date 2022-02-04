![](img/CIS_CSAT_Pro_RGB.png)

# Change Log #



----------
## CIS CSAT Pro v1.8.0 ##
**February 4, 2022**

### CIS CSAT Pro Updates ###
- Multi-Factor Authentication (using an emailed one time passcode) can now be enabled
- Members can now update the configuration settings for an existing CSAT Pro instance by re-running the installer
- Members can now choose which external control framework mappings are displayed for each user (from the User -> Mapping Preferences menu)
- The CIS Controls v8 industry averages have now been turned on for CSAT Pro instances that are opted in to industry averages

### Security Updates ###
- **Important Security Updates:** Updated numerous third-party packages to resolve vulnerabilities present in embedded package dependencies
- The log4j third-party library was updated to the most recent version (v2.17.1) in order to address a vulnerability found in earlier versions.  See CVE-2021-44832 for additional details.
- The default CSAT Pro Admin password can now be set with the installer
- Additional security improvements

### Document Updates ###
- Updated the System Recommendation information (operating systems and minimum disk space)


## CIS CSAT Pro v1.7.2 ##
**December 21, 2021**

### CIS CSAT Pro Updates ###
- None

### Security Updates ###
- **Important Security Update:** The log4j third-party library was updated to the most recent version (v2.17.0) in order to address vulnerabilities found in earlier versions.  See CVE-2021-45105 for additional details.

### Document Updates ###
- None


## CIS CSAT Pro v1.7.1 ##
**December 14, 2021**

### CIS CSAT Pro Updates ###
- None

### Security Updates ###
- **Important Security Update:** The log4j third-party library was updated to the most recent version (v2.15.0) in order to address a critical vulnerability found in earlier versions.  See CVE-2021-44228 for additional details.

### Document Updates ###
- None


## CIS CSAT Pro v1.7.0 ##
**August 26, 2021**

### CIS CSAT Pro Updates ###
- Added the ability to import CIS Controls v8.0 assessments from exported CSAT Pro or CIS-Hosted CSAT spreadsheets
- Added the ability to export a CSV file of filtered Safeguards from the Assessment Summary Page
- Increased the allowable file size for uploaded evidence files from 5MB to 15MB
- Added in-tool descriptions for the graphs
- Added greater emphasis on the required Neo4j version from the related Installer wizard page to decrease installation of incompatible Neo4j version
- Fixed a bug causing the Monthly Assessment Average graph to not display under certain circumstances
- Fixed a bug in the Implementation Group Average graph calculations
- Made additional performance improvements and bug fixes


### Security Updates ###
- **Important Security Updates:** Updated numerous outdated third party packages to resolve vulnerabilities present in embedded package dependencies
- Made additional security improvements

### Document Updates ###
- New "Port Information" Section in the Deployment Guide
- Note related to system restrictions that can interfere with the installation
- Greater emphasis on the required Neo4j versions

**Important:**
In case you missed it in the v1.5.0 release, a bug was fixed involving the applicability of Safeguards in assessments. 
If you have pre-v1.5.0 assessments that used custom Safeguard applicability (rather than one of the standard Implementation Groups), 
or used different Implementation Groups for different assessments, be sure to review the details on the [Troubleshooting page](../troubleshooting). 
If you do have any applicability adjustments to make, the new bulk applicability toggle on the Assessment Summary page might make the process easier.


## CIS CSAT Pro v1.6.0 ##
**May 18, 2021**

### CIS CSAT Pro Updates ###
- CIS Controls v8.0 support, including:
    - The ability to select between CIS Controls v7.1 and v8.0 when creating an assessment
    - CIS Controls v8.0 exports (Board Level Slides and CSV spreadsheet)
    - Copy Assessment functionality for Controls v8.0 assessments
    - CIS Controls v8.0 Safeguard mappings to NIST CSF and NIST 800-53 Rev 5
    - For users that opt in to the industry average service - please note that industry averages for Controls v8 assessments will display "0" for the time being.  Industry averages for Controls v7.1 assessments will continue to function as usual.  The v8 industry averages will be turned on in the near future, at which time there will be separate industry averages based on which version of the CIS Controls (v7.1 or v8.0) is specified for the assessment.
- Addition of two new bulk actions to the Assessment Summary page:
    - Bulk unassign – the ability to unassign users from multiple tasks at once
    - Bulk applicability toggle – the ability to toggle the applicability of multiple tasks at once
- Uploaded evidence files can now also be downloaded from Validated Safeguards/Sub-Controls, Closed Assessments, and Safeguards/Sub-Controls that are marked as Not Applicable
- Performance and security improvements

**Important:**
In case you missed it in the v1.5.0 release, a bug was fixed involving the applicability of Safeguards in assessments. 
If you have pre-v1.5.0 assessments that used custom Safeguard applicability (rather than one of the standard Implementation Groups), 
or used different Implementation Groups for different assessments, be sure to review the details on the [Troubleshooting page](../troubleshooting). 
If you do have any applicability adjustments to make, the new bulk applicability toggle on the Assessment Summary page might make the process easier.



## CIS CSAT Pro v1.5.0 ##
**March 4, 2021**

### CIS CSAT Pro Updates ###
 - Ability to copy an assessment
 - Ability to bulk assign users from Assessment Summary page
 - Fixed a bug with the "Implementation Group" dropdown action so it only applies to the current assessment

**Important:**
This bug deals with the applicability of Safeguards in assessments. If all the assessments in your CSAT Pro instance use the same IG and you don't use any custom applicability flags for individual Safeguards, then this bug shouldn’t affect you.
If you have assessments with different IG or custom applicability flags, please verify that the applicability flag for each Safeguard/task is set to the intended state. 
More information on this can be found in the [Troubleshooting page](../troubleshooting).

## CIS CSAT Pro v1.4.0 ##
**January 28, 2021**

### CIS CSAT Pro Updates ###
 - Ability to delete assessments
 - Ability to Unassign tasks
 - CIS Controls Framework is now mapped to NIST CSF v1.1 Framework
 - Mapping section is grouped by Control Frameworks and sorted
 - User Profiles are now accessible from Sub-Control View/Task View for "Assigned To/By", "Completed By" and "Validated By" users
 - Organization Logos appear in Organization Chart and Board Level Slides export

## CIS CSAT Pro v1.3.0 ##
**December 17, 2020**

### CIS CSAT Pro Updates ###
 - Ability to import a CSAT Pro CSV file as a new Assessment
 - Ability to edit the Assessment Details for existing assessments
 - The number of each Sub-Control is displayed in the Sub-Control View/Task View
 - Each Task in the Assessment Summary Page is now clickable and redirects to the Sub-Control View/Task View
 - Column Order changed for the CSV Export to better reflect the order of the workflow
 - More accurate message when Implementation Group of the Assessment is changed
 - Fixed a bug in the Installer that can prevent the Windows Neo4j service from starting after a system reboot
 - Fixed a bug in the Installer that can prevent a Linux Neo4j script from being executed
 - Fixed a bug which shows a warning message on successful rows during the Assessment Import of a Hosted CSAT XLS file

### Documentation Updates ###
 - Additional information on bundle extraction directory to avoid permission issues in Windows environment

## CIS CSAT Pro v1.2.0 ##
**October 22, 2020**
 
### CIS CSAT Pro Updates ###
 - Ability to visualize the Task Calendar
 - CIS Controls Framework is now mapped to PCI DSS v3.2.1 Framework
 - Ability to create Custom Tags tied to an Assessment Sub-Control
 - The Assessment Summary page can be filtered with multiple criteria including Custom Tags and other task properties
 - Discussions feature gives the ability to users to add comments to an Assessment Sub-Control
 - Ability to view the Assessment Event Log
 - Ability to upload your Organization Logo

## CIS CSAT Pro v1.1.0 ##
**September 17, 2020**
 
### CIS CSAT Pro Updates ###
 - Ability to visualize your Organization Chart 
 - CIS CSAT Pro can now export a Board Level Slides report
 - CIS Controls Framework is now mapped to NIST 800-53 Framework
 - Ability to see the Organization History Log
 - Email notification improvements including new notifications (for complete and send back actions) and more info included in notifications
 - Task Reminder feature to remind users when a task needs to be completed or validated
 - CIS CSAT Pro Installer updates including the ability to recognize and upgrade existing CSAT Pro installations on the machine
 - Fixed a bug that prevents the tool from running in an environment without an internet connection
 - Fixed a bug where the Task applicable toggle for one task could disable evidence file download/deletion actions for different tasks on the same page prior to reload

### Documentation Updates ###
 - Steps to Uninstall the tool in Windows and Linux
 - Additional Information on the CIS Controls Implementation Groups
 
## CIS CSAT Pro v1.0.0 ##
**August 17, 2020**

Initial Release
 
