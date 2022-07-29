![](img/CIS_CSAT_Pro_RGB.png)

CSAT Pro User Guide
=====================================

Introduction
------------
The CIS Controls Self Assessment Tool (CSAT) is a web application that helps organizations track their implementation of the CIS Critical Security Controls® (CIS Controls®) down to the Safeguard/Sub-Control level (please note that Safeguard is the newer term in CIS Controls v8, while Sub-Control was the term used previously in CIS Controls v7.1; both CSAT and this guide use the two terms interchangeably).  CSAT provides a workflow to facilitate collaboration among team members as they self-assess the organization’s CIS Controls implementation.

A free, CIS-Hosted version of CSAT was released in early 2019 and is available at [CIS CSAT](https://csat.cisecurity.org/).

SecureSuite Members also have access to an on-premises version, CSAT Pro, which this User Guide describes.  CSAT Pro gives organizations greater control by allowing them to setup and host instances of CSAT in their own environment.


License
------------
Access to CSAT Pro requires a SecureSuite Membership.  Additional information on SecureSuite Membership can be found at [CIS SecureSuite](https://www.cisecurity.org/cis-securesuite/).

See [Obtaining Configuration Files](../CSAT%20Pro%20Deployment/#obtaining-configuration-files) in the [CIS CSAT Pro Deployment Guide](../CSAT%20Pro%20Deployment/) for more details on downloading your license file bundle.

The license file will expire when your SecureSuite Membership expires.  Once your SecureSuite Membership renewal has been processed, your new license file bundle should be available in WorkBench (navigate to your company information and then select “Licenses”).  You should download this updated bundle, extract the contents, and then replace the existing license and configuration files at the location that you selected during installation.
The path is visible from `CSAT_PRO_INSTALL_DIR/conf/csat-config.yml` in the following section:

		csat:
    		license:
        		filepath: C:\path_of_my_license_dir\license.xml

Once you've put the updated files in place, then restart the CSAT Pro service according to the instructions in [Restarting CIS CSAT Pro application service](../CSAT%20Pro%20Deployment/#restartingCSATService).


Privacy Policy
------------
Please read the [CIS CSAT Pro Privacy Policy](https://workbench.cisecurity.org/files/2891) prior to using CSAT Pro.


Getting Started
------------
Information on setting up a CSAT Pro instance can be found in the [CIS CSAT Pro Deployment Guide](../CSAT%20Pro%20Deployment/).  A default System Admin user is created during the installation process.  The default username is “admin” and the default password is “@admin123”.  You can use this default user to log in to CSAT Pro for the first time and to create other users.  It is strongly recommended that you change the password for this default user immediately, as this user has full access to the tool and the password is publicly available.


The Basics
------------
This section describes the basic CSAT Pro concepts including users, organizations, and assessments, as well as how they relate to each other.

### Users, Privileges, and Roles ###
Users have two primary attributes that determine which actions they can perform in CSAT Pro when interacting with the tool as a whole, as well as the organizations, assessments, and other users within the tool.  One of these attributes is the user’s System Profile, and the other is the user’s set of Organization Roles.

#### System Profiles ####
Each user is assigned a system profile, which determines the user’s access level to the tool as a whole.  There are two system profiles available:

- System Admin: Users with the System Admin system profile have full privileges to the tool, including the ability to create Top-Level Organizations and edit other users in User Management.
- Basic: Users with the Basic system profile have limited access to the tool and are restricted from tool-level administrative actions such as creating Top-Level Organizations and accessing User Management page. Users with a Basic system profile are restricted to only organizations and users in their organization trees when viewing Organization Info pages, Organization Charts, User Profile pages, and Organization Admin user search results.

#### Organization Roles ####
Once organizations are created in the tool, users can be assigned roles in those organizations.  The role is an affiliation between the user and the organization that determines what actions the user can perform on the organization, the organization’s assessments, and the organization’s users.  There are three Organization Roles available: 

-	Admin: An Organization Admin has full access to the organization, the assessments in that organization, and control over the organizational roles for users affiliated with that organization.  An Organization Admin can create Sub-Organizations under that organization as well, and can create new assessments for the organization as well.
-	Full User: A Full User has full access to work on existing assessments in the organization.  A Full User cannot create new assessments, cannot create Sub-Organizations, and cannot edit user Organization Roles for the organization.
-	Basic User: A Basic User has limited access to the organization’s assessments and can only view/complete tasks that have been directly assigned to that user.  A Basic User cannot create new assessments, cannot create Sub-Organizations, and cannot edit user Organization Roles for the organization.

A user can be assigned a different organizational role for each organization and sub-organization in CSAT Pro, though a user does not need to have a role assigned for each organization.  For example, User A might be an Organization Admin in Organizations Z and Y, might be a Full User in Organization Q, and might have no role at all in Organizations E and F.  User B might only administer the CSAT Pro instance and not need to work on any assessments, so User B might not have any Organization Roles assigned.

Note that Organization Roles and System Profiles are independent of each other.  A user with a Basic System Profile can have an Organization Admin role in an organization.  A user with a System Admin System Profile can have a Basic User Organization Role in an organization. For the purposes of organization and user visibility, a user is considered to be a part of an organization tree if they have an organization role in any organization or sub-organization in that tree.

### Organizations ###
Multiple organizations can be created in a CSAT Pro instance.  Organizations are organized into organization trees, each of which consist of a Top-Level organization and zero or more Sub-Organizations under that Top-Level organization.  Users with the System Admin system profile can create Top-Level organizations.  Once a Top-Level organization is created, users assigned the Organization Admin role in that organization can create Sub-Organizations under that Top-Level organization.  In turn, the Organization Admins of those Sub-Organizations can create additional Sub-Organizations under those Sub-Organizations.

### Assessments ###
Organization Admins can create assessments in the organizations that they administer.  Each organization can contain zero or more assessments.  A user’s access to an organization’s assessments is determined by the Organization Role the user has for that organization.

Each assessment will be open or closed.  Assessments begin “open” which means that users in that organization can work on those assessments based on their Organization Role.  When an assessment is completed, an Organization Admin can close the assessment.  A “closed” assessment can still be viewed, but it cannot be edited.  An Organization Admin can re-open a closed assessment as needed.


Pages and Actions
------------
This section contains a description of the pages within CSAT Pro and which actions can be performed on those pages.


### Login Page ###
The login page displays the tool title and version.  Users can enter their username and password here to login.  Usernames are case sensitive.  Users will receive a “Login failed. Username/Password was incorrect” message if the username was not recognized, or if the password provided was not the correct password for that username.  If an account is disabled, login attempts for that username will receive an “Account disabled. Please contact your Administrator” message.

The Login page also has a “Forgot Password?” link below the username/password fields.  This will display a pop-up where users can enter their username and click “Send”.  Doing so will send an email to the email address on file for that username.  The email will contain a link that will allow the user to reset the password for that account.

### Two Factor Authentication Page ###
If Multi-Factor Authentication (MFA) is enabled for the CSAT Pro instance, after successfully entering their username and password, users will be taken from the login page to the Two Factor Authentication page.  Here users will submit the One Time Passcode (OTP) that was sent to the email account associated with the username.  If too much time has passed since the login, or the user enters too many incorrect OTPs, the OTP will become invalid and the user will need to login again to receive a new OTP.

### Home Page ###
Upon logging in to CSAT Pro, a user will arrive at the Home page.  This page provides access to organization and assessment information that is specific to the current user.  You can return to the Home page by selecting “Home” from the top menu at any point.  The Home page contains the following sections:

#### My Organizations ####
The My Organizations section displays the Organization Name, Industry, and the current user’s Organization Role for any organizations in the CSAT Pro instance to which the current user has an organization role.  Each organization in this list is clickable and will take you to the Organization Info page for that organization.  If the current user is a System Admin, this section will also contain a “Create Organization” button that allows the user to create new Top-Level Organizations.
#### My Assessments ####
The My Assessments section displays the assessments associated with the organizations in the My Organization section.  The following information is displayed for each assessment in the list - Assessment Name, Assessment Template, Start Date, Due Date for open assessments (or Closed Date for closed assessments), Organization, and Action icons for any actions that the current user is permitted for the particular assessment (action icons can let you view the assessment’s dashboard, edit the assessment’s name/dates, view a list of tasks to complete, view a list of tasks pending for validation, or delete an assessment).  There is an Open tab and a Closed tab that allow the user to toggle between open and closed assessments.
#### Assessment Templates ####
An Assessment Template is the combination of a Control Framework and a Scoring Method.  The Assessment Template section lists the Assessment Templates available in this CSAT Pro instance and describes the Control Framework and Scoring Method for each.  CSAT Pro currently has two Assessment Templates available: 

-	CIS Controls v7.1 with Simple Scoring
-	CIS Controls v8.0 with Simple Scoring

### Top Menu ###
The Top Menu is present at the top of all pages in CSAT Pro.  From right to left, the Top Menu offers the following options:

####Home Button####
The Home button returns the user to the Home page.

####Support Center####
The Support Center menu has links to the CSAT Pro Deployment and User Guides, to the CIS Product Support portal (where you can submit a support ticket), to the CIS WorkBench Support Center (which has information and recorded webinars on a variety of CIS topics), and to the main CIS website.

####System Admin Menu####
System Admin users will have a gear icon to represent the System Admin menu which can take them to the User Management, Org Management, System Integrations, or System Settings pages.  For users with a Basic system profile, the gear icon will not be present.

####User Menu####
Clicking on the user’s username shows a menu that can take the user to the My Profile page or the Mapping Preferences page.

####Logout####
Logout will log the user out of CSAT Pro and return the user to the CSAT Pro login page.

####License Status####
The License Status symbol shows the status of the tool’s license.  This will be a green “LICENSE IS VALID” symbol in the upper right if the license is valid, or it will be a red symbol indicating that the license is invalid.


### Organization Info Page ###
The Organization Info page has the following sections: 

####Organization Section####
The Organization section displays the Name, Website, and Industry of the current organization.  Depending on the user's role in the organization, the following buttons can be found in this section:

- Edit - Only Organization Admins have access to this button.  The Edit button allows the organization’s Name, Website, and/or Industry to be updated.  
- Delete - Only Organization Admins have access to this button.  The Delete button will remove the organization, as well as all of the organization’s sub-organizations and assessments (so use with caution).  
- View Organization Chart -  All users have access to this button.  This button will display the top-level organization along with its sub-organizations in a hierarchical chart.  In this chart, the currently selected organization is highlighted in green, while the other organizations are in blue.  For each organization/sub-organization, the organization’s name and industry are displayed, as well the number of direct and total sub-organizations that are under that organization, and an organization logo (if uploaded).  Each parent organization has a circle at the bottom with a “-” or “+” symbol that will enable the sub-organizations under that organization to be displayed or hidden.  Users can drag to move around, as well as zoom in or out on the chart using the scroll wheel of the mouse.  Clicking on any of the organization blocks in the chart will take the user to the Organization Info page for that organization.
- Upload Logo/Delete Logo – Only Organization Admins have access to these buttons.  The Upload Logo button will prompt the user to browse to an image file (of type jpeg, jpg, bmp, or png; and under 500KB in size).  Once uploaded, the Upload Logo button will be replaced with the Delete Logo button.  The Delete Logo button will prompt for confirmation and then delete that organization’s logo file, reverting the button back to the Upload Logo button.  Uploaded organization logos will display in that organization’s Organization Info page, on the first slide of Board Level Slides exports for its assessments, and on its block in the Organization Chart.

####Sub-organizations Section####
The Sub-organizations Section displays the Organization Name and Industry for sub-organizations of the current organization.  Organization Admins have a “Create Sub-organization” button that will create a new sub-organization under the current organization.  The sub-organizations in this list are clickable and will take the user to the Organization Info page of that sub-organization.

####Active Users Section####
The Active Users section displays a list of the users that have Organization Roles in the organizations.  The icons under the action section allow Organization Admins to change a user’s organizational role or remove the user from the organization (deleting the user’s organization role for the organization).  Note that there is an “Include Sub-organizations” checkbox in the pop-up window for these actions; if this checkbox is selected, the same action will be performed for that user in the sub-organizations of the current organization as well.  Organization Admins also have an “Add Users” button in this section that allows the Organization Admin to create new users in CSAT Pro, or assign an organizational role for this organization to existing users that don’t currently have a role in this organization. Organization Admins creating new users through an Organization Info page's Add Users workflow will select an Organization Role for that organization on the Create User page.  Users who are not in any of the Organization Admin's organization trees will require a System Admin to add those users to the organization tree.

####Assessments Section####
The Assessments section displays a list of the assessments that exist in this organization.  The following information is displayed for each assessment in the list - Assessment Name, Assessment Template, Start Date, Due Date for open assessments (or Closed Date for closed assessments), Organization, and Action icons for any actions that the current user is permitted for the particular assessment (action icons can let you view the assessment’s dashboard, edit the assessment’s name/dates, view a list of tasks to complete, view a list of tasks pending for validation, or delete an assessment).  There is an Open tab and a Closed tab that allow the user to toggle between open and closed assessments.  Organization Admins have buttons to start a new assessment under this organization: “Start New Assessment” (to start a new blank assessment) and “Import Assessment” (to import an assessment from a previously exported Hosted CSAT or CSAT Pro spreadsheet).

####Organization History Section####
The Organization History section displays event log information for that organization including user changes (users added to the organization, users removed from the organization, and role modifications for users in the organization) as well as changes to the organization's info (name, website, and industry).  Organization/Sub-organization creation and deletion events are also displayed.  Sub-organization creation and deletion are logged in the immediate parent of the sub-organization, as well as in the top-level organization for that organization tree.  Assessments that are deleted as part of sub-organization deletions are also logged to both the immediate parent and top-level organizations.

####Assessment History Section####
The Assessment History graph on the Organization page shows how closed assessment scores for that organization have changed over time based on the date the assessment was closed.
The chart distinguishes between assessment templates used (separate tracking for CIS Controls v7.1 versus v8) and fluctuates the span of time based on what scores are available for that organization.

Clicking the information icon beside the graph title (the blue circle with letter 'i' in it) will display in-tool information about the graph.

### Creating a New Organization ###
Top-level organizations are the start of a new organization tree and can be created by users with the System Admin system profile from the Home page by clicking on the “Create Organization” button.  This button will go to a Create Organization page that lets the user enter the information needed to create the organization.

Similarly, users with an Organization Admin organization role can click the “Create Sub-organization” button from that organization’s Organization Info page.  This button will go to a Create Sub-organization page that lets the user enter the information needed to create the organization.

Each organization/sub-organization is created with the following attributes:

-	Name – the name of the organization must be unique within the CSAT Pro instance.
-	Website – the organization’s website does not need to be unique
-	Industry – the industry is selected from a drop down menu of choices.  If the CSAT Pro instance is opted in to the Industry Average Service, the industry selection will determine the industry data that is displayed for that organization’s assessments.

The user creating the organization is assigned the Organization Admin role for that organization by default.   That Organization Admin can then add an Organization Role for other users with the “Add Users” button from the Active Users section of that organization’s Organization Info page.


### Creating a New Blank Assessment ###
Organization Admins can create new assessments from the Organization Info page for that organization.  The “Start New Assessment” button goes to a Create Assessment page that lets the user enter the information needed to create the assessment.

Each assessment is created with the following attributes:

-	Name – The name for the assessment does not need to be unique
-	Due Date – The due date is the desired date to complete the assessment
-	Assessment Template – the Control Framework and Scoring Method that the assessment will use.  CSAT Pro users can select between CIS Controls v7.1 with Simple Scoring and CIS Controls v8.0 with Simple Scoring.
-	Implementation Group – when an Assessment Template to which Implementation Groups apply is selected, an Implementation Group will need to be selected as well.  Implementation Groups apply to CIS Controls templates.


### Importing an Assessment ###
The “Import Assessment” button also lets users create a new assessment, but instead of starting with a blank assessment, importing an assessment populates the new assessment with data from a previously exported assessment spreadsheet.  Two spreadsheet formats are currently accepted for imports:

-	a CSV file that was previously exported from CSAT Pro
-	an XLSX file that was previously exported from CIS-Hosted CSAT (using the “Control Summary Report” option in the “Reports section of the menu on the left side of the page)

The Import Assessment page lets the user enter the same information as described above for a new blank assessment, but requires two additional fields:

-	Source – Select either “CSAT Pro CSV” or “Hosted CSAT XLS” from the drop down depending on the origin of the spreadsheet to be imported
-	Assessment to Import – Use the “Choose File” button to browse to a spreadsheet file.  The selected spreadsheet file must be of the format of those exported from the selected Source.

A detailed log indicating import successes and warnings will be generated and displayed following the import process.  This import log also will be available in the assessment’s Event Log.

### System Admin Pages ###
System Admins have several pages available to them that users with a Basic system profile do not.

####System Integrations Page####
This page is available by selecting “System Integrations” from the gear icon on the top menu.  The Industry Average Service is the only system integration that is currently available.  Information on the Industry Average Service can be viewed by clicking on the blue question mark icon.  System Admins can choose to opt in with the “Opt In” button if their instance is currently opted out, or they can choose to opt out with the “Opt Out” button if their instance is currently opted in.

Instances that are currently opted in will have the “Test” and “Refresh Industry Averages” buttons available to them.  The “Test” button will verify the instance’s connection to the Industry Average Service and will result in a message in the upper left indicating the results of that test.  The “Refresh Industry Averages” button will initiate a pull of the latest industry average data from the service, and will send any unsent anonymous assessment information from the current instance.

####System Settings Page####
This page allows System Admins to turn MFA on or off.  When this setting is enabled, an OTP will be emailed to users as part of the login process, and users must enter the OTP to successfully login. This serves as a second factor for Two Factor Authentication in order to provide greater account security. When this setting is disabled, users only need to provide a username and password to successfully log in. We recommend this setting be enabled for greater security.

This page also allows System Admins to configure the minimum and maximum password lengths for the CSAT Pro instance.

####User Management Page####
This page is available by selecting “User Management” from the gear icon on the top menu.  The User Management page lets System Admins search the users in the CSAT Pro instance and create new users.

System Admins can either enter the appropriate search criteria (username, first name, last name, email, system profile, and/or enabled/disabled status) to narrow their search, or they can leave these fields empty to search for all users.  The resulting list will display the username, first name, last name, email, system profile, and enabled/disabled status, last login date/time, and user creation date/time for the users that met the search criteria. Users who were created prior to installation of CSAT Pro v1.9.1 (when this feature was introduced) will be blank for Date Created.  Users who have not logged in yet will show a blank for Last Login.

The “Create User” button allows the System Admin to create a new user. New users created through this System Admin Create User workflow will not have any Organization Roles upon creation.  System Admins can then add the appropriate organizational roles for the user with the “Add Users” functionality.

####Organization Management Page####
This page is available by selecting “Org Management” from the gear icon on the top menu.  The Org Management page lets System Admins search and modify the organizations in the CSAT Pro instance.  

System Admins can either enter the appropriate search criteria (organization name, industry, website, and org level) to narrow their search, or they can leave these fields empty to search for all organizations.  The resulting list will display the organization name, industry, website, parent organization, number of sub-organizations, number of users, and number of open assessments for the organizations/sub-organizations that met the search criteria.  System Admins can use the “Edit Organization” icon in the Action column to change the organization’s information.

### Creating a New User ###
Users in CSAT Pro can be created in two ways.  System Admins can create users with the “Create User” button on the User Management page.  Organization Admins can create new users by selecting the “Add Users” button on the Organization Info page for an organization that they administer, and then selecting “Create User” on the resulting page.  In both cases, the following information needs to be entered on the Create User page:

-	Username – usernames are unique to each user; different users cannot have the same username.  A username is set when the user is created and cannot be changed later.
-	First Name and Last Name – first and last names do not need to be unique among users and can be updated after user creation.
-	Email – The email address for the user does not need to be unique among users and can be updated after user creation.  This email address will receive notification emails from the tool (such as an email indicating when this user is assigned to a task in an assessment).
-	System Profile – The user’s permission level in the tool (either System Admin or Basic)
-	Password – Users can update their passwords after user creation

Note that the System Profile dropdown may be limited by the creating user’s system profile.  So, an Organization Admin that only has a Basic system profile can only create users with a Basic system profile.

Organization Admins creating new users through an Organization Info page's Add Users workflow will choose an Organization Role to assign to the new user for the currently selected organization/sub-organization on the Create User page. New users created through the System Admin Create User workflow will not have any Organization Roles upon creation.  System Admins can then add the appropriate organizational roles for the user with the “Add Users” functionality.

### Adding a User to an Organization ###
Organization Admins can add a user to an organization by giving that user an Organization Role for that organization.  To do so, the Organization Admin should first select the “Add Users” button on the Organization Info page for an organization that they administer.  Next, the Organization Admin should perform a search to find the user or users that they want to add (by either entering the appropriate search criteria to narrow their search or leaving these fields empty to search for all users).  In the resulting user list, the Organization Admin should select the checkboxes for the user or users to be added.  (Note: Users who already have an organization role in this particular organization/sub-organization will not appear in the search results. Additionally, organization Admins with a Basic system profile will only see users in these search results who share an organization tree with the Organization Admin.)   Then, the Organization Admin should click the “Add Users” button.  This will bring up the “Select Organization Role” pop-up where the Organization Admin can select the desired Organization Role from the dropdown and check/uncheck the “Include Sub-organizations” checkbox, before finalizing the action by clicking “Add Users To Organization”.

If "Include Sub-organizations" is checked, the user's role in each of the selected organization's sub-organizations will be overwritten by the selected role (if that user already had a role in the sub-organization).  If the user doesn't currently exist in a sub-organization, the user will be added to that sub-organization with the selected Organization Role.  The user(s) will only be added (or modified in) sub-organizations for which the current Organization Admin is also an Organization Admin.

Similarly, System Admins can add users to an organization from the Org Management page, then clicking Edit Organization for the organization they wish to edit, and then selecting Add Users on the Manage Organization page for that organization.

### My Profile Page ###
The My Profile page is accessible from the Top Menu, by clicking on the user’s username, and then selecting “My Profile”.  This page lets users view their own user information, update that information (First Name, Last Name, Email Address), and change their password.

### Mapping Preferences ###
The Mapping Preferences page is accessible from the Top Menu, by clicking on the user’s username, and then selecting “Mapping Preferences”.  This page lets the user select which external frameworks the user would like to see in the Mappings section of the Safeguard View.  The page displays which CIS Controls versions that each external framework is mapped to.  Once a user has selected/deselected the checkboxes as desired, press the Save Preferences button to save those selections.  The preferred framework mappings are user specific, so users can each choose their frameworks of interest without impacting other users in the instance.

### Assessments ###
Once an assessment is created in an organization, there are several pages that let users with a role in that organization work on that assessment and view the data in it.

####Assessment Dashboard Page####
Users with an Organization Admin or Full User role in an organization can view the Assessment Dashboard for that organization’s assessments.  Users can see which Assessment Dashboards they are able to view from the My Assessments section on the Home page; users can click the book icon in the Action column to navigate to the Assessment Dashboard for a particular assessment.  Similarly, users can use the book icon in the Assessments section of the Organization Info page for a particular organization if they have the proper role in that organization.

Summary information about the assessment is provided at the top of the Assessment Dashboard including the assessment name, control framework, scoring method, start date, due date, open/closed status, organization, industry, and the implementation group that is currently selected.  The Implementation Group for the assessment can be changed with the drop down, which will change the applicability of Sub-Controls in the assessment (see the exclamation mark in the circle by the Implementation Group drop down for more information).  Below that is a row of summary statistics including the assessment average, the industry average (if the CSAT Pro instance is opted in), the percentage of the assessment that is completed, and the percentage of the assessment that is validated.  Below that is a Control Level Heat Map, which has a color coded block for each CIS Control indicating that Control’s current average.  Clicking on the exclamation mark in a circle icon below that heat map will provide a legend that maps the colors to the score ranges.  Clicking on any of the Control blocks will go to the Control View for that CIS Control.

Below that information are several graphs.  Clicking the information icon beside a graph title (the blue circle with letter 'i' in it) will display in-tool information about the graph.

-	CIS Controls Implementation Average graph - This is a bar graph showing the assessment's validated Control averages (and corresponding industry Control averages if opted in). The first bar for each Control represents the assessment's current average for that Control. Each Control average is calculated by finding the sum of the scores of the Sub-Controls/Safeguards in that Control that are both applicable and validated, and then dividing that sum by the total number of Sub-Controls/Safeguards in that Control that are both applicable and validated. When opted in to the Industry Average Service, this chart also has:
    - A second bar for each Control representing the industry average for that Control.
    - The "Number of Organizations Used in this Industry Average" at the bottom.<br/>

	<br/>The bars are colored according to the heat map coloring scheme for the scores. Hover over any bar for a tool tip with the exact average.<br/>

-	Monthly Assessment Average graph – This line graph has a data point for the assessment average score per month for the current assessment in blue. If opted in to the Industry Average Service, a second line, in red, displays the industry average for that month. The snapshot for the previous month is generally taken on the first day of the following month if the CSAT Pro instance is up and running (for instance, the August data would typically appear on the 1st day of September). Hover over dots for a tool tip with the average score.
-	Implementation Group Averages graph – This bar chart has one bar for each Implementation Group as defined in the CIS Controls. The X-axis represents each Implementation Group: IG-1, IG-2, and IG-3. The Y-axis represents the average scores, 0 - 100. Scores for the bars are calculated by averaging the validated scores of the Sub-Controls/Safeguards in each Implementation Group (applicable or not). The scores for these bars use an exclusive definition for each IG when determining the score – thus, the IG-3 bar does not factor in Safeguards that are in IG-1 or IG-2. Unlike the other graphs, this graph does not take the assessment's Safeguard applicability into account; the IG-3 bar represents the assessment's average of the IG-3 Safeguards, regardless of whether this assessment has some or all of those Safeguards marked as Not Applicable. For example, CIS Controls v7.1 IG-1 has 43 Safeguards. If one of those 43 Safeguards is scored at 100% (and validated), while all the rest are scored at 0, then the calculation would be 100/43 = 2.3. Then this average is rounded to 2. Hover over bars for a tool tip with the average score.

At the top right of the Assessment Dashboard, users can export reports and close/reopen an assessment.  Depending on the user's role in the organization, the following buttons can be found there:

- Copy Assessment – Only Organization Admins have access to this button.  Copying an assessment will create a new assessment in that organization containing the data from the original assessment.  The new assessment’s name will be of the form “originalAssessmentName Copy”.  The Start Date of the new assessment will be set to the date it was copied.  The new assessment will be Open (even if the original assessment was Closed).  The other assessment-level information for the new assessment will match the original assessment (Control Framework, Scoring Method, Due Date, and Implementation Group).  Task-level information will also be copied including scores, assignments, workflow status, discussion comments, task history, task applicability, and custom tags.  The assessments are not linked after the copy – so changes to either the original or the copy are independent and will not affect the other assessment.  The Copy Assessment functionality can be used in several ways:  
    - An assessment could be closed at the end of an assessment period and a new assessment for a new time period can be started using an existing assessment’s data.
    - An assessment template can be created that is used to generate other assessments.  For instance, maybe an organization wants to assess against IG1 plus a few additional Sub-Controls, and minus a few other Sub-Controls.  A template could be created with the desired Sub-Controls set to Applicable (and kept unscored), and then the working assessments could be created as copies of that template assessment.
- Close Assessment/Reopen Assessment - Only Organization Admins have access to this button.  If the assessment is currently open, the "Close Assessment" button will allow the Organization Admin to lock the assessment, preventing further edits.  If the assessment is currently closed, the "Reopen Assessment" button will allow the Organization Admin to unlock the assessment, allowing edits once again.
- Export CSV - Both Organization Admins and Full Users have access to this button.  This button allows users to export a Safeguard level spreadsheet in CSV format.  This report contains information similar to what is found in the Assessment Summary tab.  By default, this export will only contain the Safeguards that have been scored so far; the Export Filtered CSV functionality on the Assessment Summary page can be used to customize which Safeguards are exported to CSV.
- Export Board Level Slides - Both Organization Admins and Full Users have access to this button.  This button allows users to export a set of slides containing high level assessment summary information in pptx format.  This report contains information and graphs from the Assessment Dashboard, as well as the Assessment History graph from the Organization Info page.

####Assessment Navigation Menu####
At the top left of many assessment pages, users can select different assessment tabs to switch between the Assessment Dashboard, the Assessment Summary, the Assessment Event Log, the Task Calendar, Assigned Tasks, Pending for Validation Tasks, and the Control Views. Users with a Basic User role in the organization will have a limited Assessment Navigation Menu that only includes navigation back to their My Assigned Tasks list.

####Assessment Summary Page####
The Assessment Summary tab takes users to a listing of the assessment’s Sub-Controls showing task status information including its number, title, and whether it is applicable, assigned, completed, and/or validated.  Clicking on a task’s number or title will take you to the Task View for that task.  Hovering over a green check mark on this page will display the user who performed the action.  Hovering over the check marks in the Assigned column will also display the due date for the task.  Users can switch to the other Assessment tabs in the upper left of the Assessment Summary page.

By default, the Assessment Summary page displays all the tasks in the assessment.  This full list can be filtered to display a particular subset based on various filtering criteria.  Filtering criteria can include task applicability (applicable or not), assignment status (assigned or not), workflow status (incomplete/completed/validated), score, asset type, security function, custom tags, or Implementation Group.  Multiple criteria can be combined into one search; for instance, a user could search for all Sub-Controls that are in Implementation Group 1 and are currently unassigned.  To filter, press the Filter button to display the filtering criteria options, select the desired value from the corresponding drop down for any desired filters, and then press the blue Search button.  The tasks listed below will then update according to the selected filter criteria.  Pressing the Clear button will clear all of the filters and show all tasks in the assessment.

The Assessment Summary page also allows bulk actions to be performed on tasks in the assessment.  On the far left of the page, there are a series of checkboxes corresponding to each task that is displayed.  There is also a checkbox to the left of the headings that will Select/Deselect All checkboxes.  A bulk action can be performed with following steps:

1) Select the desired tasks using the checkboxes

2) Select the desired action from drop down above the checkboxes.  This drop down is to the left of the “Bulk Edit” button

3) Click the “Bulk Edit” button

4) Depending on the action, a pop-up window may appear allowing you to enter additional information needed for the action.  Enter any needed information and press the Submit button to perform the action

