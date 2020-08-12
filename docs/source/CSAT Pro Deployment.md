# CSAT Pro Deployment Guide for Linux#
----------
##Introduction ##
CSAT Pro is a web application built using the Grails framework. The application uses a graph database known as Neo4j. The documentation below describes how to deploy CSAT Pro on **Windows 64 bit** operating systems, as well as most **Linux** operating systems, whether GUI based, or server based. The  installer for CSAT Pro is an all-in-one package, so it will set up the application, database, and services for you. We use an embedded version of <b>Tomcat 9</b> that comes packaged with Grails, and we also supply <b>Java 11</b> that is used for the <b>Neo4j 3.5 database</b>, as well as CSAT Pro.

## System Recommendations ##
While there is no strict requirements associated with CSAT Pro, we do have some recommendations based on what we have tested locally. We do recommend to have adequate size of disk space, as we have configured the installer to install and set up the Neo4j database for the application on the same server as CSAT Pro.

Out test environment used an AWS t2.xlarge instance, which has:

 - 16GB RAM
 - 4 quad core vCPUs

The operating system CIS used when testing CSAT Pro was Windows Server 2019 and Ubuntu 18.04.

### Web Browser###
The CIS-CAT Pro Dashboard officially supports **Google Chrome** web browser. Other browsers may also work but may produce unexpected behavior.

<a name=""></a>
## Installing CSAT Pro##
<b>This section will do a step-by-step guide on how to deploy CSAT Pro, as well as the Neo4j database.</b>


 - Locate latest version of CSAT Pro in the Downloads section of [CIS WorkBench](https://workbench.cisecurity.org/).
 - Download the CSAT Pro Unix bundle from [CIS WorkBench](https://workbench.cisecurity.org/).
 - Extract the bundle on the machine you are using to host CSAT Pro.
 - Execute the CSAT Pro Installer (`CSAT_Pro_unix_Installer.sh`) as root or user that has root privileges.

####Welcome####
First, you will be brought to a welcome screen, stating you are installing CSAT Pro.

####Select Destination Directory####
Select the location of where the CSAT Pro application, as well as Neo4j database, and included version of Java will be installed.

####Select Configuration and License Directories####
On this screen, you will be selecting the configuration and license files needed for the application. You can find out more information on how to get these files in the [Obtaining Configuration Files](#obtainingConfigFiles) section in the deployment guide. We ask that these files are kept in the same directory with each other. If they aren't, the application will not be able to run.

The first file to be selected is the <b>Integration Configuration File</b>. Please enter the path to the <u>dxlclient.config</u> file, including the file name.


The next file to be selected is the <b>License Key</b> file. Please enter the path to the <u>license-key.xml</u> file, including the file name.

####Email Configuration####
CSAT Pro must be able to connect to and utilize a valid SMTP server in order to send email messages. CSAT Pro utilizes the Grails mail plugin for email communication.
Along with the default sender email address, CSAT Pro's mailing configuration must also include connection to a valid SMTP server in order to correctly distribute the "forgot password" messages. Numerous SMTP services exist, such as Gmail, Hotmail, Amazon SES, or in-house SMTP services available through corporate emailing technologies, such as Exchange. CSAT Pro can support these SMTP servers, as long as the connection information entered below is correct. By default, the plugin assumes an unsecured mail server configured at `localhost` on `port 25`. However, this can be modified in the email configuration screen.

####Set up TLS Configuration####
This screen is to set up TLS configuration. This screen has 3 options as to how you want to set up TLS for the CSAT Pro application. 

Please allow network traffic through the port specific to which option you select. We have listed the default port numbers for each option below.

----------


By default, we select generating a self-signed PKCS12 certificate, to allow for HTTPS protection to the application. Here we ask for 2 fields to be filled out, so we can generate the certificate for you. The default port for this option is **443**.

 - <b>Alias</b> - This will be the alias, as well as the key file name.
 - <b>Keystore Password</b> - This will be the password for access to the certificate.


----------


The second option is if you already have a certificate(self-signed or a certificate authority) that you would like CSAT Pro to use. The default port for this option is **443**.

 - **Certificate** - 
 - **Alias** - 
 - **Keystore Password** - 
 - **Key Password** - 


----------


The third option is our least recommended option in terms of security. This will allow for only HTTP requests, which will only have unencrypted communication to CSAT Pro. By default, the port for this option is **8080**.

####Installation####
In this section, the installer will be extracting all necessary files into the installation directory chosen. This process may take a few minutes.

####Set Up Database Admin##

####Installing and Starting CSAT Pro####

####Finished####
At this point, the installer has finished setting up and CSAT Pro is starting. It may take a few minutes for the application to be accessible. From here, you can check out the User Guide on how to log in and use CSAT Pro.

<a name="obtainingConfigFiles"></a>
## Obtaining Configuration Files##