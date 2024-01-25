# Installing Adobe AIR

<div>

To install or update the runtime, a user must have administrative privileges for
the computer.

<div>

#### Install the runtime on a Windows computer

1.  Download the runtime installation file from <http://get.adobe.com/air>.

2.  Double-click the runtime installation file.

3.  In the installation window, follow the prompts to complete the installation.

</div>

<div>

#### Install the runtime on a Mac computer

1.  Download the runtime installation file from <http://get.adobe.com/air>.

2.  Double-click runtime installation file.

3.  In the installation window, follow the prompts to complete the installation.

4.  If the Installer displays an Authenticate window, enter your Mac OS user
    name and password.

</div>

<div>

#### Install the runtime on a Linux computer

<div>

Note: At this time, AIR 2.7 and later are not supported on Linux. AIR
applications deployed to Linux should continue to use the AIR 2.6 SDK.

</div>

_Using the binary installer:_

1.  Locate the installation binary file from
    <http://kb2.adobe.com/cps/853/cpsid_85304.html> and download.

2.  Set the file permissions so that the installer application can be executed.
    From a command line, you can set the file permissions with:

        chmod +x AdobeAIRInstaller.bin

    Some versions of Linux allow you to set the file permissions on the
    Properties dialog opened through a context menu.

3.  Run the installer from the command line or by double-clicking the runtime
    installation file.

4.  In the installation window, follow the prompts to complete the installation.

Adobe AIR is installed as a native package. In other words, as rpm on an rpm
based distribution and deb on a Debian distribution. Currently AIR does not
support any other package format.

_Using the package installers:_

1.  Locate the AIR package file from
    <http://kb2.adobe.com/cps/853/cpsid_85304.html>. Download the rpm or Debian
    package, depending on which package format your system supports.

2.  If needed, double-click AIR package file to install the package.

    You can also install from the command line:

    1.  On a Debian system:

            sudo dpkg -i <path to the package>/adobeair-2.0.0.xxxxx.deb

    2.  On an rpm-based system:

            sudo rpm -i <path to the package>/adobeair-2.0.0-xxxxx.i386.rpm

        Or, if you are updating an existing version (AIR 1.5.3 or later):

            sudo rpm -U <path to the package>/adobeair-2.0.0-xxxxx.i386.rpm

Installing AIR 2 and AIR applications requires you to have administrator
privileges on your computer.

Adobe AIR is installed to the following location: /opt/Adobe AIR/Versions/1.0

AIR registers the mime-type
"application/vnd.adobe.air-application-installer-package+zip", which means that
.air files are of this mime-type and are therefore registered with the AIR
runtime.

</div>

<div>

#### Install the runtime on an Android device

You can install the latest release of the AIR runtime from the Android Market.

You can install development versions of the AIR runtime from a link on a web
page or by using the ADT `-installRuntime` command. Only one version of the AIR
runtime can be installed at a time; you cannot have both a release and a
development version installed.

See [ADT installRuntime command](WS901d38e593cd1bac1e63e3d128fc240122-7ff6.html)
for more information.

</div>

<div>

#### Install the runtime on an iOS device

The necessary AIR runtime code is bundled with each application created for
iPhone, iTouch, and iPad devices. You do not install a separate runtime
component.

</div>

</div>

<div>

<div>

More Help topics

</div>

<div>

[AIR for iOS](WSfffb011ac560372f4239c49b12cd282d498-8000.html)

</div>

<div>



</div>

</div>