The Bulk Edit actions that are currently available are:

-	Bulk Assign – Using “Assign User” from the Bulk Edit drop down menu, one or more tasks can be assigned.  A pop-up window will be displayed where the user can enter the required information (user to Assign To and the Due Date) along with an optional comment.  After entering this information and pressing Submit, a summary of the assignments will be displayed in a message banner containing information about how many tasks were successfully assigned, how many tasks were reassigned (tasks that were previously assigned), and how many tasks were unable to be assigned (tasks that are Completed, Validated, or Not Applicable cannot be assigned).  A single email will be sent to the Assign To user containing a list of the tasks that they were successfully assigned to; like the singular assign functionality, no email will be sent when users are assigning tasks to themselves.
-	Bulk Applicability Toggle – Using “Toggle Applicability” from the Bulk Edit drop down menu, the applicability for one or more tasks can be set at once.  A pop-up window will be displayed where the user can select the desired applicability for the selected tasks using the toggle (Not Applicable is selected when the toggle is on the left side; Applicable is selected when the toggle is on the right side).  Once the desired applicability is chosen and the user presses the Submit button, the tasks applicability will be updated and a summary message banner will appear to indicate how many tasks were set to the new value and how many were already in the selected state.
-	Bulk Unassign – Using “Unassign User” from the Bulk Edit drop down menu, the assigned users for multiple tasks can be unassigned from those tasks at once.  A pop-up window will appear allowing the user to either press the Submit button to proceed with the unassignment, or to press the Close button to cancel without updating the tasks.  After the user clicks the Submit button, a message banner will appear to indicate the results including how many tasks were successfully unassigned, how many did not have an assigned user prior to this bulk action, and how many could not be unassigned (asks that are Completed/Validated or that are Not Applicable cannot be unassigned). 


