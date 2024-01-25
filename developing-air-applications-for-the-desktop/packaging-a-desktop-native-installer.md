# Packaging a desktop native installer

<div>

As of AIR 2, you can use ADT to create native application installers for
distributing AIR applications. For example, you can build an EXE installer file
for distribution of an AIR application on Windows. You can build a DMG installer
file for distribution of an AIR application on Mac OS. In AIR 2.5 and AIR 2.6,
you can build a DEB or RPM installer file for distribution of an AIR application
on Linux.

Applications installed with a native application installer are known as extended
desktop profile applications. You cannot use ADT to package a native installer
for an AIR application if the application descriptor file does not support the
desktop extended profile. You can restrict this profile using the
`supportedProfiles` element in the application descriptor file. See
[Device profiles](WS144092a96ffef7cc16ddeea2126bb46b82f-8000.html) and
[supportedProfiles](WSfffb011ac560372f2fea1812938a6e463-7fe2.html).

You can build a native installer version of the AIR application in two basic
ways:

<div>

- You can build the native installer based on the application descriptor file
  and other source files. (Other source files may include SWF files, HTML files,
  and other assets.)

- You can build the native installer based on an AIR file or based on an AIRI
  file.

</div>

You must use ADT on the same operating system as that of the native installer
file you want to generate. So, to create an EXE file for Windows, run ADT on
Windows. To create a DMG file for Mac OS, run ADT on Mac OS. To create a DEB or
RPG file for Linux, run ADT from the AIR 2.6 SDK on Linux.

When you create a native installer to distribute an AIR application, the
application gains these capabilities:

<div>

