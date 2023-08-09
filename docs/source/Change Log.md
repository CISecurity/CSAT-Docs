![](img/CIS_CSAT_Pro_RGB.png)

# Change Log #

## CIS CSAT Pro v1.13.0 ##
**August 9, 2023**

### CIS CSAT Pro Updates ###
- System Admins can now reorganize organization trees.  Manage Organization pages now have a Change Parent Organization option, enabling System Admins to move an organization/sub-organization to a different location within its current tree, move it into a different existing tree, or move it out of its current tree to be the top-level organization of a new tree.
- Buttons for certain long running actions are now temporarily disabled after the initial use of that button to prevent accidental multiple submissions and related errors.  This includes the Start New Assessment, Copy Assessment, Import Assessment, Create Organization, Create Sub-Organization, Logout, Login, and OTP Submission actions.
- Page titles, section headings, and table column names throughout CSAT Pro have been added and updated to provide users with more information about where they are in the tool.
- System Admin pages are now identified with the gear icon to better differentiate between similar System Admin and Org Admin functions, and remind admins to use caution when performing actions with elevated privileges.
- Organization Info pages have been updated with counts and formatting changes to provide information such as the number of assessments (total, open, closed), number of users, and the number of sub-organizations (total and immediate).
- When importing an assessment, some Safeguard titles will now be checked to catch cases where the trailing 0 may have been lost for X.10 Safeguards (for example, to help prevent Safeguard 16.10 from being imported as 16.1 if your spreadsheet has formatted the trailing 0 away).
- Word wrap has been added for multiple fields to better display long values including first name, last name, username, email address, website, organization name, assessment name, and custom tags.
- A banner will now be displayed to provide confirmation that a user was successfully deleted. 

### Bug Fixes ###
- Fixed an issue that led the previous CSAT Pro release (v1.12.0) to not be digitally signed.
- Additional checks have been added to evidence file uploads and assessment imports to resolve some issues.
- Fixed a bug that prevented very long discussion comments from being deleted.
- Fixed a bug that generated an error during assessment creation when a space was provided as the assessment name.
- Fixed a bug that improperly displayed timestamp information following assessment imports.
- Fixed a bug that led to jQuery exceptions in certain circumstances.
- Fixed several issues with license verification.

### Security Updates ###
- **Important Security Updates:** Updated third-party packages to resolve vulnerabilities present in embedded package dependencies.
- Passwords in the csat-config.yml file are now encrypted.
- Several additional HTTP Security headers have now been implemented and/or expanded including:
    - Cross-Origin-Opener-Policy
    - Cross-Origin-Resource-Policy
    - Content-Security-Policy
    - Expanded the use of Content-Disposition
    - Explicitly disabled the deprecated X-XSS-Protection header
- Previous password reset links for a user are now invalidated when a new one is generated.
- Additional validation has been added to better enforce Safeguard workflow actions.
- Character limits have been added for certain fields including first name, last name, username, email address, website, organization name, assessment name, custom tags, and discussion comments.  A warning is provided if a pasted value exceeds the length and will be truncated.

### Document Updates ###
- A documentation folder has been added to the release bundle.  The SBOM files, the licence.txt file, and the changelog.txt file can now be found in that folder.
- The SBOM files now contain the CSAT Pro version number.
- The SBOM files are now also available as a separate download in CIS WorkBench (in addition to being included in the release bundle).


## CIS CSAT Pro v1.12.0 ##
**April 19, 2023**

### CIS CSAT Pro Updates ###
- Added 4 new bulk Safeguard actions to the Assessment Summary page:
    - Bulk Complete.  This also generates bulk summary email notifications
    - Bulk Send Back (to undo the Complete status for Safeguards).  This also generates bulk summary email notifications.
    - Bulk Validate
    - Bulk Revert Validation
- Added a Delete User capability that System Admins can access from the User Management page.  (Previously, users could only be disabled, but not deleted.)   In some situations, the user being deleted will need to be replaced (if the user has Safeguard workflow assignments in assessments or is the sole Organization Admin for an organization/sub-organization); if the System Admin performing the deletion has the appropriate organization roles, that System Admin will automatically replace the deleted user.  Otherwise, a suitable replacement user will need to be selected in order to proceed with the Delete User action.
- The Windows installer will now copy the specified license and DXL configuration files to the “conf” folder in the installation directory during installation/upgrade.  Some users were encountering errors such as “Invalid License Key” under certain configurations; this change should help prevent many of those issues.
- Updated the System Admin organization role modification and removal actions so that replacement users can be selected in certain cases (when the user being modified is the sole Organization Admin for an organization/sub-organization, or when that user has Safeguard workflow assignments in assessments).  The “Include Sub-organizations” checkbox has now been made available for these actions as well.
- Added a “Require Password Change on Next Login” toggle that System Admins can access from the Edit User page for a particular user.  When toggled on for specific users, those users will be required to use the Forgot Password workflow to reset their passwords before they can login again.
- Updated the CIS Controls v8 to NIST CSF mappings.
- Expanded the characters allowed for the website search field on the System Admin Organization Management page.
- The Safeguards on the My Assigned Tasks and Pending for Validation Tasks pages are now sortable.
- References to the older “Sub-Control” term have now been updated to the newer “Safeguard” term throughout the tool (including the Safeguard Score column header in the CSV export).
- Updated the appearance of the colored score range indicator for Safeguard scores; it now appears as a colored circle next to the numerical score rather than the numeric score itself displaying the color.
- A “CSAT Pro Knowledge Base Articles” link has been added to the Support Center menu to provide easy access to a listing of CSAT Pro KB articles.
- The Unix installer has been updated to allow the Neo4j download link to be selectable so that it can be copied/pasted.
- CSAT Pro has been updated to use a new license verification service.