####Event Log####
The assessment’s Event Log tab displays a history of events for that assessment.  Entries are currently created for events such as blank assessment creation, importing an assessment from a file, assessment closing/reopening, and changes to the assessment’s Implementation Group.  Each log entry includes the user who performed the action and the date/time of the action.  Users can switch to the other Assessment tabs in the upper left of the assessment Event Log page.

####Calendar####
The assessment’s Calendar tab displays a calendar of tasks by due date.  All tasks in the assessment that have an assigned due date will be displayed on the day that task is due.  Hovering over a task on the calendar shows the task number, title, Assigned To user, due date, Assigned By user, Completed By user, and Validated By user.  The tasks also have checkmarks to indicate their status in the workflow – a double checkmark preceding the task indicates the task has been validated, a single checkmark indicates the task has been completed but not validated, and no checkmark indicates that the task has not yet been completed.  The tasks in the calendar are clickable; clicking on one will take you to the Sub-Control View for that task.  If a day has more tasks on it than can be displayed, a “+# more” indicator will be there (where # is replaced by the number of undisplayed tasks); clicking on the “+# more” indicator will display all of the tasks for that day.  The calendar view can be shifted among monthly, weekly, and daily views with the buttons in the upper right.  The arrows in the upper left will let you move forward and backward in time; the single arrow by a single month, week, or day depending on the current view; the double arrows by a full year.

