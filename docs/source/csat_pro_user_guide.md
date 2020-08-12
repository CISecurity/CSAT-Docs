![](img/CIS_CSAT_Pro_RGB.png)

CSAT Pro User Guide
=====================================

Introduction
------------
The CIS Controls Self Assessment Tool (CSAT) is a web application that helps organizations track their implementation of the CIS Controls down to the Sub-Control level.  CSAT provides a workflow to facilitate collaboration among team members as they self-assess the organization’s CIS Controls implementation.

A free, CIS-Hosted version of CSAT was released in early 2019 and is available at https://csat.cisecurity.org/

SecureSuite Members also have access to an on-premises version, CSAT Pro, which this User Guide describes.  CSAT Pro gives organizations greater control by allowing them to setup and host instances of CSAT in their own environment.


License
------------
Access to CSAT Pro requires a SecureSuite Membership.  Additional information on SecureSuite Membership can be found at https://www.cisecurity.org/cis-securesuite/


Getting Started
------------
Information on setting up a CSAT Pro instance can be found in the Deployment Guide.


The Basics
------------
This section describes the basic CSAT Pro concepts including users, organizations, and assessments, as well as how they relate to each other.

### Users, Privileges, and Roles ###
Users have two primary attributes that determine which actions they can perform in CSAT Pro when interacting with the tool as a whole, as well as the organizations, assessments, and other users within the tool.  One of these attributes is the user’s System Profile, and the other is the user’s set of Organization Roles.

#### System Profiles ####
Each user is assigned a system profile, which determines the user’s access level to the tool as a whole.  There are two system profiles available:

- System Admin: Users with the System Admin system profile have full privileges to the tool, including the ability to create Top-Level Organizations and edit other users in User Management.
- Basic: Users with the Basic system profile have limited access to the tool and are restricted from actions such as creating Top-Level Organizations and accessing User Management page.

#### Organization Roles ####
Once organizations are created in the tool, users can be assigned roles in those organizations.  The role is an affiliation between the user and the organization that determines what actions the user can perform on the organization, the organization’s assessments, and the organization’s users.  There are three Organization Roles available: 

- Admin: An Organization Admin has full access to the organization, the assessments in that organization, and control over the organizational roles for users affiliated with that organization.  An Organization Admin can create Sub-Organizations under that organization as well, and can create new assessments for the organization as well.
- Full User: A Full User has full access to work on existing assessments in the organization.  A Full User cannot create new assessments, cannot create Sub-Organizations, and cannot edit user Organization Roles for the organization.
- Basic User: A Basic User has limited access to the organization’s assessments and can only view/complete tasks that have been directly assigned to that user.  A Basic User cannot create new assessments, cannot create Sub-Organizations, and cannot edit user Organization Roles for the organization.

A user can be assigned a different organizational role for each organization and sub-organization in CSAT Pro, though a user does not need to have a role assigned for each organization.  For example, User A might be an Organization Admin in Organizations Z and Y, might be a Full User in Organization Q, and might have no role at all in Organizations E and F.  User B might only administer the CSAT Pro instance and not need to work on any assessments, so User B might not have any Organization Roles assigned.

Note that Organization Roles and System Profiles are independent of each other.  A user with a Basic System Profile can have an Organization Admin role in an organization.  A user with a System Admin System Profile can have a Basic User Organization Role in an organization.

### Organizations ###
Multiple organizations can be created in a CSAT Pro instance.  Organizations are organized into organization trees, each of which consist of a Top-Level organization and zero or more Sub-Organizations under that Top-Level organization.  Users with the System Admin system profile can create Top-Level organizations.  Once a Top-Level organization is created, users assigned the Organization Admin role in that organization can create Sub-Organizations under that Top-Level organization.  In turn, the Organization Admins of those Sub-Organizations can create additional Sub-Organizations under those Sub-Organizations.

### Assessments ###
Organization Admins can create assessments in the organizations that they administer.  Each organization can contain zero or more assessments.  A user’s access to an organization’s assessments is determined by the Organization Role the user has for that organization.

Each assessment will be open or closed.  Assessments begin “open” which means that users in that organization can work on those assessments based on their Organization Role.  When an assessment is completed, an Organization Admin can close the assessment.  A “closed” assessment can still be viewed, but it cannot be edited.  An Organization Admin can re-open a closed assessment as needed.


Pages and Actions
------------
This section contains a description of the pages within CSAT Pro and which actions can be performed on those pages.



### Home Page ###
Upon logging in to CSAT Pro, a user will arrive at the Home page.  This page provides access to organization and assessment information that is specific to the current user.  You can return to the Home page by selecting “Home” from the top menu at any point.  The Home page contains the following sections:

#### My Organizations ####
The My Organizations section displays the Organization Name, Industry, and the current user’s Organization Role for any organizations in the CSAT Pro instance to which the current user has an organization role.  Each organization in this list is clickable and will take you to the Organization Info page for that organization.  If the current user is a System Admin, this section will also contain a “Create Organization” button that allows the user to create new Top-Level Organizations.
#### My Assessments ####
The My Assessments section displays the assessments associated with the organizations in the My Organization section.  The following information is displayed for each assessment in the list - Assessment Name, Assessment Template, Start Date, Due Date for open assessments (or Closed Date for closed assessments), Organization, and Action icons for any actions that the current user is permitted for the particular assessment (action icons can take you to the assessment’s dashboard, a list of tasks to complete, or a list of tasks pending for validation if applicable).  There is an Open tab and a Closed tab that allow the user to toggle between open and closed assessments.
#### Assessment Templates ####
An Assessment Template is the combination of a Control Framework and a Scoring Method.  The Assessment Template section lists the Assessment Templates available in this CSAT Pro instance and describes the Control Framework and Scoring Method for each.  CSAT Pro currently has the CIS Controls v7.1 with Simple Scoring available.  


### Top Menu ###
The Top Menu is present at the top of all pages in CSAT Pro.  From right to left, the Top Menu offers the following options:

####Home Button#### 
The Home button returns the user to the Home page.

####Support Center####
The Support Center menu has links to the CSAT Pro Deployment and User Guides, to the CIS Product Support portal (where you can submit a support ticket), to the CIS WorkBench Support Center (which has information and recorded webinars on a variety of CIS topics), and to the main CIS website.

####System Admin Menu####
System Admin users will have a gear icon to represent the System Admin menu which can take them to the User Management or System Integrations pages.  For users with a Basic system profile, the gear icon will not be present.

####User Profile Menu####
Clicking on the user’s username shows a menu that can take the user to the My Profile page.

####Logout####
Logout will log the user out of CSAT Pro.

####License Status####
The License Status symbol shows the status of the tool’s license.  System Admins can click this to go to the License Information page.


### Organization Info Page ###
The Organization Info page has the following sections: 

####Organization Section####
The Organization section displays the Name, Website, and Industry of the current organization.  Organization Admins have “Edit” and “Delete” buttons in this section as well.  The Edit button allows the organization’s Name, Website, and/or Industry to be updated.  The Delete button will remove the organization, as well as all of the organization’s sub-organizations and assessments (so use with caution).

####Sub-organizations Section####
The Sub-organizations Section displays the Organization Name and Industry for sub-organizations of the current organization.  Organization Admins have a “Create Sub-organization” button that will create a new sub-organization under the current organization.  The sub-organizations in this list are clickable and will take the user to the Organization Info page of that sub-organization.

####Active Users Section####
The Active Users section displays a list of the users that have Organization Roles in the organizations.  The icons under the action section allow Organization Admins to change a user’s organizational role or remove the user from the organization (deleting the user’s organization role for the organization).  Note that there is an “Include Sub-organizations” checkbox in the pop-up window for these actions; if this checkbox is selected, the same action will be performed for that user in the sub-organizations of the current organization as well.  Organization Admins also have an “Add Users” button in this section that allows the Organization Admin to create new users in CSAT Pro, or assign an organizational role for this organization to existing users that don’t currently have a role in this organization.

####Assessments Section####
The Assessments section displays a list of the assessments that exist in this organization.  The following information is displayed for each assessment in the list - Assessment Name, Assessment Template, Start Date, Due Date for open assessments (or Closed Date for closed assessments), Organization, and Action icons for any actions that the current user is permitted for the particular assessment (action icons can take you to the assessment’s dashboard, a list of tasks to complete, or a list of tasks pending for validation if applicable).  There is an Open tab and a Closed tab that allow the user to toggle between open and closed assessments.  Organization Admins have buttons to start a new assessment under this organization: “Start New Assessment” (to start a new blank assessment) and “Import Assessment” (to import an assessment from a previously exported Hosted CSAT spreadsheet).

####Assessment History Section####
The Assessment History section shows a graph of the closed assessments for this organization to show how the organization’s assessment scores have changed over time.


### Creating a New Organization ###
Top-level organizations are the start of a new organization tree and can be created by users with the System Admin system profile from the Home page by clicking on the “Create Organization” button.  This button will go to a Create Organization page that lets the user enter the information needed to create the organization.

Similarly, users with an Organization Admin organization role can click the “Create Sub-organization” button from that organization’s Organization Info page.  This button will go to a Create Sub-organization page that lets the user enter the information needed to create the organization.

Each organization/sub-organization is created with the following attributes:

- Name – the name of the organization must be unique within the CSAT Pro instance.
- Website – the organization’s website does not need to be unique
- Industry – the industry is selected from a drop down menu of choices.  If the CSAT Pro instance is opted-in to the Industry Average Service, the industry selection will determine the industry data that is displayed for that organization’s assessments.