### Bug Fixes ###
- Bulk actions can no longer be performed against closed assessments.  To modify a closed assessment with bulk (or singular actions), you need to reopen the assessment first.
- Fixed a bug that allowed a negative 1 to be displayed for an industry average in rare cases.
- Fixed a bug in the installers so that some Advanced Mail Setting recommendations are populated for certain webmail providers.
- Removed duplicated text in Safeguard 5.5 (Controls v8) to correct the Safeguard description.

### Security Updates ###
- **Important Security Updates:** Updated third-party packages to resolve vulnerabilities present in embedded package dependencies.
- Added account lockout and unlock features:
    - User accounts can be automatically locked out after a specified number of failed login attempts (or automatic account lockout can be turned off entirely).
    - User accounts can be automatically unlocked after a specified number of minutes (or automatic account unlock can be turned off entirely).
    - Upon update, the default (CIS recommended) values are set: account lockout after 5 failed login attempts and auto unlock after 15 minutes.
    - These two values can be customized (or turned off) by System Admins in the System Settings page.  
    - User accounts can now also be manually locked or unlocked using the “Account Locked” toggle on the System Admin Edit User page for a user (accessible from the User Management page).
- The Feature-Policy HTTP Security Header has now been updated to the newer Permissions-Policy header.
- Additional security improvements.

### Document Updates ###
- Software Bill of Materials (SBOM) files are now included in the CSAT Pro release bundles (in both JSON and XML formats).


## CIS CSAT Pro v1.11.0 ##
**December 14, 2022**

### CIS CSAT Pro Updates ###
- When a change to a setting is successfully made on the System Settings page, this will update the csat-config.yml file so that the updated setting persists through reboots.
- System Admin users can now see a list of organizations which a user has a role in on the Edit User page, as well as showing what that user’s role is in each organization. System Admins can now modify these roles from this page as well.
- Added additional checks to prevent problematic cases when System Admins modify/remove user organization roles
- The Date Closed field can now be edited on the Edit Assessment page.
- Improved system navigation for System Admin users.
- The Manage User (Edit User) page available to System Admins now displays the Last Login date and Created Date of a user.
- Closed assessments on the Organization Info page and the Home page can now be sorted by the Date Closed column.
- The sub-organizations, assessments, and users tables on the System Admin Manage/Edit Organization page can now be sorted.
- Updated the CIS Controls v8 to NIST 800-53 Low Baseline mappings.

### Bug Fixes ###
- Fixed the display of error messages related to password length requirements.
- When all safeguard checkboxes have been deselected, the bulk edit button on the Assessment Summary page will now be disabled.
- Fixed a bug that allowed Safeguards to be validated without a score selected in some cases.
- Corrected some minor formatting issues on the Assessment Summary page.
- Fixed a typo in the spelling of the word "organization" in the organization history log.

### Security Updates ###
- **Important Security Updates:** Updated third-party packages to resolve vulnerabilities present in embedded package dependencies.
- Directory permissions for the installation directory in Windows installations are now more restrictive.
- Users are now required to verify their current password when changing their password from the My Profile page.
- Outdated TLS versions are now explicitly denied for HTTPS connections, rather than solely relying on browser configurations for this restriction.
- Additional security improvements.

### Document Updates ###
- Updated LICENSE.txt file to reflect the current versions of dependencies used.


## CIS CSAT Pro v1.10.0 ##
**September 29, 2022**

### CIS CSAT Pro Updates ###
- Tables and search results on the following pages can now be sorted (and reverse sorted) by clicking their column headers: Home page, Organization Info pages, Organization Management page, User Management page, Organization Admin Add User pages, Assessment Summary page.
- Expanded the set of allowable characters for Safeguard Discussion Comments; the pipe character ("|") will still be rejected.
- Mappings to external frameworks can now be used to filter Safeguards from the Assessment Summary page.
- Added a warning message to let Organization Admins know if an organization role removal action will remove the user entirely from the organization tree, since a System Admin would be required to add the user back to that tree in the future.
- When an Organization Admin provides a user with an organization role as part of the Organization Admin Create User action, the addition of the user to that organization is now logged in the Organization History log.