####Control View####
The Control View can be reached by clicking on a Control block in the Control Block Heat Map on the Assessment Dashboard, or by clicking on the “Show all safeguards” link from the Safeguard View, or by selecting a Control from the Assessment Navigation Menu.  This view provides the Control title and description.  It has the overall Assessment Average, but it also has Control level summary statistics including the Control Average, the Industry Control Average (if subscribed), the percentage completed for the Control, and the percentage validated for the Control.  Below that, it lists all of the Sub-Controls for that Control.  Each of these can be expanded by clicking on the Sub-Control number/title, which will show the Sub-Control View for that Sub-Control.  Users can navigate to the Next or Previous Controls using the buttons at the top.

####Safeguard View / Sub-Control View / Task View####
The Safeguard View (also referred to as the Sub-Control or Task View) provides the number and title of the Sub-Control which can be used to collapse or expand that Sub-Control.  To the right of the title is the Implementation Group for that Sub-Control (IG-1, IG-2, or IG-3) and an applicability toggle to indicate whether the Sub-Control is applicable or not for the assessment.

Below the Sub-Control title bar is the Sub-Control number, title, and description.

#####Sub-Control View - Left Side#####
On the left side of the Sub-Control View, there is a drop down to score the Sub-Control; new scores are automatically saved when selected in this drop down.

