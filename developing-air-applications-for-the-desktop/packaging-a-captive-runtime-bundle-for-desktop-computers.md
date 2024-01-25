# Packaging a captive runtime bundle for desktop computers

<div>

A captive runtime bundle is a package that includes your application code along
with a dedicated version of the runtime. An application packaged in this manner
uses the bundled runtime instead of the shared runtime installed elsewhere on a
user’s computer.

The bundle produced is a self-contained folder of application files on Windows
and an .app bundle on Mac OS. You must produce the bundle for a target operating
system while running under that operating system. (A virtual machine, such as
VMWare, can be used to run multiple operating systems on one computer.)

The application can be run from that folder or bundle without installation.

<div>

#### Benefits

- Produces a self-contained application

- No Internet access required for installation

- Application is isolated from runtime updates

- Enterprises can certify the specific application and runtime combination

- Supports the traditional software deployment model

- No separate runtime redistribution required

- Can use the NativeProcess API

- Can use native extensions

- Can use the `File.openWithDefaultApplication()` function without restriction

- Can run from a USB or optical disk without installation

</div>

<div>

#### Drawbacks

- Critical security fixes are not automatically available to users when Adobe
  publishes a security patch

- Cannot use the .air file format

- You must create your own installer, if needed

- AIR update API and framework are not supported

- The AIR in-browser API for installing and launching an AIR application from a
  web page is not supported

- On Windows, file registration must be handled by your installer

- Larger application disk footprint

</div>

</div>

<div>

## Creating a captive runtime bundle on Windows

<div>

To create a captive runtime bundle for Windows, you must package the application
while running under the Windows operating system. Package the application using
the ADT _bundle_ target:

    adt -package
        -keystore ..\cert.p12 -storetype pkcs12
        -target bundle
        myApp
        myApp-app.xml
        myApp.swf icons resources

This command creates the bundle in a directory named, myApp. The directory
contains the files for your application as well as the runtime files. You can
run the program directly from the folder. However, to create a program menu
entry, register file types, or URI scheme handlers, you must create an installer
program that sets the requisite registry entries. The AIR SDK does not include
tools for creating such installers, but several third-party options are
available, including both commercial and free, open-source installer toolkits.

You can sign the native executable on WIndows, by specifying a second set of
signing options after the `-target bundle` entry on the command line. These
signing options identify the private key and associated certificate to use when
applying the native Windows signature. (An AIR code signing certificate can
typically be used.) Only the primary executable is signed. Any additional
executables packaged with your application are not signed by this process.

<div>

#### File type association

To associate your application with public or custom file types on Windows, your
installer program must set the appropriate registry entries. The file types
should be listed in the fileTypes element of the application descriptor file as
well.

For more information about Windows file types, see
[MSDN Library: File Types and File Associations](http://msdn.microsoft.com/en-us/library/cc144104%28v=VS.85%29.aspx)

</div>

<div>

#### URI handler registration

In order for your application to handle the launch of a URL using a given URI
scheme, your installer must set the requisite registry entries.

For more information about registering an application to handle a URI scheme,
see
[MSDN Library: Registering an Application to a URL Protocol](http://msdn.microsoft.com/en-us/library/aa767914%28v=vs.85%29.aspx)

</div>

</div>

</div>

<div>

## Creating a captive runtime bundle on Mac OS X

<div>

To create a captive runtime bundle for Mac OS X, you must package the
application while running under the Macintosh operating system. Package the
application using the ADT _bundle_ target:

    adt -package
        -keystore ../cert.p12 -storetype pkcs12
        -target bundle
        myApp.app
        myApp-app.xml
        myApp.swf icons resources

This command creates the application bundle named, myApp.app. The bundle
contains the files for your application as well as the runtime files. You can
run the application by double-clicking the myApp.app icon and install it by
dragging it to a suitable location such as the Applications folder. However, to
register file types or URI scheme handlers, you must edit the property list file
inside the application package.

For distribution, you can create a disk image file (.dmg). The Adobe AIR SDK
does not provide tools for creating a dmg file for a captive runtime bundle.

<div>

#### File type association

To associate your application with public or custom file types on Mac OS X, you
must edit the info.plist file in the bundle to set the CFBundleDocumentTypes
property. See
[Mac OS X Developer Library: Information Property List Key Reference, CFBundleURLTypes](http://developer.apple.com/library/mac/#DOCUMENTATION/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html#//apple_ref/doc/uid/TP40009249-SW1).

</div>

<div>

#### URI handler registration

In order for your application to handle the launch of a URL using a given URI
scheme, you must edit the info.plist file in the bundle to set the
CFBundleURLTypes property. See
[Mac OS X Developer Library: Information Property List Key Reference, CFBundleDocumentTypes](http://developer.apple.com/library/mac/#DOCUMENTATION/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html#//apple_ref/doc/uid/TP40009249-SW1).

</div>

</div>

</div>

<div>

<div>



</div>

</div>
