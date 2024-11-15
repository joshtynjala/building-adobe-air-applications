# Distributing AIR packages for desktop computers

AIR applications can be distributed as an AIR package, which contains the
application code and all assets. You can distribute this package through any of
the typical means, such as by download, by e-mail, or by physical media such as
a CD-ROM. Users can install the application by double-clicking the AIR file. You
can use the AIR in-browser API (a web-based ActionScript library) to let users
install your AIR application (and Adobe® AIR®, if needed) by clicking a single
link on a web page.

AIR applications can also be packaged and distributed as native installers (in
other words, as EXE files on Windows, DMG files on Mac, and DEB or RPM files on
Linux). Native install packages can be distributed and installed according to
the relevant platform conventions. When you distribute your application as a
native package, you do lose some of the benefits of the AIR file format. Namely,
a single install file can no longer be used on most platforms, the AIR update
framework can no longer be used, and the in-browser API can no longer be used.

## Installing and running an AIR application on the desktop

You can simply send the AIR file to the recipient. For example, you can send the
AIR file as an e-mail attachment or as a link in a web page.

Once the user downloads the AIR application, the user follows these instructions
to install it:

1.  Double-click the AIR file.

    Adobe AIR must already be installed on the computer.

2.  In the Installation window, leave the default settings selected, and then
    click Continue.

    In Windows, AIR automatically does the following:

    - Installs the application into the Program Files directory

    - Creates a desktop shortcut for application

    - Creates a Start Menu shortcut

    - Adds an entry for application in the Add / Remove Programs Control Panel

    In the Mac OS, by default the application is added to the Applications
    directory.

    If the application is already installed, the installer gives the user the
    choice of opening the existing version of the application or updating to the
    version in the downloaded AIR file. The installer identifies the application
    using the application ID and publisher ID in the AIR file.

3.  When the installation is complete, click Finish.

On Mac OS, to install an updated version of an application, the user needs
adequate system privileges to install to the application directory. On Windows
and Linux, a user needs administrative privileges.

An application can also install a new version via ActionScript or JavaScript.
For more information, see
[Updating AIR applications](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff2.html).

Once the AIR application is installed, a user simply double-clicks the
application icon to run it, just like any other desktop application.

- On Windows, double-click the application's icon (which is either installed on
  the desktop or in a folder) or select the application from the Start menu.

- On Linux, double-click the application's icon (which is either installed on
  the desktop or in a folder) or select the application from the applications
  menu.

- On Mac OS, double-click the application in the folder in which it was
  installed. The default installation directory is the /Applications directory.

> **Note:** Only AIR applications developed for AIR 2.6 or earlier can be
> installed on Linux.

The AIR _seamless install_ feature lets a user install an AIR application by
clicking a link in a web page. The AIR _browser invocation_ features lets a user
run an installed AIR application by clicking a link in a web page. These
features are described in the following section.

## Installing and running desktop AIR applications from a web page

The AIR in-browser API lets you install and run AIR application from a web page.
The AIR in-browser API is provided in a SWF library, _air.swf_, that is hosted
by Adobe. The AIR SDK includes a sample "badge" application that uses this
library to install, update, or launch an AIR application (and the runtime, if
necessary). You can modify the provided sample badge or create your own badge
web application that uses the online air.swf library directly.

Any AIR application can be installed through a web page badge. But, only
applications that include the
`<allowBrowserInvocation>true</allowBrowserInvocation>` element in their
application descriptor files can be launched by a web badge.

## Enterprise deployment on desktop computers

IT administrators can install the Adobe AIR runtime and AIR applications
silently using standard desktop deployment tools. IT administrators can do the
following:

- Silently install the Adobe AIR runtime using tools such as Microsoft SMS, IBM
  Tivoli, or any deployment tool that allows silent installations that use a
  bootstrapper

- Silently install the AIR application using the same tools used to deploy the
  runtime

For more information, see the
_[Adobe AIR Administrator's Guide](https://web.archive.org/web/20150311152212/http://help.adobe.com/en_US/air/admin/index.html)._

## Installation logs on desktop computers

Installation logs are recorded when either the AIR runtime itself or an AIR
application is installed. You can examine the log files to help determine the
cause of any installation or update problems that occur.

The log files are created in the following locations:

- Mac: the standard system log (`/private/var/log/system.log`)

  You can view the Mac system log by opening the Console application (typically
  found in the Utilities folder).

- Windows XP:
  `C:\Documents and Settings\<username>\Local Settings\Application Data\Adobe\AIR\logs\Install.log`

- Windows Vista, Windows 7:
  `C:\Users\<username>\AppData\Local\Adobe\AIR\logs\Install.log`

- Linux: `/home/<username>/.appdata/Adobe/AIR/Logs/Install.log`

> **Note:** These log files were not created in versions of AIR earlier than
> AIR 2.

More Help topics

[AIR.SWF in-browser API](WSfffb011ac560372f-1c6efe05128cca667e7-8000.html)