Below that are workflow buttons.  The buttons available vary as different actions are performed.  These buttons include:

-	Assign User – This button brings up the Assign User pop-up that allows a user to be selected, a due date to be provided, and an optional comment to be included.  This Sub-Control will be assigned to that user with the provided due date.  This task will then appear in a user’s “My Assigned Tasks” for that assessment.  This will generate an email to the assigned user (unless the assignee is the same user as the assignor) along with an optional comment.
-	Re-Assign User – This is essentially the same as the Assign User button, but it appears after a task has been assigned.  This button lets the assigned user and/or due date for the task be changed.  This will generate emails in the same manner as Assign User.
-	Complete – A task can only be completed after it has been scored.  The Complete button removes the task from the Assigned Task list for the assigned user and makes the task ready for validation; a completed task will appear in the Assigned By user’s “My Pending for Validation Tasks” list.  The task can be reviewed and either sent back or validated.  If an unassigned task is completed, the task is assigned to the completing user.  Once completed, the Assign/Re-Assign buttons disappear for the task.  This will generate an email to the Assigned By user that the task is ready to be validated (unless the completing user is the Assigned By user).
-	Send Back – Once a task is completed, the Send Back button becomes available.  If a task is sent back, it will return to the Assigned Tasks list for the Assigned To user and be removed from the Pending for Validation Tasks list for the Assigned By user.  This will generate an email to the Assigned To and Completed By users (no email will be sent to the user who is sending the task back) and can include an optional comment.
-	Validate – Once a task is completed, the Validate button becomes available.  If a task is validated, it will lock the scoring drop down and the ability to upload evidence files.  This also removes the task from the Pending for Validation Tasks list for the Assigned By User.
-	Revert Validation – Once a task is validated, the Revert Validation button becomes available.  This button will unlock the scoring drop down and the ability to upload evidence files.  It will also add the task back to the Pending for Validation Tasks list for the Assigned By User.

