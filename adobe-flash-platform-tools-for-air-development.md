# Adobe Flash Platform tools for AIR development

<div>

You can develop AIR applications with the following Adobe Flash Platform
development tools.

For ActionScript 3.0 (Flash and Flex) developers:

<div>

- Adobe Flash Professional (see
  [Publishing for AIR](http://help.adobe.com/en_US/Flash/10.0_UsingFlash/WSF0126B20-BFF4-4c50-9978-BCA47C8C3C3F.html))

- Adobe Flex 3.x and 4.x SDKs (see
  [Setting up the Flex SDK](WS2d8d13466044a733190f0432124114d9a19-8000.html) and
  [AIR Developer Tool (ADT)](WS5b3ccc516d4fbf351e63e3d118666ade46-7fd9.html))

- Adobe Flash Builder (see
  [Developing AIR Applications with Flash Builder](http://help.adobe.com/en_US/Flex/4.0/UsingFlashBuilder/WS6b84a753ecd210fd-7fb8a08d12114b6a4cf-8000.html))

</div>

For HTML and Ajax developers:

- Adobe AIR SDK (see
  [Installing the AIR SDK](WS2d8d13466044a73328ed2239124110d12b3-8000.html) and
  [AIR Developer Tool (ADT)](WS5b3ccc516d4fbf351e63e3d118666ade46-7fd9.html))

- Adobe Dreamweaver CS3, CS4, CS5 (see
  [AIR Extension for Dreamweaver](http://help.adobe.com/en_US/Dreamweaver/CS5/Using/WS6463f310bbfa3de2-1eb2a492126f73db0f1-8000.html))

<!-- -->

</div>

<div>

## Installing the AIR SDK

<div>

The Adobe AIR SDK contains the following command-line tools that you use to
launch and package applications:

AIR Debug Launcher (ADL)  
Allows you to run AIR applications without having to first install them. See
[AIR Debug Launcher (ADL)](WSfffb011ac560372f-6fa6d7e0128cca93d31-8000.html).

AIR Development Tool (ADT)  
Packages AIR applications into distributable installation packages. See
[AIR Developer Tool (ADT)](WS5b3ccc516d4fbf351e63e3d118666ade46-7fd9.html).

The AIR command-line tools require Java to be installed your computer. You can
use the Java virtual machine from either the JRE or the JDK (version 1.5 or
newer). The Java JRE and the Java JDK are available at http://java.sun.com/.

At least 2GB of computer memory is required to run the ADT tool.

<div>

Note: Java is not required for end users to run AIR applications.

</div>

For a quick overview of building an AIR application with the AIR SDK, see
[Creating your first HTML-based AIR application with the AIR SDK](WS5b3ccc516d4fbf351e63e3d118666ade46-7ecc.html).

</div>

<div>

### Download and install the AIR SDK

<div>

You can download and install the AIR SDK using the following instructions:

<div>

#### Install the AIR SDK in Windows

- Download the AIR SDK installation file.

- The AIR SDK is distributed as a standard file archive. To install AIR, extract
  the contents of the SDK to a folder on your computer (for example: C:\Program
  Files\Adobe\AIRSDK or C:\AIRSDK).

- The ADL and ADT tools are contained in the bin folder in the AIR SDK; add the
  path to this folder to your PATH environment variable.

</div>

<div>

#### Install the AIR SDK in Mac OS X

- Download the AIR SDK installation file.

- The AIR SDK is distributed as a standard file archive. To install AIR, extract
  the contents of the SDK to a folder on your computer (for example:
  /Users/\<userName\>/Applications/AIRSDK).

- The ADL and ADT tools are contained in the bin folder in the AIR SDK; add the
  path to this folder to your PATH environment variable.

</div>

<div>

#### Install the AIR SDK in Linux

- The SDK is available in tbz2 format.

- To install the SDK, create a folder in which you want to unzip the SDK, then
  use the following command: tar -jxvf \<path to AIR-SDK.tbz2\>

For information about getting started using the AIR SDK tools, see Creating an
AIR application using the command-line tools.

</div>

</div>

</div>

<div>

### What's included in the AIR SDK

<div>

The following table describes the purpose of the files contained in the AIR SDK:

<div>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>SDK folder</p></th>
<th><p>Files/tools description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>bin</p></td>
<td><p>The AIR Debug Launcher (ADL) allows you to run an AIR application
without first packaging and installing it. For information about using
this tool, see <a
href="WSfffb011ac560372f-6fa6d7e0128cca93d31-8000.html">AIR Debug
Launcher (ADL)</a>.</p>
<p>The AIR Developer Tool (ADT) packages your application as an AIR file
for distribution. For information about using this tool, see <a
href="WS5b3ccc516d4fbf351e63e3d118666ade46-7fd9.html">AIR Developer Tool
(ADT)</a>.</p></td>
</tr>
<tr class="even">
<td><p>frameworks</p></td>
<td><p>The libs directory contains code libraries for use in AIR
applications.</p>
<p>The projects directory contains the code for the compiled SWF and SWC
libraries.</p></td>
</tr>
<tr class="odd">
<td><p>include</p></td>
<td><p>The include directory contains the C-language header file for
writing native extensions.</p></td>
</tr>
<tr class="even">
<td><p>install</p></td>
<td><p>The install directory contains the Windows USB drivers for
Android devices. (These are the drivers provided by Google in the
Android SDK.)</p></td>
</tr>
<tr class="odd">
<td><p>lib</p></td>
<td><p>Contains support code for the AIR SDK tools.</p></td>
</tr>
<tr class="even">
<td><p>runtimes</p></td>
<td><p>The AIR runtimes for the desktop and for mobile devices.</p>
<p>The desktop runtime is used by ADL to launch your AIR applications
before they have been packaged or installed.</p>
<p>The AIR runtimes for Android (APK packages) can be installed on
Android devices or emulators for development and testing. Separate APK
packages are used for devices and emulators. (The public AIR runtime for
Android is available from the Android Market.)</p></td>
</tr>
<tr class="odd">
<td><p>samples</p></td>
<td><p>This folder contains a sample application descriptor file, a
sample of the seamless install feature (badge.swf), and the default AIR
application icons.</p></td>
</tr>
<tr class="even">
<td><p>templates</p></td>
<td><p>descriptor-template.xml - A template of the application
descriptor file, which is required for each AIR application. For a
detailed description of the application descriptor file, see <a
href="WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html">AIR application
descriptor files</a>.</p>
<p>Schema files for the XML structure of the application descriptor for
each release version of AIR are also found in this folder.</p></td>
</tr>
</tbody>
</table>

</div>

</div>

</div>

</div>

<div>

## Setting up the Flex SDK

<div>

To develop Adobe® AIR® applications with Adobe® Flex™, you have the following
options:

- You can download and install Adobe® Flash® Builder™, which provides integrated
  tools to create Adobe AIR projects and test, debug, and package your AIR
  applications. See
  [Creating your first desktop Flex AIR application in Flash Builder](WS5b3ccc516d4fbf351e63e3d118676a28bd-8000.html).

- You can download the Adobe® Flex™ SDK and develop Flex AIR applications using
  your favorite text editor and the command-line tools.

For a quick overview of building an AIR application with Flex SDK, see
[Creating your first desktop AIR application with the Flex SDK](WS144092a96ffef7cc4c0afd1212601c9a36f-8000.html).

</div>

<div>

### Install the Flex SDK

<div>

Building AIR applications with the command-line tools requires that Java is
installed on your computer. You can use the Java virtual machine from either the
JRE or the JDK (version 1.5 or newer). The Java JRE and JDK are available at
http://java.sun.com/.

<div>

Note: Java is not required for end users to run AIR applications.

</div>

The Flex SDK provides you with the AIR API and command-line tools that you use
to package, compile, and debug your AIR applications.

1.  If you haven't already done so, download the Flex SDK at
    <http://opensource.adobe.com/wiki/display/flexsdk/Downloads>.

2.  Place the contents of the SDK into a folder (for example, Flex SDK).

3.  Copy the contents of the AIR SDK over the files in the Flex SDK.

    <div>

    Note: On Mac computers, make sure that you copy or replace the individual
    files in the SDK folders — not entire directories. By default, copying a
    directory on the Mac to a directory of the same name removes the existing
    files in the target directory; it does not merge the contents of the two
    directories. You can use the `ditto` command in a terminal window to merge
    the AIR SDK into the Flex SDK:`ditto air_sdk_folder flex_sdk_folder`

    </div>

4.  The command-line AIR utilities are located in the bin folder.

</div>

</div>

</div>

<div>

## Setting up external SDKs

<div>

Developing applications for Android and iOS requires that you download
provisioning files, SDKs or other development tools from the platform makers.

For information about downloading and installing the Android SDK, see
[Android Developers: Installing the SDK](http://developer.android.com/sdk/installing.html).
As of AIR 2.6, you are not required to download the Android SDK. The AIR SDK now
includes the basic components needed to install and launch APK packages. Still,
the Android SDK can be useful for a variety of development tasks, including
creating and running software emulators and taking device screenshots.

An external SDK is not required for iOS development. However, special
certificates and provisioning profiles are needed. For more information, see
[Obtaining developer files from Apple](http://help.adobe.com/en_US/as3/iphone/WS789ea67d3e73a8b2-240138de1243a7725e7-7ffd.html).

</div>

</div>

<div>

<div>



</div>

</div>
