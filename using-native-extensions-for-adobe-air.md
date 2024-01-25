# Using native extensions for Adobe AIR

<div>

Native extensions for Adobe AIR provide ActionScript APIs that provide you
access to device-specific functionality programmed in native code. Native
extension developers sometimes work with device manufacturers, and sometimes are
third-party developers.

If you are developing a native extension, see
[Developing Native Extensions for Adobe AIR](http://www.adobe.com/go/learn_air_as_extensions_en).

A native extension is a combination of:

- ActionScript classes.

- Native code.

However, as an AIR application developer using a native extension, you work with
only the ActionScript classes.

Native extensions are useful in the following situations:

- The native code implementation provides access to platform-specific features.
  These platform-specific features are not available in the built-in
  ActionScript classes, and are not possible to implement in
  application-specific ActionScript classes. The native code implementation can
  provide such functionality because it has access to device-specific hardware
  and software.

- A native code implementation can sometimes be faster than an implementation
  that uses only ActionScript.

- The native code implementation can provide ActionScript access to legacy
  native code.

Some examples of native extensions are on the Adobe Developer Center. For
example, one native extension provides AIR applications access to Android’s
vibration feature. See
[Native extensions for Adobe AIR](http://www.adobe.com/go/learn_native_extension_examples_en).

<div xmlns:adobe="http://www.adobe.com/saxon">

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td colspan="2"><h2 id="adobe-recommends">Adobe recommends</h2></td>
<td colspan="2"><h3 id="have-a-tutorial-you-would-like-to-share"><img
src="./img/TinyBlueTutIcon.png" /><a
href="http://www.adobe.com/community/publishing/download.html">Have a
tutorial you would like to share?</a></h3></td>
</tr>
<tr class="even">
<td colspan="4" height="10"></td>
</tr>
<tr class="odd">
<td width="5%"><span><img src="./img/oliver_goldman.png" /></span></td>
<td width="45%"><h3 id="extending-adobe-air"><a
href="http://goo.gl/y8Lu7">Extending Adobe AIR</a></h3>
<span>Oliver Goldman</span></td>
<td width="5%"><span><img src="./img/milkmanGames.png" /></span></td>
<td width="45%"><h3
id="developing-android-extensions-for-air3-a-beginners-guide"><a
href="http://goo.gl/EPSg6">Developing Android Extensions for AIR3: A
Beginner's Guide</a></h3>
<span>Milkman Games</span></td>
</tr>
</tbody>
</table>

</div>

</div>

<div>

## AIR Native Extension (ANE) files

<div>

Native extension developers package a native extension into an ANE file. An ANE
file is an archive file that contains the necessary libraries and resources for
the native extension.

Note for some devices, the ANE file contains the native code library that the
native extension uses. But for other devices, the native code library is
installed on the device. In some cases, the native extension has no native code
at all for a particular device; it is implemented with ActionScript only.

As an AIR application developer, you use the ANE file as follows:

<div>

- Include the ANE file in the application’s library path in the same way you
  include a SWC file in the library path. This action allows the application to
  reference the extension’s ActionScript classes.

  <div>

  Note: When compiling your application, be sure to use dynamic linking for the
  ANE. If you use Flash Builder, specify External on the ActionScript Builder
  Path Properties panel; if you use the command line, specify
  -external-library-path.

  </div>

- Package the ANE file with the AIR application.

</div>

</div>

</div>

<div>

## Native extensions versus the NativeProcess ActionScript class

<div>

ActionScript 3.0 provides a NativeProcess class. This class lets an AIR
application execute native processes on the host operating system. This
capability is similar to native extensions, which provide access to
platform-specific features and libraries. When deciding on using the
NativeProcess class versus using a native extension, consider the following:

- Only the `extendedDesktop` AIR profile supports the NativeProcess class.
  Therefore, for applications with the AIR profiles `mobileDevice` and
  `extendedMobileDevice`, native extensions are the only choice.

- Native extension developers often provide native implementations for various
  platforms, but the ActionScript API they provide is typically the same across
  platforms. When using the NativeProcess class, ActionScript code to start the
  native process can vary among the different platforms.

- The NativeProcess class starts a separate process, whereas a native extension
  runs in the same process as the AIR application. Therefore, if you are
  concerned about code crashing, using the NativeProcess class is safer.
  However, the separate process means that you possibly have interprocess
  communication handling to implement.

<!-- -->

</div>

</div>

<div>

## Native extensions versus ActionScript class libraries (SWC files)

<div>

A SWC file is an ActionScript class library in an archive format. The SWC file
contains a SWF file and other resource files. The SWC file is a convenient way
to share ActionScript classes instead of sharing individual ActionScript code
and resource files.

A native extension package is an ANE file. Like a SWC file, an ANE file is also
an ActionScript class library, containing a SWF file and other resource files in
an archive format. However, the most important difference between an ANE file
and a SWC file is that only an ANE file can contain a native code library.

<div>

Note: When compiling your application, be sure to use dynamic linking for the
ANE file. If you use Flash Builder, specify External on the ActionScript Builder
Path Properties panel; if you use the command line, specify
-external-library-path.

</div>

</div>

</div>

<div>

## Supported devices

<div>

Starting in AIR 3, you can use native extensions in applications for the
following devices:

<div>

- Android devices, starting with Android 2.2

- iOS devices, starting with iOS 4.0

- iOS Simulator, starting with AIR 3.3

- Blackberry PlayBook

- Windows desktop devices that support AIR 3.0

- Mac OS X desktop devices that support AIR 3.0

</div>

Often, the same native extension targets multiple platforms. The extension’s ANE
file contains ActionScript and native libraries for each supported platform.
Usually, the ActionScript libraries have the same public interfaces for all the
platforms. The native libraries are necessarily different.

Sometimes a native extension supports a default platform. The default platform’s
implementation has only ActionScript code, but no native code. If you package an
application for a platform that the extension does not specifically support, the
application uses the default implementation when it executes. For example,
consider an extension that provides a feature that applies only to mobile
devices. The extension can also provide a default implementation that a desktop
application can use to simulate the feature.

</div>

</div>

<div>

## Supported device profiles

<div>

The following AIR profiles support native extensions:

<div>

- `extendedDesktop`, starting in AIR 3.0

- `mobileDevice`, starting in AIR 3.0

- `extendedMobileDevice`, starting in AIR 3.0

</div>

</div>

</div>

<div>

## Task list for using a native extension

<div>

To use a native extension in your application, do the following tasks:

1.  Declare the extension in your application descriptor file.

2.  Include the ANE file in your application’s library path.

3.  Package the application.

</div>

</div>

<div>

## Declaring the extension in your application descriptor file

<div>

All AIR applications have an application descriptor file. When an application
uses a native extension, the application descriptor file includes an
`<extensions>` element. For example:

    <extensions>
        <extensionID>com.example.Extension1</extensionID>
        <extensionID>com.example.Extension2</extensionID>
    </extensions>

The `extensionID` element has the same value as the `id` element in the
extension descriptor file. The extension descriptor file is an XML file called
extension.xml. It is packaged in the ANE file. You can use an archive extractor
tool to look at the extension.xml file.

</div>

</div>

<div>

## Including the ANE file in your application’s library path

<div>

To compile an application that uses a native extension, include the ANE file in
your library path.

</div>

<div>

### Using the ANE file with Flash Builder

<div>

If your application uses a native extension, include the ANE file for the native
extension in your library path. Then you can use Flash Builder to compile your
ActionScript code.

Do the following steps, which use Flash Builder 4.5.1:

<div>

1.  Change the filename extension of the ANE file from .ane to .swc. This step
    is necessary so that Flash Builder can find the file.

2.  Select Project \> Properties on your Flash Builder project.

3.  Select the Flex Build Path in the Properties dialog box.

4.  In the Library Path tab, select Add SWC....

5.  Browse to the SWC file and select Open.

6.  Select OK in the Add SWC... dialog box.

    The ANE file now appears in the Library Path tab in the Properties dialog
    box.

7.  Expand the SWC file entry. Double-click Link Type to open the Library Path
    Item Options dialog box.

8.  In the Library Path Item Options dialog box, change the Link Type to
    External.

</div>

Now you can compile your application using, for example, Project \> Build
Project.

</div>

</div>

<div>

### Using the ANE file with Flash Professional

<div>

If your application uses a native extension, include the ANE file for the native
extension in your library path. Then you can use Flash Professional CS5.5 to
compile your ActionScript code. Do the following:

<div>

1.  Change the filename extension of the ANE file from .ane to .swc. This step
    is necessary so that Flash Professional can find the file.

2.  Select File \> ActionScript Settings on your FLA file.

3.  Select the Library Path tab in the Advanced ActionScript 3.0 Settings dialog
    box.

4.  Select the Browse To SWC File button.

5.  Browse to the SWC file and select Open.

    The SWC file now appears in the Library Path tab in the Advanced
    ActionScript 3.0 Settings dialog box

6.  With the SWC file selected, select the button Select Linkage Options For A
    Library.

7.  In the Library Path Item Options dialog box, change the Link Type to
    External.

</div>

</div>

</div>

</div>

<div>

## Packaging an application that uses native extensions

<div>

Use ADT to package an application that uses native extensions. You cannot
package the application using Flash Professional CS5.5 or Flash Builder 4.5.1.

Details about using ADT are at
[AIR Developer Tool (ADT)](http://www.adobe.com/go/learn_fbairdevelopertool_en).

For example, the following ADT command creates a DMG file (a native installer
file for Mac OS X) for an application that uses native extensions:

<div>

    adt -package
        -storetype pkcs12
        -keystore myCert.pfx
        -target native
        myApp.dmg
        application.xml
        index.html resources
        -extdir extensionsDir

</div>

<div>

The following command creates an APK package for an Android device:

    adt -package
        -target apk
        -storetype pkcs12 -keystore ../codesign.p12
        myApp.apk
        myApp-app.xml
        myApp.swf icons
        -extdir extensionsDir

</div>

The following command creates an iOS package for an iPhone application:

    adt -package
        -target ipa-ad-hoc
        -storetype pkcs12 -keystore ../AppleDistribution.p12
        -provisioning-profile AppleDistribution.mobileprofile
        myApp.ipa
        myApp-app.xml
        myApp.swf icons Default.png
        -extdir extensionsDir

Note the following:

- Use a native installer package type.

- Specify the extension directory.

- Make sure that the ANE file supports the application’s target device.

<!-- -->

</div>

<div>

### Use a native installer package type

<div>

The application package must be a native installer. You cannot create a
cross-platform AIR package (a .air package) for an application that uses a
native extension, because native extensions usually contain native code.
However, typically a native extension supports multiple native platforms with
the same ActionScript APIs. In these cases, you can use the same ANE file in
different native installer packages.

The following table summarizes the value to use for the `-target` option of the
ADT command:

<div>

<div>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Application’s target platform</p></th>
<th><p>-target</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mac OS X or Windows desktop devices</p></td>
<td><p>-target native</p>
<p>-target bundle</p></td>
</tr>
<tr class="even">
<td><p>Android</p></td>
<td><p>-target apk</p>
<p>or other Android package targets.</p></td>
</tr>
<tr class="odd">
<td><p>iOS</p></td>
<td><p>-target ipa-ad-hoc</p>
<p>or other iOS package targets</p></td>
</tr>
<tr class="even">
<td><p>iOS Simulator</p></td>
<td><p>-target ipa-test-interpreter-simulator</p>
<p>-target ipa-debug-interpreter-simulator</p></td>
</tr>
</tbody>
</table>

</div>

</div>

</div>

</div>

<div>

### Specify the extension directory

<div>

Use the ADT option `-extdir`to tell ADT the directory that contains the native
extensions (ANE files).

For details about this option, see
[File and path options](WS901d38e593cd1bac1e63e3d128fc240122-7ff2.html).

</div>

</div>

<div>

### Make sure that the ANE file supports the application’s target device

<div>

When providing an ANE file, the native extension developer informs you which
platforms the extension supports. You can also use an archive extractor tool to
look at the contents of the ANE file. The extracted files include a directory
for each supported platform.

Knowing which platforms the extension supports is important when packaging the
application that uses the ANE file. Consider the following rules:

- To create an Android application package, the ANE file must include the
  `Android-ARM` platform. Alternatively, the ANE file must include the default
  platform and at least one other platform.

- To create an iOS application package, the ANE file must include the
  `iPhone-ARM` platform. Alternatively, the ANE file must include the default
  platform and at least one other platform.

- To create an iOS Simulator application package, the ANE file must include the
  `iPhone-x86` platform.

- To create a Mac OS X application package, the ANE file must include the
  `MacOS-x86`platform. Alternatively, the ANE file must include the default
  platform and at least one other platform.

- To create a Windows application package, the ANE file must include the
  `Windows-x86` platform. Alternatively, the ANE file must include the default
  platform and at least one other platform.

</div>

</div>

</div>

<div>

<div>

More Help topics

</div>

<div>

</div>

[About SWC files](http://www.adobe.com/go/learn_about_SWC_files_en "http://www.adobe.com/go/learn_about_SWC_files_en")

[AIR profile support](http://help.adobe.com/go/learn_air_app_profiles_en "http://help.adobe.com/go/learn_air_app_profiles_en")

<div>

</div>

</div>