In addition to the task’s current stage in the workflow, button availability also varies with the current user’s role in the organization.  Organization Admins and Full Users for that organization can perform all of the workflow actions listed above, even for tasks to which they are not directly assigned.  

Basic Users in the organization are more limited.  Basic Users will only have access to the specific tasks that they have been assigned.  For a task assigned to a Basic User, that Basic User will be able to score that task, complete that task, upload/download/delete evidence files for that task, and toggle the task’s applicability.  A Basic User cannot send back, validate, or revert validation for a task.

A task that is Not Applicable cannot be scored and its workflow buttons will not be available.  Task applicability can be initially set by the Implementation Group selected for the assessment.  The applicability for individual tasks can be adjusted with the Applicability toggle for that task by users with the appropriate role.

Evidence files can be uploaded to the task with the Upload Evidence button, which is next to the workflow buttons.  This button will display an Upload Evidence pop-up that will allow the user to browse to an evidence file that they wish to upload to that task.  The Maximum file size for uploads is currently 15MB.  Uploaded evidence files are compressed into a zip format.  If evidence files have been uploaded to the task, there will be an Evidence section below the workflow buttons.  This section will display a list of the evidence files that have been uploaded to the task so far.  Clicking on the filename for the evidence file will download that evidence file.  Clicking on the trash can icon next to an evidence file name will delete the evidence file.