The user creating the organization is assigned the Organization Admin role for that organization by default.   That Organization Admin can then add an Organization Role for other users with the “Add Users” button from the Active Users section of that organization’s Organization Info page.


### Creating a New Assessment ###
Organization Admins can create new assessments from the Organization Info page for that organization.  The “Start New Assessment” button goes to a Create Assessment page that lets the user enter the information needed to create the assessment.

Each assessment is created with the following attributes:

- Name – The name for the assessment does not need to be unique
- Due Date – The due date is the desired date to complete the assessment
- Assessment Template – the Control Framework and Scoring Method that the assessment will use.  CSAT Pro currently has the CIS Controls v7.1 with Simple Scoring available.
- Implementation Group – when an Assessment Template to which Implementation Groups apply is selected, an Implementation Group will need to be selected as well.  Implementation Groups apply to CIS Controls templates.

Similarly, the “Import Assessment” button goes to an Import Assessment page that lets the user enter this same information.  The Import Assessment page requires one additional field; the user must use the “Choose File” button to browse to a spreadsheet file.  The selected spreadsheet file must be of the format of those exported from the CIS-Hosted version of CSAT.  A detailed log indicating import successes and warnings will be generated and displayed following the import process.

### System Admin Pages ###
System Admins have several pages available to them that users with a Basic system profile do not.

####License Information Page####
This page is available by clicking on the green “LICENSE IS VALID” symbol in the upper right (or the equivalent red symbol indicating that the license is invalid if that’s the case).  This page shows the path to the license file, the verification type (Online or Offline), and the contents of the license file.

####System Integrations Page####
This page is available by selecting “System Integrations” from the gear icon on the top menu.  The Industry Average Service is the only system integration that is currently available.  Information on the Industry Average Service can be viewed by clicking on the blue question mark icon.  System Admins can choose to opt in with the “Opt In” button if their instance is currently opted out, or they can choose to opt out with the “Opt Out” button if their instance is currently opted in.

Instances that are currently opted in will have the “Test” and “Refresh Industry Averages” buttons available to them.  The “Test” button will verify the instance’s connection to the Industry Average Service and will result in a message in the upper left indicating the results of that test.  The “Refresh Industry Averages” button will initiate a pull of the latest industry average data from the service, and will send any unsent anonymous assessment information from the current instance.

####User Management Page####
This page is available by selecting “User Management” from the gear icon on the top menu.  The User Management page lets System Admins search the users in the CSAT Pro instance and create new users.  

System Admins can either enter the appropriate search criteria (username, first name, and/or last name) to narrow their search, or they can leave these fields empty to search for all users.  The resulting list will display the username, first name, last name, email, and system profile for the users that met the search criteria.  System Admins can use the “Edit User” icon in the Action column to change the user’s information or to disable that user (a disabled user will not be able to log into the CSAT Pro instance).  System Admins may not edit their own user details from this menu, but can instead edit their info with “My Profile” under their username in the top menu.

The “Create User” button allows the System Admin to create a new user.


### Creating a New User ###
Users in CSAT Pro can be created in two ways.  System Admins can create users with the “Create User” button on the User Management page.  Organization Admins can create new users by selecting the “Add Users” button on the Organization Info page for an organization that they administer, and then selecting “Create User” on the resulting page.  In both cases, the following information needs to be entered on the Create User page:

-	Username – usernames are unique to each user; different users cannot have the same username.  A username is set when the user is created and cannot be changed later.
-	First Name and Last Name – first and last names do not need to be unique among users and can be updated after user creation.
-	Email – The email address for the user does not need to be unique among users and can be updated after user creation.  This email address will receive notification emails from the tool (such as an email indicating when this user is assigned to a task in an assessment).
-	System Profile – The user’s permission level in the tool (either System Admin or Basic)
-	Password – Users can update their passwords after user creation

Note that the System Profile dropdown may be limited by the creating user’s system profile.  So, an Organization Admin that only has a Basic system profile can only create users with a Basic system profile.

Upon creation, new users do not have any Organization Roles.  Organization Admins can then add the appropriate organizational roles for the user with the “Add Users” functionality.


### Adding a User to an Organization ###
Organization Admins can add a user to an organization by giving that user an Organization Role for that organization.  To do so, the Organization Admin should first select the “Add Users” button on the Organization Info page for an organization that they administer.  Next, the Organization Admin should perform a search to find the user or users that they want to add (by either entering the appropriate search criteria to narrow their search or leaving these fields empty to search for all users).  In the resulting user list, the Organization Admin should select the checkboxes for the user or users to be added.  Then, the Organization Admin should click the “Add Users” button.  This will bring up the “Select Organization Role” pop-up where the Organization Admin can select the desired Organization Role from the dropdown and check/uncheck the “Include Sub-organizations” checkbox, before finalizing the action by clicking “Add Users To Organization”.

