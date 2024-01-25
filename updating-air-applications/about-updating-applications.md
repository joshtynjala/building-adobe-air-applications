# About updating applications

<div>

The
[Updater](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/Updater.html)
class (in the flash.desktop package) includes one method, `update()`, which you
can use to update the currently running application with a different version.
For example, if the user has a version of the AIR file ("Sample_App_v2.air")
located on the desktop, the following code updates the application.

ActionScript example:

    var updater:Updater = new Updater();
    var airFile:File = File.desktopDirectory.resolvePath("Sample_App_v2.air");
    var version:String = "2.01";
    updater.update(airFile, version);

JavaScript example:

    var updater = new air.Updater();
    var airFile = air.File.desktopDirectory.resolvePath("Sample_App_v2.air");
    var version = "2.01";
    updater.update(airFile, version);

Before an application uses the Updater class, the user or the application must
download the updated version of the AIR file to the computer. For more
information, see
[Downloading an AIR file to the user’s computer](WS5b3ccc516d4fbf351e63e3d118666ade46-7c55.html).

</div>

<div>

## Results of the Updater.update() method call

<div>

When an application in the runtime calls the `update()` method, the runtime
closes the application, and it then attempts to install the new version from the
AIR file. The runtime checks that the application ID and publisher ID specified
in the AIR file matches the application ID and publisher ID for the application
calling the `update()` method. (For information on the application ID and
publisher ID, see
[AIR application descriptor files](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html).)
It also checks that the version string matches the `version` string passed to
the `update()` method. If installation completes successfully, the runtime opens
the new version of the application. Otherwise (if the installation cannot
complete), it reopens the existing (pre-install) version of the application.

On Mac OS, to install an updated version of an application, the user must have
adequate system privileges to install to the application directory. On Windows
and Linux, a user must have administrative privileges.

If the updated version of the application requires an updated version of the
runtime, the new runtime version is installed. To update the runtime, a user
must have administrative privileges for the computer.

When testing an application using ADL, calling the `update()` method results in
a runtime exception.

</div>

</div>

<div>

## About the version string

<div>

The string that is specified as the `version` parameter of the `update()` method
must match the string in the `version` or `versionNumber` element in the
application descriptor file for the AIR file to be installed. Specifying the
`version` parameter is required for security reasons. By requiring the
application to verify the version number in the AIR file, the application will
not inadvertently install an older version. (An older version of the application
might contain a security vulnerability that has been fixed in the currently
installed application.) The application should also check the version string in
the AIR file with version string in the installed application to prevent
downgrade attacks.

Prior to AIR 2.5, the version string can be of any format. For example, it can
be "2.01" or "version 2". In AIR 2.5, or later, the version string must be a
sequence of up to three, three-digit numbers separated by periods. For example,
“.0”, “1.0”, and “67.89.999” are all valid version numbers. You should validate
the update version string before updating the application.

If an Adobe AIR application downloads an AIR file via the web, it is a good
practice to have a mechanism by which the web service can notify the Adobe AIR
application of the version being downloaded. The application can then use this
string as the `version` parameter of the `update()` method. If the AIR file is
obtained by some other means, in which the version of the AIR file is unknown,
the AIR application can examine the AIR file to determine the version
information. (An AIR file is a ZIP-compressed archive, and the application
descriptor file is the second record in the archive.)

For details on the application descriptor file, see
[AIR application descriptor files](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html).

</div>

</div>

<div>

## Signing workflow for application updates

<div>

Publishing updates in an ad-hoc manner complicates the tasks of managing
multiple application versions and also makes tracking certificate expiry dates
difficult. Certificates may expire before you can publish an update.

Adobe AIR runtime treats an application update published without a migration
signature as a new application. Users must uninstall their current AIR
application before they can install the application update.

To resolve the problem, upload each updated application with the latest
certificate to a separate deployment URL. Include a mechanism that reminds you
to apply migration signatures when your certificate is within the 180 days grace
period. See
[Signing an updated version of an AIR application](WS13ACB483-1711-43c0-9049-0A7251630A7D.html)
for more information.

See [ADT commands](WS901d38e593cd1bac1e63e3d128fc240122-8000.html) for
information on how to apply signatures.

Perform the following tasks to streamline the process of applying the migration
signatures:

- Upload each updated application to a separate deployment URL.

- Upload the upgrade descriptor XML file and the latest certificate for the
  update to the same URL.

- Sign the updated application with the latest certificate.

- Apply a migration signature to the updated application with the certificate
  used to sign the previous version located at a different URL.

</div>

</div>

<div>

<div>



</div>

</div>