Below the workflow buttons and Evidence section (if present) are the Discussion and History sections.  Users can switch between these by clicking the appropriate tab:  

-	The Discussion section displays comments that users have entered for the task.  A user can enter a comment with the “Add Comment” button, and that comment will be annotated with the user who submitted it and the date/time it was submitted.  Users can also delete their own comments using the trash can icon next to the comment; users cannot delete comments submitted by other users.
-	The History section serves as a log for that task’s events.  It provides details on the action that occurred, which user performed the action, and when that action took place.

#####Sub-Control View - Right Side#####
On the right side of the Sub-Control View you can find additional information on the Sub-Control including:

- Score - the Sub-Control’s current score converted to a 0 – 100 scale
- Mappings – This section displays mappings to other frameworks.  A block will appear for each mapping indicating the framework and identifier within that framework to which this CIS Safeguard is mapped.  Users can click these blocks to pop-up additional information on that mapping.  Please refer to the spreadsheets at [CIS Controls Mappings](https://workbench.cisecurity.org/community/94/files) for additional information on these mappings (such as more detail on the relationship between the mapped controls) as well as mappings to other frameworks.  Users will only see those mappings that they have turned on in their Mapping Preferences, which is available in their User Menu.  Currently, CSAT Pro has the following mappings available:
    - CIS Controls v7.1 to NIST 800-53 Revision 4 Low Baseline, the NIST Cybersecurity Framework (CSF), and PCI DSS v3.2.1
    - CIS Controls v8.0 to NIST 800-53 Revision 5 Low Baseline and the NIST Cybersecurity Framework (CSF).
- Custom Tags – This section displays existing tags for the task and allows the user to add new ones. There is an input box where the user can enter new tags; as the user starts typing in this box, it will autopopulate existing tag options that match the characters typed so far.  Once the desired tag has been typed, hitting the enter key will apply that new tag to the task.  Tags are case insensitive (so ABC will be treated the same as abc).  A list of the tags that have already been applied to that task is displayed; a tag can be removed from that task by clicking the ‘x’ at the right of the tag in question.  Custom tags can be used in the Assessment Summary page as a filter to display all tasks that have a particular tag.
- Asset type
- Security function – This section displays the security function identified for the CIS Sub-Control.  These are based on the functions used in the NIST Cybersecurity Framework: Identify, Protect, Detect, Respond, and Recover.

As workflow actions are performed such as assigning the task, completing the task, and validating the task, additional information will be populated on the right including the Assigned To and Assigned By users, the Assigned Date and Due Date, and the Completed By and Validated By users.  Clicking on a user name in this section will navigate to that user’s profile.

A remind action (a bell icon) will be available beside the Assigned To user when the task has been assigned but not yet completed.  Similarly, a remind action will be available beside the Assigned By user when the task is completed but not yet validated.  Clicking on either of these remind icons will bring up a pop-up where an optional comment can be entered; clicking “Send Reminder” in that pop-up will then email the user listed on that line to remind the user to either complete or validate the task.

An unassign action (a trash can icon) will be available beside the Assigned To user when a task has been assigned but not yet completed.  Clicking on the unassign icon will prompt the user with a confirmation pop-up.  If confirmed, this action will remove the Assigned To user, the Assigned By user, the Assigned Date, and the Due Date information from that task, returning the task to an unassigned state.


####Assigned Tasks List####
A user’s Assigned Tasks list for an assessment is the list of tasks that have been assigned to that user that have not yet been completed.  A user will have a distinct Assigned Tasks list for each assessment that the user has access to.  The Assigned Tasks list can be reached from the Action column of an assessment’s row on both the My Assessments section on the Home page and the Assessments section of an Organization Info page, or from the Assessment Navigation Menu at the top of an assessment.  The icon shows a person with a gear; hovering over the icon will indicate the number of tasks currently assigned to the user in that assessment.  If the user does not have any assigned tasks for an assessment, the icon will not appear.  Clicking the icon will take the user to the “My Assigned Tasks” page for that assessment, where users can view a list of their assigned tasks for the assessment along with which user assigned the task and when it is due.  Clicking on a task from the list will take the user to the Sub-Control view for that task where the user can complete the task, or step to the Next or Previous task in the list with the buttons at the top.  Once the user completes the task, it will be removed from the Assigned Tasks list and will appear in the Pending for Validation list for the user who assigned the task.

####Pending for Validation Tasks List####
A user’s Pending for Validation Tasks list for an assessment is the list of tasks for which the user is the assignor, that have been completed, but have not yet been validated.  A user will have a distinct Pending for Validation Tasks list for each assessment that the user has access to.  The Pending for Validation Tasks list can be reached from the Action column of an assessment’s row on both the My Assessments section on the Home page and the Assessments section of an Organization Info page, or from the Assessment Navigation Menu at the top of an assessment.  The icon shows a person with a checkmark; hovering over the icon will indicate the number of tasks that are currently pending for validation for that user in that assessment.  If the user does not have any pending for validation tasks for an assessment, the icon will not appear.  Clicking the icon will take the user to the “My Pending for Validation Tasks” page for that assessment, where users can view a list of their pending for validation tasks along with which user the task was assigned to and which user completed the task.  Clicking on a task from the list will take the user to the Sub-Control view for that task where the user can either send the task back or validate the task, or step to the Next or Previous task in the list with the buttons at the top.  If the user sends the task back, it will be added to the Assigned Tasks list for the user the task is assigned to.  The task will be removed from the user’s Pending for Validation Tasks list once the task is either sent back or validated.

####Edit Assessment####
Users with an Organization Admin role for an assessment can edit the name, start date, and due date of that assessment.  The Edit Assessment page can be reached from the Action column of an assessment’s row on either the My Assessments section on the Home page or the Assessments section of an Organization Info page.  On the Edit Assessment page, users can update the desired fields and click Save to update the information for that assessment.

####Delete Assessment####
Users with an Organization Admin role for an assessment can delete the assessment.  Assessments can be deleted using the trash can icon in the Action column of an assessment’s row on either the My Assessments section on the Home page or the Assessments section of an Organization Info page.  Clicking this icon will result in a confirmation pop-up; if the Delete button is pressed in the Delete Assessment confirmation pop-up, the assessment and all of its data will be deleted.  Warning: this action cannot be reversed.



Scoring
------------
CIS CSAT Pro currently uses a Simple Scoring Method for CIS Controls assessments.  This means that each CIS Sub-Control can be assigned a whole number score of 1 through 5.  Reference ranges are provided with each option; for instance, if an organization has a Sub-Control implemented on 50% of their systems, they could select a score of 3 which has a reference range of “41 – 60%”.  These reference ranges are only intended as a convenience and are not intended to be a hard and fast scoring requirement.  If an organization has its own way of scoring on a 1 – 5 scale that differs from the reference ranges, they are free to ignore the reference ranges and select the 1 – 5 scores that fit their scoring methodology.  The provided scoring options with reference ranges are:

-	1 (0-20%)
-	2 (21-40%)
-	3 (41-60%)
-	4 (61-80%)
-	5(81-100%)
-	Not Applicable
-	Not Available

Note that the “Not Applicable” and “Not Available” options will be treated, from a scoring perspective, the same as if the “1 (0-20%)” option were selected, which will yield a percentage score of 0 for that Sub-Control.

The 1 – 5 Sub-Control score is converted to a percentage with the formula: (Score – 1) * 25.  This percentage score is displayed to the right side of the Sub-Control View.

The scoring in CSAT Pro focuses on validated Sub-Controls.  Thus, a Control Average score is the average of the Sub-Controls under that Control that are both applicable and validated.  For instance, if only one Sub-Control in a Control has been validated with a score of 100, and there are two applicable Sub-Controls under that Sub-Control (including the one that has been validated), the Control Average will show 100, while the Control Validated percentage will only show 50.  It is this validated Control Average that is used on the Assessment Dashboard for the Control block heat map and the CIS Controls Implementation Graph.

The overall Assessment Average is generated by averaging the validated Control Averages from applicable Controls.  A Control is considered applicable if at least one of its Sub-Controls is applicable.

Industry Average Service
------------
By default, CIS CSAT Pro instances are opted out of the Industry Average Service; this means that CSAT Pro does not share any assessment data from the user’s on-premises instance back to CIS by default.

Users can choose to opt in to the Industry Average Service; see the [System Integrations](#system-integrations-page) section for instructions on how to opt in. Users who do choose to opt in will receive industry average information for their selected industry or industries that will be displayed throughout the CSAT Pro instance, providing richer information in assessment dashboards and graphs. This includes an assessment level industry average and Control level industry averages; Safeguard level industry averages are not provided. Opting in to the Industry Average Service also means that users will share anonymous assessment data (CIS Safeguard scoring data) from their CSAT Pro instance securely with CIS over a TLS v1.3 connection. Sharing this anonymous data helps improve CIS’s industry average data set.

Users who choose not to opt in will not receive the industry average data feed. Once opted in, you may choose to opt out of sharing your data at any time. If you opt out, the industry average subscription feed will also terminate.

While the industry average information can be useful as a point of comparison for your organization, it should not be used to determine when your organization has reached an acceptable level of maturity in your implementation of the CIS Controls; the decision of what is an acceptable level of maturity for the CIS Controls implementation for your organization should be made only after performing a thorough risk analysis for your organization. The industry average information provided is based on the self-assessed industry identification and self-assessed Safeguard scoring of CSAT users; as such, this information is provided as a point of reference, and should not be the basis for organizational decisions.

By opting in to the Industry Average Service, you and your organization agree to share anonymous assessment scoring data with CIS.

There are separate industry averages based on which version of the CIS Controls (v7.1 or v8.0) is specified for the assessment.

CIS Controls
------------
The CIS Controls are a prioritized set of actions that collectively form a defense-in-depth set of best practices that mitigate the most common attacks against systems and networks. The CIS Controls are developed by a community of IT experts who apply their first-hand experience as cyber defenders to create these globally accepted security best practices. The experts who develop the CIS Controls come from a wide range of sectors including retail, manufacturing, healthcare, education, government, defense, and others.

The CIS Controls v8.0 consists of 18 top-level Controls that serve as categories to house 153 Safeguards.  Each CIS Safeguard is a specific action that can be implemented or activity that can be performed to improve an organization’s cyber defense program.  The previous version of the CIS Controls, v7.1, consists of 20 top-level Controls that serve as categories to house 171 Safeguards.

To download the CIS Controls and see the other companion resources that are available, please visit the [CIS Controls](https://www.cisecurity.org/controls/).

### Implementation Groups ###
In v7.1 of the CIS Controls, Implementation Groups (IGs) were introduced.  Implementation Groups put the CIS Safeguards (known as CIS Sub-Controls prior to CIS Controls v8) into 3 groups to help organizations prioritize which Safeguards to implement first.  CIS recommends that all organizations implement IG1, as the IG1 Safeguards represent essential cyber hygiene.  Based on the resources available to the organization, as well the criticality of the data and services that the organization needs to protect, the organization can determine whether they should also implement additional Safeguards from IG2 and IG3.  Each Implementation Group builds on the lower Implementation Groups; thus an organization implementing IG2 should also implement IG1, and an organization implementing IG3 should implement all three Implementation Groups.

The following are some general guidelines to help organizations determine which Implementation Groups are right for them:

####IG1####
Organizations with limited resources where the sensitivity of data is low will need to implement the Safeguards that typically fall into the IG1 category.

####IG2####
Organizations with moderate resources and greater risk exposure for handling more sensitive assets and data will need to implement the IG2 controls along with IG1. These Safeguards focus on helping security teams manage sensitive client or company information.

####IG3####
Mature organizations with significant resources and high risk exposure for handling critical assets and data need to allocate the Safeguards under the IG3 category along with IG1 and IG2. The Safeguards that help reduce the impact targeted attacks from sophisticated adversaries typically fall into IG3.

A useful reference that lists all of the CIS Safeguards and which Implementation Group they belong to (for CIS Controls v7.1) can be found at: [CIS Controls v7.1 Implementation Groups Reference](https://www.cisecurity.org/white-papers/cis-controls-v7-1-implementation-groups/).
