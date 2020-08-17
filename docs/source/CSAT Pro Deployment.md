![](img/CIS_CSAT_Pro_RGB.png)


# CIS CSAT Pro Deployment Guide#
----------
##Introduction ##
CIS CSAT Pro is a web application built using the Grails framework. The application uses a graph database known as Neo4j. The documentation below describes how to deploy CIS CSAT Pro on **Windows Server 2019 (64 bit)** operating systems, as well as **Ubuntu 18.04** operating systems, whether GUI based, or server based. The  installer for CIS CSAT Pro is an all-in-one package, so it will set up the application, database, and services for you. We use an embedded version of <b>Tomcat 9</b> that comes packaged with Grails, and we also supply <b>Java 11</b> that is used for the <b>Neo4j 3.5 database</b>, as well as CIS CSAT Pro.

## System Recommendations ##
While there is no strict requirements associated with CIS CSAT Pro, we do have some recommendations based on what we have tested locally. We do recommend to have adequate size of disk space, as we have configured the installer to install and set up the Neo4j database for the application on the same server as CIS CSAT Pro.

Out test environment used an AWS t2.xlarge instance, which has:

 - 16GB RAM
 - 4 quad core vCPUs

The operating system CIS used when testing CIS CSAT Pro was Windows Server 2019 and Ubuntu 18.04.

### Web Browser###
The CIS-CAT Pro Dashboard officially supports **Google Chrome** web browser. Other browsers may also work but may produce unexpected behavior.

<a name=""></a>
## Installing CIS CSAT Pro##
<b>This section will do a step-by-step guide on how to deploy CIS CSAT Pro, as well as the Neo4j database.</b>


 - Locate latest version of CIS CSAT Pro in the Downloads section of [CIS WorkBench](https://workbench.cisecurity.org/).
 - Download the CIS CSAT Pro Unix bundle from [CIS WorkBench](https://workbench.cisecurity.org/).
 - Extract the bundle on the machine you are using to host CIS CSAT Pro.
 - Execute the CIS CSAT Pro Installer (`CSAT_Pro_unix_Installer.sh`) as root or user that has root privileges.

####Welcome####
First, you will be brought to a welcome screen, stating you are installing CIS CSAT Pro.

####Select Destination Directory####
Select the location of where the CIS CSAT Pro application, as well as Neo4j database, and included version of Java will be installed.

####Select Configuration and License Directories####
On this screen, you will be selecting the configuration and license files needed for the application. You can find out more information on how to get these files in the [Obtaining Configuration Files](#obtainingConfigFiles) section in the deployment guide. We ask that these files are kept in the same directory with each other. If they aren't, the application will not be able to run.

The first file to be selected is the <b>Integration Configuration File</b>. Please enter the path to the <u>dxlclient.config</u> file, including the file name.


The next file to be selected is the <b>License Key</b> file. Please enter the path to the <u>license-key.xml</u> file, including the file name.

####Email Configuration####
CIS CSAT Pro must be able to connect to and utilize a valid SMTP server in order to send email messages. CIS CSAT Pro utilizes the Grails mail plugin for email communication.
Along with the default sender email address, CIS CSAT Pro's mailing configuration must also include connection to a valid SMTP server in order to correctly distribute the "forgot password" messages. Numerous SMTP services exist, such as Gmail, Hotmail, Amazon SES, or in-house SMTP services available through corporate emailing technologies, such as Exchange. CIS CSAT Pro can support these SMTP servers, as long as the connection information entered below is correct. By default, the plugin assumes an unsecured mail server configured at `localhost` on `port 25`. However, this can be modified in the email configuration screen.

####Set up TLS Configuration####
This screen is to set up TLS configuration. This screen has 3 options as to how you want to set up TLS for the CIS CSAT Pro application. 

Please allow network traffic through the port specific to which option you select. We have listed the default port numbers for each option below.

----------


By default, we select generating a self-signed PKCS12 certificate, to allow for HTTPS protection to the application. Here we ask for 2 fields to be filled out, so we can generate the certificate for you. The default port for this option is **443**.

 - <b>Alias</b> - This will be the alias, as well as the key file name.
 - <b>Keystore Password</b> - This will be the password for access to the certificate.


----------


The second option is if you already have a certificate(self-signed or a certificate authority) that you would like CIS CSAT Pro to use. The default port for this option is **443**.

 - **Certificate** - File path to the existing certificate.
 - **Alias** - Alias name for the existing certificate.
 - **Keystore Password** - Keystore password for the existing certificate.
 - **Key Password** - Key password for the existing password.


----------


The third option is our least recommended option in terms of security. This will allow for only HTTP requests, which will only have unencrypted communication to CIS CSAT Pro. By default, the port for this option is **8080**.

####Installation####
In this section, the installer will be extracting all necessary files into the installation directory chosen. This process may take a few minutes.

####Set Up Database Admin####
On this page, we need to set up the password for the Neo4j database admin user. By default, the user name is `neo4j`. The password has some requirements, which are: 1 letter, 1 number, 1 special character `!@#$%^&`, and must be 8-64 characters long.

####Installing and Starting CIS CSAT Pro####
Here, the installer is starting up the Neo4j service, and is creating and starting the CIS CSAT Pro service. This can take a few minutes.

####Finished####
At this point, the installer has finished setting up and CIS CSAT Pro is starting. It may take a few minutes for the application to be accessible. From here, you can check out the [User Guide]("../csat_pro_user_guide") on how to log in and use CIS CSAT Pro.

<a name="obtainingConfigFiles"></a>
## Obtaining Configuration Files##
Your organization’s license file and configuration files can be obtained through CIS WorkBench [CIS WorkBench](https://workbench.cisecurity.org/).  After logging into WorkBench, your organization’s Company Manager in WorkBench can click on their company information (reachable from the down arrow near the user’s username in the upper right corner of the page and then clicking on the company’s name in that menu).  On the company information page, click on “Licenses” on the right.  This will take the Company Manager to a page that shows the company’s Active License Keys.  The Company Manager should then download the license bundle.  If this page says “There are no active license keys for this organization”, then the Company Manager will need to contact [CIS Support](https://www.cisecurity.org/support/). 

Once downloaded, you should unzip the files.  Two of the files that will be extracted from this bundle are the dxlclient.config file and the license-key.xml file.  During the installation process, you will browse to these files when prompted by the installer as described above in the Select Configuration and License Directories section.