- <div>

  It can launch and interact with native processes, using the NativeProcess
  class. For details, see one of the following:

  - [Communicating with native processes in AIR](http://help.adobe.com/en_US/as3/dev/WSb2ba3b1aad8a27b060d22f991220f00ad8a-8000.html)
    (for ActionScript developers)

  - [Communicating with native processes in AIR](http://help.adobe.com/en_US/air/html/dev/WSb2ba3b1aad8a27b060d22f991220f00ad8a-8000.html)
    (for HTML developers)

  </div>

- It can use native extensions.

- It can use the `File.openWithDefaultApplication()` method to open any file
  with the default system application defined to open it, regardless of its file
  type. (There are restrictions on applications that are _not_ installed with a
  native installer. For details, see the entry for the
  `File.openWithDefaultApplication()` entry in the language reference.)

</div>

However, when packaged as a native installer, the application loses some of the
benefits of the AIR file format. A single file can no longer be distributed to
all desktop computers. The built-in update function (as well as the updater
framework) does not work.

When the user double-clicks the native installer file, it installs the AIR
application. If the required version of Adobe AIR is not already installed on
the machine, the installer downloads it from the network and installs it first.
If there is no network connection from which to obtain the correct version of
Adobe AIR (if necessary), installation fails. Also, the installation fails if
the operating system is not supported in Adobe AIR 2.

<div>

<div>

Note: If you want a file to be executable in your installed application, make
sure that it's executable on the filesystem when you package your application.
(On Mac and Linux, you can use chmod to set the executable flag, if needed.)

</div>

</div>

<div>

#### Creating a native installer from the application source files

To build a native installer out of the source files for the application, use the
`-package` command with the following syntax (on a single command line):

    adt -package AIR_SIGNING_OPTIONS
        -target native
        [WINDOWS_INSTALLER_SIGNING_OPTIONS]
        installer_file
        app_xml
        [file_or_dir | -C dir file_or_dir | -e file dir ...] ...

This syntax is similar to the syntax for packaging an AIR file (without a native
installer). However there are a few differences:

<div>

- You add the `-target native` option to the command. (If you specify
  `-target air`, then ADT generates an AIR file instead of a native installer
  file.)

- You specify the target DMG or EXE file as the `installer_file`.

- Optionally, on Windows you can add a second set of signing options, indicated
  as `[WINDOWS_INSTALLER_SIGNING_OPTIONS]` in the syntax listing. On Windows, in
  addition to signing the AIR file, you can sign the Windows Installer file. Use
  the same type of certificate and signing option syntax as you would for
  signing the AIR file (see
  [ADT code signing options](WS5b3ccc516d4fbf351e63e3d118666ade46-7f72.html)).
  You can use the same certificate to sign the AIR file and the installer file,
  or you can specify different certificates. When a user downloads a signed
  Windows Installer file from the web, Windows identifies the source of the
  file, based on the certificate.

</div>

For details on ADT options other than the `-target` option, see
[AIR Developer Tool (ADT)](WS5b3ccc516d4fbf351e63e3d118666ade46-7fd9.html).

The following example creates a DMG file (a native installer file for Mac OS):

<div>

    adt -package
        -storetype pkcs12
        -keystore myCert.pfx
        -target native
        myApp.dmg
        application.xml
        index.html resources

</div>

The following example creates an EXE file (a native installer file for Windows):

<div>

    adt -package
        -storetype pkcs12
        -keystore myCert.pfx
        -target native
        myApp.exe
        application.xml
        index.html resources

</div>

The following example creates an EXE file and signs it:

<div>

    adt -package
        -storetype pkcs12
        -keystore myCert.pfx
        -target native
        -storetype pkcs12
        -keystore myCert.pfx
        myApp.exe
        application.xml
        index.html resources

</div>

</div>

<div>

#### Creating a native installer for an application that uses native extensions

You can build a native installer out of the source files for the application and
the native extension packages that the application requires. Use the `-package`
command with the following syntax (on a single command line):

    adt -package AIR_SIGNING_OPTIONS
        -migrate MIGRATION_SIGNING_OPTIONS
        -target native
        [WINDOWS_INSTALLER_SIGNING_OPTIONS]
        installer_file
        app_xml
        -extdir extension-directory
        [file_or_dir | -C dir file_or_dir | -e file dir ...] ...

This syntax is the same syntax used for packaging an a native installer, with
two additional options. Use the `-extdir `_`extension-directory`_ option to
specify the directory that contains the ANE files (native extensions) that the
application uses. Use the optional `-migrate` flag and
`MIGRATION_SIGNING_OPTIONS` parameters to sign an update to an application with
a migration signature, when the primary code-signing certificate is different
certificate than the one used by the previous version. For more information see
[Signing an updated version of an AIR application](WS13ACB483-1711-43c0-9049-0A7251630A7D.html).

For details on ADT options, see
[AIR Developer Tool (ADT)](WS5b3ccc516d4fbf351e63e3d118666ade46-7fd9.html).

The following example creates a DMG file (a native installer file for Mac OS)
for an application that uses native extensions:

<div>

    adt -package
        -storetype pkcs12
        -keystore myCert.pfx
        -target native
        myApp.dmg
        application.xml
        -extdir extensionsDir
        index.html resources

</div>

</div>

<div>

#### Creating a native installer from an AIR file or an AIRI file

You can use ADT to generate a native installer file based on an AIR file or an
AIRI file. To build a native installer based on an AIR file, use the ADT
`-package` command with the following syntax (on a single command line):

    adt -package
        -target native
        [WINDOWS_INSTALLER_SIGNING_OPTIONS]
        installer_file
        air_file

This syntax is similar to the syntax for creating a native installer based on
the source files for the AIR application. However, there are a few differences:

<div>

- As the source, you specify an AIR file, rather than an application descriptor
  file and other source files for the AIR application.

- Do not specify signing options for the AIR file, as it is already signed

</div>

To build a native installer based on an _AIRI_ file, use the ADT `-package`
command with the following syntax (on a single command line):

    adt AIR_SIGNING_OPTIONS
        -package
        -target native
        [WINDOWS_INSTALLER_SIGNING_OPTIONS]
        installer_file
        airi_file

This syntax is similar to the syntax for creating a native installer based on an
AIR file. However there are a few of differences:

<div>

- As the source, you specify an AIRI file.

- You specify signing options for the target AIR application.

</div>

The following example creates a DMG file (a native installer file for Mac OS)
based on an AIR file:

<div>

    adt -package -target native myApp.dmg myApp.air

</div>

The following example creates an EXE file (a native installer file for Windows)
based on an AIR file:

<div>

    adt -package -target native myApp.exe myApp.air

</div>

The following example creates an EXE file (based on an AIR file) and signs it:

<div>

    adt -package -target native -storetype pkcs12 -keystore myCert.pfx myApp.exe myApp.air

</div>

The following example creates a DMG file (a native installer file for Mac OS)
based on an AIRI file:

<div>

    adt -storetype pkcs12 -keystore myCert.pfx -package -target native myApp.dmg myApp.airi

</div>

The following example creates an EXE file (a native installer file for Windows)
based on an AIRI file:

<div>

    adt -storetype pkcs12 -keystore myCert.pfx -package -target native myApp.exe myApp.airi

</div>

The following example creates an EXE file (based on an AIRI file) and signs it
with both an AIR and a native Windows signature:

<div>

    adt -package -storetype pkcs12 -keystore myCert.pfx -target native -storetype pkcs12 -keystore myCert.pfx myApp.exe myApp.airi

</div>

</div>

</div>

<div>

<div>



</div>

</div>