### Bug Fixes ###
- Fixed an issue where commas in organization names caused problems when trying to export a CSV from assessments in that organization.  Commas, periods, and ampersands in organization names are now replaced with underscores in the filenames of exported CSVs.
- Fixed an issue causing errors with the Bulk Unassign and Bulk Toggle Applicability actions on the Assessment Summary page.
- Fixed two issues with importing discussion comments from CSV files; comments were being imported in reverse order and names with more than two words caused issues
- Fixed an issue where an incorrect error message was sometimes displayed during Forgot Password password resets.
- Fixed an issue that was preventing the industry averages from updating properly. Note: this fix was released to the industry average service on 9/2/22.

### Security Updates ###
- **Important Security Updates:** Updated third-party packages to resolve vulnerabilities present in embedded package dependencies.
- Directory permissions for the installation directory in Linux installations are now more restrictive.
- Additional security improvements.

### Document Updates ###
- Updated LICENSE.txt file to reflect the current versions of dependencies used.

## CIS CSAT Pro v1.9.1 ##
**July 28, 2022**

### CIS CSAT Pro Updates ###
- System Admin users will now see the last login date and created date of a user on the User Management page.
- System Admins can now perform additional actions from the Manage Organization pages (accessible from Organization Management search results).
- System Admins can now search partial email addresses on the User Management page.
- When viewing a Safeguard, users with the Basic User organization role now have a tab allowing them to quickly navigate back to their My Assigned Tasks list.
- Miscellaneous wording and cosmetic changes.

### Bug Fixes ###
- Fixed a bug whereby editing an assessment to change the assessment name, start date, or due date would no longer save.
- Corrected the counts for open assessments, sub-organizations, and users in the Organization Management page.

### Security Updates ###
- **Important Security Updates:** Updated third-party packages to resolve vulnerabilities present in embedded package dependencies.
- Non System Admins are now restricted to only organizations and users in their organization trees when viewing Organization Info pages, Organization Charts, User Profile pages, and Organization Admin user search results.
- When editing an assessment name, validation has been added to ensure only allowed characters are used.
- Additional security improvements.

### Document Updates ###
- Updated license.txt file to more accurately reflect the current versions of dependencies used including some version numbers that were missed in the v1.9.0 license.txt file.

----------
## CIS CSAT Pro v1.9.0 ##
**June 6, 2022**

### CIS CSAT Pro Updates ###
- Additional fields are now included in the CSV export and import
    - Fields added to the export: Discussion Comments, Safeguard History Log, Custom Tags, Mappings to external frameworks, Implementation Group, Security Function, Asset Type, Safeguard Average (in percentage format), Safeguard Applicability, Assigned Date, and Due Date
    - Fields added to the import: Discussion Comments, Safeguard History Log, Custom Tags, Safeguard Applicability, Assigned Date, Due Date, Assigned To user, Assigned By user, Completed By user, and Validated By user
    - Assessment Import log has been improved
        - Assessment import log now persists as part of the Assessment Event log
        - Assessment Import log now includes the new import fields
        - Assessment Import log noise has been reduced
- New Organization Management page has been added for System Admins
    - Org Management page accessible from the System Admin (gear) menu
    - Search organizations by name, industry, website, or level (top level vs. sub-organization)
    - See summary information for organizations including the number of open assessments, users, sub-organizations, and parent organization name
    - Allows System Admins to view and modify organizations in the CSAT Pro instance
 - New search fields added to the User Management page for System Admins: email, system profile, and enabled/disabled
 - Filtering in the Assessment Summary page has been updated
    - Allows multiple selections within the same filter
    - Implementation Groups can now be selected individually
- The From email address set in the installer will now apply to OTP and Task emails (in addition to the Forgot Password emails that it already applied to)
- Improved navigation and user interface
    - Added links to the next and previous Controls from the Control View
    - Added a link to the Control View from the Safeguard View
    - Added links to the next and previous Safeguards from the Assigned Tasks list and from the Pending for Validation Tasks list
    - Made the Assessment Navigation Menu available at the top of more assessment pages
    - Added more tabs and information to the Assessment Navigation Menu including:
        - Assigned Tasks
        - Pending for Validation Tasks
        - Control View selector
        - Assessment Name displayed on more pages
    - The number of search results are now displayed
    - Updated informational and warning icons to be more consistent

### Security Updates ###
- **Important Security Updates:** Updated numerous third-party packages including several to resolve vulnerabilities present in embedded package dependencies
- Password length requirements (minimum and maximum) can now be customized by System Admins for the CSAT Pro instance from the installer and from the System Settings page

### Document Updates ###
- Updated the Deployment Guide to address PowerShell configuration requirements for Neo4j in Windows environments


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
 