If "Include Sub-organizations" is checked, the user's role in each of the selected organization's sub-organizations will be overwritten by the selected role (if that user already had a role in the sub-organization).  If the user doesn't currently exist in a sub-organization, the user will be added to that sub-organization with the selected Organization Role.  The user(s) will only be added (or modified in) sub-organizations for which the current Organization Admin is also an Organization Admin.


### My Profile Page ###
The My Profile page is accessible from the Top Menu, by clicking on the user’s username, and then selecting “My Profile”.  This page lets users view their own user information, update that information (First Name, Last Name, Email Address), and change their password.


### Assessments ###
Once an assessment is created in an organization, there are several pages that let users with a role in that organization work on that assessment and view the data in it.

####Assessment Dashboard Page####
Users with an Organization Admin or Full User role in an organization can view the Assessment Dashboard for that organization’s assessments.  Users can see which Assessment Dashboards they are able to view from the My Assessments section on the Home page; users can click the book icon in the Action column to navigate to the Assessment Dashboard for a particular assessment.  Similarly, users can use the book icon in the Assessments section of the Organization Info page for a particular organization if they have the proper role in that organization.

Summary information about the assessment is provided at the top of the Assessment Dashboard including the assessment name, control framework, scoring method, start date, due date, open/closed status, organization, industry, and the implementation group that is currently selected.  The Implementation Group for the assessment can be changed with the drop down, which will change the applicability of Sub-Controls in the assessment (see the exclamation mark in the circle by the Implementation Group drop down for more information).  Below that is a row of summary statistics including the assessment average, the industry average (if the CSAT Pro instance is opted in), the percentage of the assessment that is completed, and the percentage of the assessment that is validated.  Below that is a Control Level Heat Map, which has a color coded block for each CIS Control indicating that Control’s current average.  Clicking on the exclamation mark in a circle icon below that heat map will provide a legend that maps the colors to the score ranges.  Clicking on any of the Control blocks will go to the Control View for that CIS Control.

Below that information are several graphs: 

-	CIS Controls Implementation Average graph - This is a bar graph that shows current average for each Control (color coded to the same score ranges as indicated by the legend).  If the organization is opted in to the Industry Average Service, each Control will also have a bar indicating the industry average for that Control.  Hovering over a bar will show the Control number, the specific average, and whether that represents this assessment (org average) or the industry average.  Also, if opted in, the number of organizations used for the industry average is provided at the bottom of this graph.
-	Monthly Assessment Average graph – This line graph shows a monthly snapshot of the overall assessment score so that users can see how the assessment score has changed over time.  If opted in to the industry average service, there will also be a separate line representing the industry average.  The snapshot for the previous month is generally taken on the first day of the following month if the CSAT Pro instance is up and running (for instance, the August data would typically appear on the 1st day of September).
-	Implementation Group Averages graph – This graph has a bar for each of the three CIS Controls Implementation Groups (IG1, IG2, and IG3).  The scores for these bars use an exclusive definition for each IG when determining the score – thus, the IG3 bar does not factor in Sub-Controls that are in IG1 or IG2.  Unlike the other graphs, this graph does not take the assessment’s Sub-Control applicability into account; the IG3 bar represents the assessment’s average of the 31 IG3 Sub-Controls, regardless of whether this assessment has some or all of those Sub-Controls marked as Not Applicable.

At the top right of the Assessment Dashboard, users can Close/Reopen an assessment.  Users can also export assessment information there; currently, the “Export CSV” button allows users to export a Sub-Control level spreadsheet.  At the top left of the Assessment Dashboard, users can select the Assessment Summary tab to switch to the Assessment Summary page.

####Assessment Summary Page####
At the top left of the Assessment Dashboard, users can switch to the “Assessment Summary” tab which takes users to a listing of the assessment’s Sub-Controls showing task status information including its number, title, and whether it is applicable, assigned, completed, and/or validated.  Hovering over a green check mark on this page will provide the user who performed the action.  Hovering over the check marks in the Assigned column will also provide the due date for the task.  Users can switch back to the Assessment Dashboard by clicking the “Dashboard” tab in the upper left of the Assessment Summary page.

####Control View####
The Control View can be reached by clicking on a Control block in the Control Block Heat Map on the Assessment Dashboard.  This view provides the Control title and description.  It has the overall Assessment Average, but it also has Control level summary statistics including the Control Average, the Industry Control Average (if subscribed), the percentage completed for the Control, and the percentage validated for the Control.  Below that, it has all of the Sub-Controls for that Control.  Each of these can be expanded by clicking on the Sub-Control title, which will show the Sub-Control View for that Sub-Control.

