# Updating AIR applications

<div>

Users can install or update an AIR application by double-clicking an AIR file on
their computer or from the browser (using the seamless install feature). The
Adobe® AIR® installer application manages the installation, alerting the user if
they are updating an already existing application.

However, you can also have an installed application update itself to a new
version, using the Updater class. (An installed application may detect that a
new version is available to be downloaded and installed.) The Updater class
includes an `update()` method that lets you point to an AIR file on the user’s
computer and update to that version. Your application must be packaged as an AIR
file in order to use the Updater class. Applications packaged as a native
executable or package should use the update facilities provided by the native
platform.

Both the application ID and the publisher ID of an update AIR file must match
the application to be updated. The publisher ID is derived from the signing
certificate. Both the update and the application to be updated must be signed
with the same certificate.

For AIR 1.5.3 or later, the application descriptor file includes a
`<publisherID>` element. You must use this element if there are versions of your
application developed using AIR 1.5.2 or earlier. For more information, see
[publisherID](WS901d38e593cd1bac1e63e3d12939cc14ab-8000.html).

As of AIR 1.1 and later, you can migrate an application to use a new
code-signing certificate. Migrating an application to use a new signature
involves signing the update AIR file with both the new and the original
certificates. Certificate migration is a one-way process. After the migration,
only AIR files signed with the new certificate (or with both certificates) will
be recognized as updates to an existing installation.

Managing updates of applications can be complicated. AIR 1.5 includes the new
_update framework for AdobeAIR applications_. This framework provides APIs to
assist developers in providing good update capabilities in AIR applications.

You can use certificate migration to change from a self-signed certificate to a
commercial code-signing certificate or from one self-signed or commercial
certificate to another. If you do not migrate the certificate, existing users
must remove their current version of your application before installing the new
version. For more information see
[Changing certificates](WSFAB6E5EB-316A-42b0-81A3-0BC232ACD99A.html).

It is a good practice to include an update mechanism in your application. If you
create a new version the application, the update mechanism can prompt the user
to install the new version.

The AIR application installer creates log files when an AIR application is
installed, updated, or removed. You can consult these logs to help determine the
cause of any installation problems. See
[Installation logs](http://kb2.adobe.com/cps/839/cpsid_83989.html).

<div>

<div>

Note: New versions of the Adobe AIR runtime may include updated versions of
WebKit. An updated version of WebKit _may_ result in unexpected changes in HTML
content in a deployed AIR application. These changes may require you to update
your application. An update mechanism can inform the user of the new version of
the application. For more information, see
[About the HTML environment](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7fb1.html)
(for ActionScript developers) or
[About the HTML environment](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7fb1.html)
(for HTML developers).

</div>

</div>

- [About updating applications](WS5b3ccc516d4fbf351e63e3d118666ade46-7c57.html)
- [Presenting a custom application update user interface](WS5b3ccc516d4fbf351e63e3d118666ade46-7ccd.html)
- [Downloading an AIR file to the user’s computer](WS5b3ccc516d4fbf351e63e3d118666ade46-7c55.html)
- [Checking to see if an application is running for the first time](WS5b3ccc516d4fbf351e63e3d118666ade46-7c54.html)
- [Using the update framework](WS9CD40F06-4DD7-4230-B56A-88AA27541A1E.html)

</div>

<div>

<div>



</div>

</div>
