---
layout: default
---
# SURFsara Central Data Infrastructure documentation

We're working on documentation for the SURFsara Central Data Infrastructure (CDI). Stay tuned.

*Note: The CDI is under heavy development. Data stored on the CDI may be erased without notice. Don't store valuable data on the CDI; use test data only.*

# What is the Central Data Infrastructure?

We're working on a description.

# Getting access to the CDI

To request access to the CDI for testing, contact our advisors at <a href="mailto:helpdesk@surfsara.nl?subject=Requesting%20access%20to%20CDI">helpdesk@surfsara.nl</a>. If granted, we'll give you a username and password. If you already have a SURFsara CUA account, please tell us, so that we can authorize your existing account for the CDI.

# Logging in to the portal

To access the ownCloud portal, go to https://portal.cdi.surfsara.nl. You will see a login screen: 

<a href="images/cdi-portal-login.png"><img src="images/cdi-portal-login.png" alt="CDI portal login" width="50%" height="50%" /></a>

Log in with your username and password. You will then see the ownCloud portal interface:

<a href="images/cdi-portal.png"><img src="images/cdi-portal.png" alt="CDI portal" width="75%" height="75%" /></a>

Here you can upload, download, move, remove and share files.

Please refer to the common ownCloud documentation at https://doc.owncloud.org/ to learn more about its capabilities. The currently installed version is 9.0.1.

# Using webdav

## OwnCloud webdav

OwnCloud has a webdav interface that enables mounting and automated access. You can find the webdav address when you click on the wheel icon in the lower left corner of the web interface.

## dCache webdav

There is also another webdav interface. The storage system behind ownCloud is dCache. dCache has a native webdav door, accessible at [https://pn1.cdi.surfsara.nl:8443/cdi/users/username/files/](https://pn1.cdi.surfsara.nl:8443/cdi/users/username/files/), where username is your own username. You will be asked for your username and password.

The dCache webdav interface offers a better performance than the ownCloud webdav. You may want to use it if you want to upload or download large amounts of data. The downside is that files that were shared through ownCloud are not visible through the dCache webdav interface.

<a href="images/dcache-webdav-interface.png"><img src="images/dcache-webdav-interface.png" alt="dCache webdav interface" width="75%" height="75%" /></a>

### Connection not secure

You may see the error "Connection not secure" when accessing the dCache webdav door. 

<a href="images/connection-not-secure.png"><img src="images/connection-not-secure.png" alt="Connection not secure" width="50%" height="50%" /></a>

That is because a root CA certificate needs to be installed. You can find this certificate at [https://www.terena.org/activities/tcs/repository-g3/](https://www.terena.org/activities/tcs/repository-g3/). Save the "TCS eScience SSL CA 3" PEM certificate, as illustrated below:

![cdi_portal](images/download-ca-cert.png)

Then (in Firefox; other browser may behave differently) go to Preferences -> Advanced -> Certificates -> View certificates.

![cdi_portal](images/import-ca-root-cert.png)

Click Import and select the certificate you have just downloaded. You will see the following dialogue:

![cdi_portal](images/trust-ca-cert.png)

Select all checkboxes and click OK. Then go back to the webdav interface and refresh the page.

### Automating webdav access

With `curl`, you can access the CDI storage from scripts that run non-interactively. For examples, please have a look at our [Grid documentation about curl and webdav](http://doc.grid.surfsara.nl/en/latest/Pages/Advanced/storage_clients/webdav.html#webdav "Grid documentation about curl & webdav"). Don't forget to use the correct webdav URL. Put your password in a file with `curl --netrc-file filename`; it's not safe to specify passwords on a command line on a shared system.

# Other access protocols

dCache offers these other file transfer protocols to access your data. Please note that shared files are not visible this way.

* GridFTP may be interesting in cases where the geographical distance is large, or where large amounts of data need to be transferred. GridFTP is designed to offer good performance in such cases. You need a user certificate to work with GridFTP.
* NFS - only from trusted (SURFsara) hosts
* dCap
* GSIdCap
* Xrootd
* SCP - through an NFS mount
* SFTP - through an NFS mount
* Globus-url-copy - through an NFS mount

If you need SCP, SFTP or other protocols we can set up such a service on top of an NFS mount.

Contact us if you want to experiment with any of these protocols.
