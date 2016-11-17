---
layout: default
---
# SURFsara Central Data infrastructure documentation

We're working on documentation for the SURFsara Central Data Infrastructure (CDI). Stay tuned.

# What is the Central Data Infrastructure?

We're working on a description.

# Getting access to the CDI

To get access to the CDI for testing, contact our advisors at <a href="mailto:helpdesk@surfsara.nl?subject=Requesting%20access%20to%20CDI">helpdesk@surfsara.nl</a>. If granted, you will get a username and password. If you already have a SURFsara CUA account, please tell us so that we can authorize your existing account for the CDI.

# Logging in to the portal

To access the ownCloud portal, go to https://portal.cdi.surfsara.nl. You will see a login screen: 

![cdi_portal_login](images/cdi-portal-login.png)

Log in with your username and password. You will then see the ownCloud portal interface:

![cdi_portal](images/cdi-portal.png)

Here you can upload, download, move, remove and share files.

Please refer to the common ownCloud documentation at https://doc.owncloud.org/ to learn more about its capabilities. The currently installed version is 9.0.1.

# Using webdav

## OwnCloud webdav

OwnCloud has a webdav interface that enables mounting and automated access. You can find the webdav address when you click on the wheel icon in the lower left corner of the web interface.

## dCache webdav

There is also another webdav interface. The storage system behind ownCloud is dCache. dCache has a native webdav door, accessible at https://pn1.cdi.surfsara.nl:8443/cdi/users/username/files/, where username is your own username. You will be asked for your username and password.

### Connection not secure

You may see the error "Connection not secure" when accessing the dCache webdav door. 

![cdi_portal](images/connection-not-secure.png)

That is because a root CA certificate needs to be installed. You can find this certificate at https://www.terena.org/activities/tcs/repository-g3/. Save the "TCS eScience SSL CA 3" PEM certificate, as illustrated below:

![cdi_portal](images/download-ca-cert.png)

Then (in Firefox; other browser may behave differently) go to Preferences -> Advanced -> Certificates -> View certificates.

![cdi_portal](images/import-ca-root-cert.png)

Click Import and select the certificate you have just downloaded. You will see the following dialogue:

![cdi_portal](images/trust-ca-cert.png)

Select all checkboxes and click OK. Then go back to the webdav interface and refresh the page.

# Other access protocols

dCache is also accessible via other file transfer protocols. GridFTP is one of them, that may be interesting in cases where the geographical distance is large, or where large amounts of data need to be transferred. GridFTP is designed to offer the best performance in such cases. Contact us if you want to experiment with that.
