# AIR application descriptor elements

<div>

The following dictionary of elements describes each of the legal elements of an
AIR application descriptor file.

</div>

<div>

## allowBrowserInvocation

<div>

Enables the AIR in-browser API to detect and launch the application.

If you set this value to `true`, be sure to consider security implications.
These are described in
[Invoking an AIR application from the browser](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118676a5d46-8000.html#WS5b3ccc516d4fbf351e63e3d118666ade46-7e19)
(for ActionScript developers) and
[Invoking an AIR application from the browser](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118676a5d46-8000.html#WS5b3ccc516d4fbf351e63e3d118666ade46-7e19)
(for HTML developers).

For more information, see
[Launching an installed AIR application from the browser](WS5b3ccc516d4fbf351e63e3d118666ade46-7cd2.html).

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

`true` or `false` (default)

</div>

<div>

#### Example

    <allowBrowserInvocation>true</allowBrowserInvocation>

</div>

</div>

</div>

<div>

## android

<div>

Allows you to add elements to the Android manifest file. AIR creates the
AndroidManifest.xml file for every APK package. You can use the android element
in the AIR application descriptor to add additional items to it. Ignored on all
platforms except Android.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:**

- [colorDepth](WS54ddc2cc39d08a6245f46ba4132b124f13e-8000.html)

- [manifestAdditions](WSfffb011ac560372f33105f2a1293d3d21e0-7ffd.html)

<div>

#### Content

Elements defining the Android-specific properties to add to the Android
application manifest.

</div>

<div>

#### Example

    <android>
        <manifestAdditions>
            ...
        </manifestAdditions>
    </android>

</div>

</div>

</div>

<div>

## application

<div>

The root element of an AIR application descriptor document.

**Parent element:** none

**Child elements:**

- [allowBrowserInvocation](WSfffb011ac560372f2fea1812938a6e463-7fde.html)

- [android](WSfffb011ac560372f-6fd06f0f1293d3b33ea-8000.html)

- [copyright](WSfffb011ac560372f2fea1812938a6e463-7ff7.html)

- [customUpdateUI](WSfffb011ac560372f2fea1812938a6e463-7fdf.html)

- [description](WSfffb011ac560372f2fea1812938a6e463-7ff8.html)

- [extensions](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffd.html)

- [filename](WSfffb011ac560372f2fea1812938a6e463-7ff9.html)

- [fileTypes](WSfffb011ac560372f2fea1812938a6e463-7fdd.html)

- [icon](WSfffb011ac560372f2fea1812938a6e463-7ff6.html)

- [id](WSfffb011ac560372f2fea1812938a6e463-7ffe.html)

- [initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

- [installFolder](WSfffb011ac560372f2fea1812938a6e463-7fe1.html)

- [iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html)

- [name](WSfffb011ac560372f2fea1812938a6e463-7ffd.html)

- [programMenuFolder](WSfffb011ac560372f2fea1812938a6e463-7fe0.html)

- [publisherID](WS901d38e593cd1bac1e63e3d12939cc14ab-8000.html)

- [supportedLanguages](WS06ac295d95cf5a5c-4601cdc2134337a7308-8000.html)

- [supportedProfiles](WSfffb011ac560372f2fea1812938a6e463-7fe2.html)

- [version](WSfffb011ac560372f2fea1812938a6e463-7ffc.html)

- [versionLabel](WSfffb011ac560372f2fea1812938a6e463-7ffa.html)

- [versionNumber](WSfffb011ac560372f2fea1812938a6e463-7ffb.html)

<div>

#### Attributes

minimumPatchLevel — The AIR runtime minimum patch level required by this
application.

xmlns — the XML namespace attribute determines the required AIR runtime version
of the application.

The namespace changes with each major release of AIR (but not with minor
patches). The last segment of the namespace, such as “3.0,” indicates the
runtime version required by the application.

The xmlns values for the major AIR releases are:

    xmlns="http://ns.adobe.com/air/application/1.0"
    xmlns="http://ns.adobe.com/air/application/1.1"
    xmlns="http://ns.adobe.com/air/application/1.5"
    xmlns="http://ns.adobe.com/air/application/1.5.2"
    xmlns="http://ns.adobe.com/air/application/1.5.3"
    xmlns="http://ns.adobe.com/air/application/2.0"
    xmlns="http://ns.adobe.com/air/application/2.5"
    xmlns="http://ns.adobe.com/air/application/2.6"
    xmlns="http://ns.adobe.com/air/application/2.7"
    xmlns="http://ns.adobe.com/air/application/3.0"
    xmlns="http://ns.adobe.com/air/application/3.1"
    xmlns="http://ns.adobe.com/air/application/3.2"
    xmlns="http://ns.adobe.com/air/application/3,3"
    xmlns="http://ns.adobe.com/air/application/3.4"
    xmlns="http://ns.adobe.com/air/application/3.5"
    xmlns="http://ns.adobe.com/air/application/3.6"
    xmlns="http://ns.adobe.com/air/application/3.7"

For SWF-based applications, the AIR runtime version specified in the application
descriptor determines the maximum SWF version that can be loaded as the initial
content of the application. Applications that specify AIR 1.0 or AIR 1.1 can
only use SWF9 (Flash Player 9) files as initial content — even when run using
the AIR 2 runtime. Applications that specify AIR 1.5 (or later) can use either
SWF9 or SWF10 (Flash Player 10) files as initial content.

The SWF version determines which version of the AIR and Flash Player APIs are
available. If a SWF9 file is used as the initial content of an AIR 1.5
application, that application will only have access to the AIR 1.1 and Flash
Player 9 APIs. Furthermore, behavior changes made to existing APIs in AIR 2.0 or
Flash Player 10.1 will not be effective. (Important security-related changes to
APIs are an exception to this principle and can be applied retroactively in
present or future patches of the runtime.)

For HTML-based applications, the runtime version specified in the application
descriptor determines which version of the AIR and Flash Player APIs are
available to the application. The HTML, CSS, and JavaScript behaviors are always
determined by the version of Webkit used in the installed AIR runtime, not by
the application descriptor.

When an AIR application loads SWF content, the version of the AIR and Flash
Player APIs available to that content depends on how the content is loaded.
Sometimes the effective version is determined by the application descriptor
namespace, sometimes it is determined by the version of the loading content, and
sometimes it is determined by the version of the loaded content. The following
table shows how the API version is determined based on the loading method:

<div>

| How the content is loaded                                                                         | How the API version is determined  |
| ------------------------------------------------------------------------------------------------- | ---------------------------------- |
| Initial content, SWF-based application                                                            | SWF version of the **loaded** file |
| Initial content, HTML-based application                                                           | Application descriptor namespace   |
| SWF loaded by SWF content                                                                         | Version of the **loading** content |
| SWF library loaded by HTML content using \<script\> tag                                           | Application descriptor namespace   |
| SWF loaded by HTML content using AIR or Flash Player APIs (such as flash.display.Loader)          | Application descriptor namespace   |
| SWF loaded by HTML content using \<object\> or \<embed\> tags (or the equivalent JavaScript APIs) | SWF version of the **loaded** file |

</div>

When loading a SWF file of a different version than the loading content, you can
run into the two problems:

- Loading a newer version SWF by an older version SWF— References to APIs added
  in the newer versions of AIR and Flash Player in the loaded content will be
  unresolved

- Loading an older version SWF by a newer version SWF — APIs changed in the
  newer versions of AIR and Flash Player may behave in ways that the loaded
  content does not expect.

</div>

<div>

#### Content

The application element contains child elements that define the properties of an
AIR application.

</div>

<div>

#### Example

    <?xml version="1.0" encoding="utf-8" ?>
    <application xmlns="http://ns.adobe.com/air/application/3.0">
        <id>HelloWorld</id>
        <version>2.0</version>
        <filename>Hello World</filename>
        <name>Example Co. AIR Hello World</name>
         <description>
            <text xml:lang="en">This is an example.</text>
            <text xml:lang="fr">C'est un exemple.</text>
            <text xml:lang="es">Esto es un ejemplo.</text>
        </description>
        <copyright>Copyright (c) 2010 Example Co.</copyright>
        <initialWindow>
            <title>Hello World</title>
            <content>
                HelloWorld.swf
            </content>
            <systemChrome>none</systemChrome>
            <transparent>true</transparent>
            <visible>true</visible>
            <minSize>320 240</minSize>
        </initialWindow>
        <installFolder>Example Co/Hello World</installFolder>
        <programMenuFolder>Example Co</programMenuFolder>
        <icon>
            <image16x16>icons/smallIcon.png</image16x16>
            <image32x32>icons/mediumIcon.png</image32x32>
            <image48x48>icons/bigIcon.png</image48x48>
            <image128x128>icons/biggestIcon.png</image128x128>
        </icon>
        <customUpdateUI>true</customUpdateUI>
        <allowBrowserInvocation>false</allowBrowserInvocation>
        <fileTypes>
            <fileType>
                <name>adobe.VideoFile</name>
                <extension>avf</extension>
                <description>Adobe Video File</description>
                <contentType>application/vnd.adobe.video-file</contentType>
                <icon>
                    <image16x16>icons/avfIcon_16.png</image16x16>
                    <image32x32>icons/avfIcon_32.png</image32x32>
                    <image48x48>icons/avfIcon_48.png</image48x48>
                    <image128x128>icons/avfIcon_128.png</image128x128>
                </icon>
            </fileType>
        </fileTypes>
    </application>

</div>

</div>

</div>

<div>

## aspectRatio

<div>

Specifies the aspect ratio of the application.

If not specified, the application opens in the “natural” aspect ratio and
orientation of the device. The natural orientation varies from device to device.
Typically, it is the portrait aspect ratio on small-screen devices such as
phones. On some devices, such as the iPad tablet, the application opens in the
current orientation. In AIR 3.3 and higher, this applies to the entire
application, not just the initial display.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

`portrait, landscape`, or `any`

</div>

<div>

#### Example

    <aspectRatio>landscape</aspectRatio>

</div>

</div>

</div>

<div>

## autoOrients

<div>

Specifies whether the orientation of content in the application automatically
reorients as the device itself changes physical orientation. For more
information, see
[Stage orientation](http://help.adobe.com/en_US/as3/dev/WS901d38e593cd1bac3bf97f12ca4e5c567-8000.html).

When using auto-orientation, consider setting the `align` and `scaleMode`
properties of the Stage to the following:

    stage.align = StageAlign.TOP_LEFT;
    stage.scaleMode = StageScaleMode.NO_SCALE;

These settings allow the application to rotate around the top, left corner and
prevents your application content from being automatically scaled. While the
other scale modes do adjust your content to fit the rotated stage dimensions,
they also clip, distort, or excessively shrink that content. Better results can
almost always be achieved by redrawing or relaying out the content yourself.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

`true` or `false` (default)

</div>

<div>

#### Example

    <autoOrients>true</autoOrients>

</div>

</div>

</div>

<div>

## colorDepth

<div>

Specifies whether to use 16-bit or 32-bit color.

Using 16-bit color can increase rendering performance at the expense of color
fidelity. Prior to AIR 3, 16-bit color is always used on Android. In AIR 3,
32-bit color is used by default.

<div>

Note: If your application uses the StageVideo class, you must use 32-bit color.

</div>

**Parent element:**[android](WSfffb011ac560372f-6fd06f0f1293d3b33ea-8000.html)

**Child elements:** none

<div>

#### Content

One of the following values:

- 16bit

- 32bit

</div>

<div>

#### Example

    <android>
        <colorDepth>16bit</colorDepth>
        <manifestAdditions>...</manifestAdditions>
    </android>

</div>

</div>

</div>

<div>

## containsVideo

<div>

Specifies whether the application will contain any video content or not.

**Parent element:**[android](WSfffb011ac560372f-6fd06f0f1293d3b33ea-8000.html)

**Child elements:** none

<div>

#### Content

One of the following values:

- true

- false

</div>

<div>

#### Example

    <android>
        <containsVideo>true</containsVideo>
        <manifestAdditions>...</manifestAdditions>
    </android>

</div>

</div>

</div>

<div>

## content

<div>

The value specified for the `content` element is the URL for the main content
file of the application. This may be either a SWF file or an HTML file. The URL
is specified relative to the root of the application installation folder. (When
running an AIR application with ADL, the URL is relative to the folder
containing the application descriptor file. You can use the `root-dir` parameter
of ADL to specify a different root directory.)

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

A URL relative to the application directory. Because the value of the content
element is treated as a URL, characters in the name of the content file must be
URL encoded according to the rules defined in
[RFC 1738](http://tools.ietf.org/html/rfc1738). Space characters, for example,
must be encoded as `%20`.

</div>

<div>

#### Example

    <content>TravelPlanner.swf</content>

</div>

</div>

</div>

<div>

## contentType

<div>

`contentType` is required as of AIR 1.5 (it was optional in AIR 1.0 and 1.1).
The property helps some operating systems to locate the best application to open
a file. The value should be the MIME type of the file content. Note that the
value is ignored on Linux if the file type is already registered and has an
assigned MIME type.

**Parent element:**[fileType](WSfffb011ac560372f2fea1812938a6e463-7fdc.html)

**Child elements:** none

<div>

#### Content

The MIME type and subtype. See [RFC2045](http://www.ietf.org/rfc/rfc2045.txt)
for more information about MIME types.

</div>

<div>

#### Example

    <contentType>text/plain</contentType>

</div>

</div>

</div>

<div>

## copyright

<div>

The copyright information for the AIR application. On Mac OS, the copyright text
appears in the About dialog box for the installed application. On Mac OS, the
copyright information is also used in the NSHumanReadableCopyright field in the
Info.plist file for the application.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

A string containing the application copyright information.

</div>

<div>

#### Example

    <copyright>© 2010, Examples, Inc.All rights reserved.</copyright>

</div>

</div>

</div>

<div>

## customUpdateUI

<div>

Indicates whether an application will provide its own update dialogs. If
`false`, AIR presents standard update dialogs to the user. Only applications
distributed as AIR files can use the built-in AIR update system.

When the installed version of your application has the `customUpdateUI` element
set to `true` and the user then double-clicks the AIR file for a new version or
installs an update of the application using the seamless install feature, the
runtime opens the installed version of the application. The runtime does not
open the default AIR application installer. Your application logic can then
determine how to proceed with the update operation. (The application ID and
publisher ID in the AIR file must match the values in the installed application
for an upgrade to proceed.)

<div>

Note: The `customUpdateUI` mechanism only comes into play when the application
is already installed and the user double-clicks the AIR installation file
containing an update or installs an update of the application using the seamless
install feature. You can download and start an update through your own
application logic, displaying your custom UI as necessary, whether or not
`customUpdateUI` is `true`.

</div>

For more information, see
[Updating AIR applications](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff2.html).

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

`true` or `false` (default)

</div>

<div>

#### Example

    <customUpdateUI>true</customUpdateUI>

</div>

</div>

</div>

<div>

## depthAndStencil

<div>

Indicates that the application requires the use of the depth or stencil buffer.
You typically use these buffers when working with 3D content. By default, the
value of this element is `false` to disable the depth and stencil buffers. This
element is necessary because the buffers must be allocated on application
startup, before any content loads.

The setting of this element must match the value passed for the
`enableDepthAndStencil` argument to the `Context3D.configureBackBuffer()`
method. If the values do not match, AIR issues an error.

This element is only applicable when `renderMode` = `direct`. If `renderMode`
does not equal `direct`, ADT throws error 118:

<div>

    <depthAndStencil> element unexpected for render mode cpu.  It requires "direct" render mode.

</div>

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

`true` or `false` (default)

</div>

<div>

#### Example

    <depthAndStencil>true</depthAndStencil>

</div>

</div>

</div>

<div>

## description

<div>

The description of the application, displayed in the AIR application installer.

If you specify a single text node (not multiple text elements), the AIR
application installer uses this description, regardless of the system language.
Otherwise, the AIR application installer uses the description that most closely
matches the user interface language of the user’s operating system. For example,
consider an installation in which the `description` element of the application
descriptor file includes a value the en (English) locale. The AIR application
installer uses the en description if the user’s system identifies en (English)
as the user interface language. It also uses the en description if the system
user interface language is en-US (U.S. English). However, if system user
interface language is en-US and the application descriptor file defines both
en-US and en-GB names, then the AIR application installer uses the en-US value.
If the application defines no description that matches the system user interface
language, the AIR application installer uses the first `description` value
defined in the application descriptor file.

For more information on developing multi-language applications, see
[Localizing AIR applications](WSB2927578-20D8-4065-99F3-00ACE6511EEE.html).

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:**[text](WSfffb011ac560372f-1f98376f1293df83869-7ffa.html)

<div>

#### Content

The AIR 1.0 application descriptor schema allows only one simple text node to be
defined for the name (not multiple `text` elements).

In AIR 1.1 (or above), you can specify multiple languages in the `description`
element. The `xml:lang` attribute for each text element specifies a language
code, as defined in [RFC4646](http://www.ietf.org/rfc/rfc4646.txt)
(http://www.ietf.org/rfc/rfc4646.txt).

</div>

<div>

#### Example

Description with simple text node:

    <description>This is a sample AIR application.</description>

Description with localized text elements for English, French, and Spanish (valid
in AIR 1.1 and later):

    <description>
        <text xml:lang="en">This is an example.</text>
        <text xml:lang="fr">C'est un exemple.</text>
        <text xml:lang="es">Esto es un ejemplo.</text>
    </description>

</div>

</div>

</div>

<div>

## description

<div>

The file type description is displayed to the user by the operating system. The
file type description is not localizable.

See also: [description](WSfffb011ac560372f2fea1812938a6e463-7ff8.html) as child
of the application element

**Parent element:**[fileType](WSfffb011ac560372f2fea1812938a6e463-7fdc.html)

**Child elements:** none

<div>

#### Content

A string describing the file contents.

</div>

<div>

#### Example

    <description>PNG image</description>

</div>

</div>

</div>

<div>

<span id="embedFonts"></span>

## embedFonts

<div>

Allows you to use custom fonts on StageText in the AIR application. This element
is optional.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:**[font](font.html)

<div>

#### Content

The embedFonts element may contain any number of font elements.

</div>

<div>

#### Example

    <embedFonts>
       <font>
          <fontPath>ttf/space age.ttf</fontPath>
          <fontName>space age</fontName>
       </font>
       <font>
          <fontPath>ttf/xminus.ttf</fontPath>
          <fontName>xminus</fontName>
       </font>
    </embedFonts>

</div>

</div>

</div>

<div>

## Entitlements

<div>

iOS uses properties called entitlements to provide application access to
additional resources and capabilities. Use the Entitlements element to specify
this information in a mobile iOS application.

**Parent element:**[iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html)

**Child elements:** iOS Entitlements.plist elements

<div>

#### Content

Contains child elements specifying key-value pairs to use as Entitlements.plist
settings for the application. Content of the Entitlements element should be
enclosed in a CDATA block. For more information, see the
[Entitlement Key Reference](https://developer.apple.com/library/IOs/#documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html)
in the iOS Developer Library.

</div>

<div>

#### Example

    <iphone>
    ...
       <Entitlements>
          <![CDATA[
             <key>aps-environment</key>
             <string>development</string>
          ]]>
       </Entitlements>
    </iphone>

</div>

</div>

</div>

<div>

## extension

<div>

The extension string of a file type.

**Parent element:**[fileType](WSfffb011ac560372f2fea1812938a6e463-7fdc.html)

**Child elements:** none

<div>

#### Content

A string identifying the file extension characters (without the dot, “.”).

</div>

<div>

#### Example

    <extension>png</extension>

</div>

</div>

</div>

<div>

## extensionID

<div>

Specifies the ID of an ActionScript extension used by the application. The ID is
defined in the extension descriptor document.

**Parent
element:**[extensions](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffd.html)

**Child elements:** none

<div>

#### Content

A string identifying the ActionScript extension ID.

</div>

<div>

#### Example

    <extensionID>com.example.extendedFeature</extensionID>

</div>

</div>

</div>

<div>

## extensions

<div>

Identifies the ActionScript extensions used by an application.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:**[extensionID](WSfffb011ac560372f2fea1812938a6e463-7fda.html)

<div>

#### Content

Child `extensionID` elements containing the ActionScript extension IDs from the
extension descriptor file.

</div>

<div>

#### Example

    <extensions>
        <extensionID>extension.first</extensionID>
        <extensionID>extension.next</extensionID>
        <extensionID>extension.last</extensionID>
    </extensions>

</div>

</div>

</div>

<div>

## externalSwfs

<div>

Specifies the name of a text file that contains a list of SWFs to be configured
by ADT for remote hosting. You can minimize your initial application download
size by packaging a subset of the SWFs used by your application and loading the
remaining (asset-only) external SWFs at runtime using the `Loader.load()`
method. To use this feature, you must package the application such that ADT
moves all ActionScript ByteCode (ABC) from the externally loaded SWF files to
the main application SWF, leaving a SWF file that contains only assets. This is
to conform with the Apple Store’s rule that forbids downloading any code after
an application is installed.

For more information, see
[Minimize download size by loading external, asset-only SWFs](WS180fc5cb46642d107f85760613d88823106-8000.html).

**Parent element:**[iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html),
[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

Name of a text file that contains a line-delimited list of SWFs to be remotely
hosted.

</div>

<div>

#### Attributes:

None.

</div>

<div>

#### Examples

iOS:

    <iPhone>
        <externalSwfs>FileContainingListofSWFs.txt</externalSwfs>
    </iPhone>

</div>

</div>

</div>

<div>

## filename

<div>

The string to use as a filename of the application (without extension) when the
application is installed. The application file launches the AIR application in
the runtime. If no `name` value is provided, the `filename` is also used as the
name of the installation folder.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

The `filename` property can contain any Unicode (UTF-8) character except the
following, which are prohibited from use as filenames on various file systems:

<div>

| Character | Hexadecimal Code |
| --------- | ---------------- |
| _various_ | 0x00 – x1F       |
| \*        | x2A              |
| "         | x22              |
| :         | x3A              |
| \>        | x3C              |
| \<        | x3E              |
| ?         | x3F              |
| \\        | x5C              |
| \|        | x7C              |

</div>

The `filename` value cannot end in a period.

</div>

<div>

#### Example

    <filename>MyApplication</filename>

</div>

</div>

</div>

<div>

## fileType

<div>

Describes a single file type that the application can register for.

**Parent element:**[fileTypes](WSfffb011ac560372f2fea1812938a6e463-7fdd.html)

**Child elements:**

- [contentType](WSfffb011ac560372f2fea1812938a6e463-7fd8.html)

- [description](WSfffb011ac560372f2fea1812938a6e463-7fd9.html)

- [extension](WS901d38e593cd1bac1e63e3d12942101400-8000.html)

- [icon](WSfffb011ac560372f2fea1812938a6e463-7ff6.html)

- [name](WSfffb011ac560372f2fea1812938a6e463-7fdb.html)

<div>

#### Content

Elements describing a file type.

</div>

<div>

#### Example

    <fileType>
        <name>foo.example</name>
        <extension>foo</extension>
        <description>Example file type</description>
        <contentType>text/plain</contentType>
        <icon>
            <image16x16>icons/fooIcon16.png</image16x16>
            <image48x48>icons/fooIcon48.png</imge48x48>
        <icon>
    </fileType>

</div>

</div>

</div>

<div>

## fileTypes

<div>

The `fileTypes` element allows you to declare the file types with which an AIR
application can be associated.

When an AIR application is installed, any declared file type is registered with
the operating system. If these file types are not already associated with
another application, they are associated with the AIR application. To override
an existing association between a file type and another application, use the
`NativeApplication.setAsDefaultApplication()` method at run time (preferably
with the user’s permission).

<div>

Note: The runtime methods can only manage associations for the file types
declared in the application descriptor.

</div>

The `fileTypes` element is optional.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:**[fileType](WSfffb011ac560372f2fea1812938a6e463-7fdc.html)

<div>

#### Content

The `fileTypes` element may contain any number of `fileType` elements.

</div>

<div>

#### Example

    <fileTypes>
        <fileType>
            <name>adobe.VideoFile</name>
            <extension>avf</extension>
            <description>Adobe Video File</description>
            <contentType>application/vnd.adobe.video-file</contentType>
            <icon>
                <image16x16>icons/AIRApp_16.png</image16x16>
                <image32x32>icons/AIRApp_32.png</image32x32>
                <image48x48>icons/AIRApp_48.png</image48x48>
                <image128x128>icons/AIRApp_128.png</image128x128>
            </icon>
        </fileType>
    </fileTypes>

</div>

</div>

</div>

<div>

<span id="font"></span>

## font

<div>

Describes a single custom font that can be used in the AIR application.

**Parent element:**[embedFonts](embedFonts.html)

**Child elements:**[fontName](fontName.html), [fontPath](fontPath.html)

<div>

#### Content

Elements specifying the custom font name and its path.

</div>

<div>

#### Example

    <font>
       <fontPath>ttf/space age.ttf</fontPath>
       <fontName>space age</fontName>
    </font>

</div>

</div>

</div>

<div>

<span id="fontName"></span>

## fontName

<div>

Specifies the name of the custom font.

**Parent element:**[font](font.html)

**Child elements:** None

<div>

#### Content

Name of the custom font to be specified in StageText.fontFamily

</div>

<div>

#### Example

    <fontName>space age</fontName>

</div>

</div>

</div>

<div>

<span id="fontPath"></span>

## fontPath

<div>

Gives the location of the custom font file.

**Parent element:**[font](font.html)

**Child elements:** None

<div>

#### Content

Path of the custom font file (with respect to the source).

</div>

<div>

#### Example

    <fontPath>ttf/space age.ttf</fontPath>

</div>

</div>

</div>

<div>

## forceCPURenderModeForDevices

<div>

Force CPU render mode for a specified set of devices. This feature effectively
lets you selectively enable GPU render mode for the remaining iOS devices.

You add this tag as a child of the `iPhone` tag and specify a space-separated
list of device model names. Valid device model names include the following:

<div>

|         |           |          |
| ------- | --------- | -------- |
| iPad1,1 | iPhone1,1 | iPod1,1  |
| iPad2,1 | iPhone1,2 | iPod2,1  |
| iPad2,2 | iPhone2,1 | iPod3,3  |
| iPad2,3 | iPhone3.1 | iPod4,1  |
| iPad2,4 | iPhone3,2 | iPod 5,1 |
| iPad2,5 | iPhone4,1 |          |
| iPad3,1 | iPhone5,1 |          |
| iPad3,2 |           |          |
| iPad3,3 |           |          |
| iPad3,4 |           |          |

</div>

**Parent element:**[iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html),
[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

Space-separated list of device model names.

</div>

<div>

#### Attributes:

None.

</div>

<div>

#### Examples

iOS:

    ...
    <renderMode>GPU</renderMode>
    ...
    <iPhone>
    ...
       <forceCPURenderModeForDevices>iPad1,1 iPhone1,1 iPhone1,2 iPod1,1
       </forceCPURenderModeForDevices>
    </iPhone>

</div>

</div>

</div>

<div>

## fullScreen

<div>

Specifies whether the application starts up in fullscreen mode.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

`true` or `false` (default)

</div>

<div>

#### Example

    <fullscreen>true</fullscreen>

</div>

</div>

</div>

<div>

## height

<div>

The initial height of the main window of the application.

If you do not set a height, it is determined by the settings in the root SWF
file or, in the case of an HTML-based AIR application, by the operating system.

The maximum height of a window changed from 2048 pixels to 4096 pixels in AIR 2.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

A positive integer with a maximum value of 4095.

</div>

<div>

#### Example

    <height>4095</height>

</div>

</div>

</div>

<div>

## icon

<div>

The `icon` property specifies one or more icon files to be used for the
application. Including an icon is optional. If you do not specify an `icon`
property, the operating system displays a default icon.

The path specified is relative to the application root directory. Icon files
must be in the PNG format. You can specify all of the following icon sizes:

If an element for a given size is present, the image in the file must be exactly
the size specified. If all sizes are not provided, the closest size is scaled to
fit for a given use of the icon by the operating system.

<div>

Note: The icons specified are not automatically added to the AIR package. The
icon files must be included in their correct relative locations when the
application is packaged.

</div>

For best results, provide an image for each of the available sizes. In addition,
make sure that the icons look presentable in both 16- and 32-bit color modes.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:**[imageNxN](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html)

<div>

#### Content

An imageNxN element for each desired icon size.

</div>

<div>

#### Example

    <icon>
        <image16x16>icons/smallIcon.png</image16x16>
        <image32x32>icons/mediumIcon.png</image32x32>
        <image48x48>icons/bigIcon.png</image48x48>
        <image128x128>icons/biggestIcon.png</image128x128>
    </icon>

</div>

</div>

</div>

<div>

## id

<div>

An identifier string for the application, known as the application ID. A reverse
DNS-style identifier is often used, but this style is not required.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

The ID value is restricted to the following characters:

- 0–9

- a–z

- A–Z

- . (dot)

- \- (hyphen)

The value must contain 1 to 212 characters. This element is required.

</div>

<div>

#### Example

    <id>org.example.application</id>

</div>

</div>

</div>

<div>

## imageNxN

<div>

Defines the path to an icon relative to the application directory.

The following icon images can be used, each specifying a different icon size:

- image16x16

- image29x29 (AIR 2+)

- image32x32

- image36x36 (AIR 2.5+)

- image48x48

- image50x50 (AIR 3.4+)

- image57x57 (AIR 2+)

- image58x58 (AIR 3.4+)

- image72x72 (AIR 2+)

- image100x100 (AIR 3.4+)

- image114x114 (AIR 2.6+)

- image128x128

- image144x144 (AIR 3.4+)

- image512x512 (AIR 2+)

- image1024x1024 (AIR 3.4+)

The icon must be a PNG graphic that is exactly the size indicated by the image
element. Icon files must be included in the application package; icons
referenced in the application descriptor document are not included
automatically.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

The file path to the icon can contain any Unicode (UTF-8) character except the
following, which are prohibited from use as filenames on various file systems:

<div>

| Character | Hexadecimal Code |
| --------- | ---------------- |
| _various_ | 0x00 – x1F       |
| \*        | x2A              |
| "         | x22              |
| :         | x3A              |
| \>        | x3C              |
| \<        | x3E              |
| ?         | x3F              |
| \\        | x5C              |
| \|        | x7C              |

</div>

</div>

<div>

#### Example

    <image32x32>icons/icon32.png</image32x32>

</div>

</div>

</div>

<div>

## InfoAdditions

<div>

Allows you to specify additional properties of an iOS application.

**Parent element:**[iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html)

**Child elements:** iOS Info.plist elements

<div>

#### Content

Contains child elements specifying key-value pairs to use as Info.plist settings
for the application. Content of the InfoAdditions element should be enclosed in
a CDATA block.

See
[Information Property List Key Reference](http://developer.apple.com/iphone/library/documentation/General/Reference/InfoPlistKeyReference/index.html)
in the Apple iPhone Reference Library for information about the key value pairs
and how to express them in XML.

</div>

<div>

#### Example

    <InfoAdditions>
        <![CDATA[
            <key>UIStatusBarStyle</key>
            <string>UIStatusBarStyleBlackOpaque</string>
            <key>UIRequiresPersistentWiFi</key>
            <string>NO</string>
        ]]>
    </InfoAdditions>

</div>

</div>

</div>

<div>

## initialWindow

<div>

Defines the main content file and initial application appearance.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

<div>

**Child elements:** All of the following elements can appear as children of the
initialWindow element. However, some elements are ignored depending on whether
AIR supports windows on a platform:

<div>

| Element                                                                        | Desktop                   | Mobile  |
| ------------------------------------------------------------------------------ | ------------------------- | ------- |
| [aspectRatio](WSfffb011ac560372f2fea1812938a6e463-7fe6.html)                   | ignored                   | used    |
| [autoOrients](WSfffb011ac560372f2fea1812938a6e463-7fe5.html)                   | ignored                   | used    |
| [content](WSfffb011ac560372f2fea1812938a6e463-7ff4.html)                       | used                      | used    |
| [depthAndStencil](WS99d2e2affb7f39bd-2d75e77d134e7ea3560-8000.html)            | used                      | used    |
| [fullScreen](WSfffb011ac560372f2fea1812938a6e463-7fe4.html)                    | ignored                   | used    |
| [height](WSfffb011ac560372f2fea1812938a6e463-7fe9.html)                        | used                      | ignored |
| [maximizable](WSfffb011ac560372f2fea1812938a6e463-7fee.html)                   | used                      | ignored |
| [maxSize](WSfffb011ac560372f2fea1812938a6e463-7fe7.html)                       | used                      | ignored |
| [minimizable](WSfffb011ac560372f2fea1812938a6e463-7fef.html)                   | used                      | ignored |
| [minSize](WSfffb011ac560372f2fea1812938a6e463-7fe8.html)                       | used                      | ignored |
| [renderMode](WSfffb011ac560372f2fea1812938a6e463-7fe3.html)                    | used (AIR 3.0 and higher) | used    |
| [requestedDisplayResolution](WSfffb011ac560372f-4cb7055d12d779150e8-8000.html) | used (AIR 3.6 and higher) | ignored |
| [resizable](WSfffb011ac560372f2fea1812938a6e463-7fed.html)                     | used                      | ignored |
| [softKeyboardBehavior](WSfffb011ac560372f1a6f6f1912d7748050e-7fff.html)        | ignored                   | used    |
| [systemChrome](WSfffb011ac560372f2fea1812938a6e463-7ff2.html)                  | used                      | ignored |
| [title](WSfffb011ac560372f2fea1812938a6e463-7ff3.html)                         | used                      | ignored |
| [transparent](WSfffb011ac560372f2fea1812938a6e463-7ff1.html)                   | used                      | ignored |
| [visible](WSfffb011ac560372f2fea1812938a6e463-7ff0.html)                       | used                      | ignored |
| [width](WSfffb011ac560372f2fea1812938a6e463-7fea.html)                         | used                      | ignored |
| [x](WSfffb011ac560372f2fea1812938a6e463-7fec.html)                             | used                      | ignored |
| [y](WSfffb011ac560372f2fea1812938a6e463-7feb.html)                             | used                      | ignored |

</div>

</div>

<div>

#### Content

Child elements defining the application appearance and behavior.

</div>

<div>

#### Example

    <initialWindow>
        <title>Hello World</title>
        <content>
            HelloWorld.swf
        </content>
        <depthAndStencil>true</depthAndStencil>
        <systemChrome>none</systemChrome>
        <transparent>true</transparent>
        <visible>true</visible>
        <maxSize>1024 800</maxSize>
        <minSize>320 240</minSize>
        <maximizable>false</maximizable>
        <minimizable>false</minimizable>
        <resizable>true</resizable>
        <x>20</x>
        <y>20</y>
        <height>600</height>
        <width>800</width>
        <aspectRatio>landscape</aspectRatio>
        <autoOrients>true</autoOrients>
        <fullScreen>false</fullScreen>
        <renderMode>direct</renderMode>
    </initialWindow>

</div>

</div>

</div>

<div>

## installFolder

<div>

Identifies the subdirectory of the default installation directory.

On Windows, the default installation subdirectory is the Program Files
directory. On Mac OS, it is the /Applications directory. On Linux, it is /opt/.
For example, if the `installFolder` property is set to `"Acme"` and an
application is named `"ExampleApp"`, then the application is installed in
C:\Program Files\Acme\ExampleApp on Windows, in /Applications/Acme/Example.app
on MacOS, and /opt/Acme/ExampleApp on Linux.

The `installFolder` property is optional. If you specify no `installFolder`
property, the application is installed in a subdirectory of the default
installation directory, based on the `name` property.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** None

<div>

#### Content

The `installFolder` property can contain any Unicode (UTF-8) character except
those that are prohibited from use as folder names on various file systems (see
the `filename` property for the list of exceptions).

Use the forward-slash (/) character as the directory separator character if you
want to specify a nested subdirectory.

</div>

<div>

#### Example

    <installFolder>utilities/toolA</installFolder>

</div>

</div>

</div>

<div>

## iPhone

<div>

Defines iOS-specific application properties.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

<div>

**Child elements:**

- [Entitlements](WSd6d4f896b3a8801b-3c9d92f81393051c54c-8000.html)

- [externalSwfs](WS180fc5cb46642d105c891f2413da22fbc8f-8000.html)

- [forceCPURenderModeForDevices](WS180fc5cb46642d10-3a65697f13da2342af2-8000.html)

- [InfoAdditions](WSfffb011ac560372f2fea1812938a6e463-7fd5.html)

- [requestedDisplayResolution](WSfffb011ac560372f-4cb7055d12d779150e8-8000.html)

</div>

</div>

</div>

<div>

## manifest

<div>

Specifies information to add to the Android manifest file for the application.

**Parent
element:**[manifestAdditions](WSfffb011ac560372f33105f2a1293d3d21e0-7ffd.html)

**Child elements:** Defined by the Android SDK.

<div>

#### Content

The manifest element is not, technically speaking, a part of the AIR application
descriptor schema. It is the root of the Android manifest XML document. Any
content that you put within the manifest element must conform to the
AndroidManifest.xml schema. When you generate an APK file with the AIR tools,
information in the manifest element is copied into the corresponding part of the
generated AndroidManifest.xml of the application.

If you specify Android manifest values that are only available in an SDK version
more recent than that directly supported by AIR, then you must set the
`‑platformsdk` flag to ADT when packaging the app. Set the flag to the file
system path to a version of Android SDK which supports the values that you are
adding.

The manifest element itself must be enclosed in a CDATA block within the AIR
application descriptor.

</div>

<div>

#### Example

    <![CDATA[
        <manifest android:sharedUserID="1001">
            <uses-permission android:name="android.permission.CAMERA"/>
            <uses-feature android:required="false" android:name="android.hardware.camera"/>
            <application     android:allowClearUserData="true"
                        android:enabled="true"
                        android:persistent="true"/>
        </manifest>
    ]]>

</div>

</div>

</div>

<div>

## manifestAdditions

<div>

Specifies information to add to the Android manifest file.

Every Android application includes a manifest file that defines basic
application properties. The Android manifest is similar in concept to the AIR
application descriptor. An AIR for Android application has both an application
descriptor and an automatically generated Android manifest file. When an AIR for
Android app is packaged, the information in this `manifestAdditions` element is
added to the corresponding parts of the Android manifest document.

**Parent element:**[android](WSfffb011ac560372f-6fd06f0f1293d3b33ea-8000.html)

**Child elements:**[manifest](WSfffb011ac560372f33105f2a1293d3d21e0-7ffe.html)

<div>

#### Content

Information in the `manifestAdditions` element is added to the AndroidManifest
XML document.

AIR sets several manifest entries in the generated Android manifest document to
ensure that application and runtime features work correctly. You cannot override
the following settings:

You cannot set the following attributes of the manifest element:

- package

- android:versionCode

- android:versionName

You cannot set the following attributes for the main activity element:

- android:label

- android:icon

You cannot set the following attributes of the application element:

- android:theme

- android:name

- android:label

- android:windowSoftInputMode

- android:configChanges

- android:screenOrientation

- android:launchMode

</div>

<div>

#### Example

    <manifestAdditions>
        <![CDATA[
            <manifest android:installLocation="preferExternal">
                <uses-permission android:name="android.permission.INTERNET"/>
                <application     android:allowClearUserData="true"
                            android:enabled="true"
                            android:persistent="true"/>
            </manifest>
        ]]>
    </manifestAdditions>

</div>

</div>

</div>

<div>

## maximizable

<div>

Specifies whether the window can be maximized.

<div>

Note: On operating systems, such as Mac OS X, for which maximizing windows is a
resizing operation, both maximizable and resizable must be set to `false` to
prevent the window from being zoomed or resized.

</div>

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

`true` (default) or `false`

</div>

<div>

#### Example

    <maximizable>false</maximizable>

</div>

</div>

</div>

<div>

## maxSize

<div>

The maximum sizes of the window. If you do not set a maximum size, it is
determined by the operating system.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

Two integers representing the maximum width and height, separated by whites
pace.

<div>

Note: The maximum window size supported by AIR increased from 2048x2048 pixels
to 4096x4096 pixels in AIR 2. (Because the screen coordinates are zero-based,
the maximum value you can use for width or height is 4095.)

</div>

</div>

<div>

#### Example

    <maxSize>1024 360</maxSize>

</div>

</div>

</div>

<div>

## minimizable

<div>

Specifies whether the window can be minimized.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** None

<div>

#### Content

`true` (default) or `false`

</div>

<div>

#### Example

    <minimizable>false</minimizable>

</div>

</div>

</div>

<div>

## minSize

<div>

Specifies the minimum size allowed for the window.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

Two integers representing the minimum width and height, separated by whites
pace. Note that the minimum size imposed by the operating system takes
precedence over the value set in the application descriptor.

</div>

<div>

#### Example

    <minSize>120 60</minSize>

</div>

</div>

</div>

<div>

## name

<div>

The application title displayed by the AIR application installer.

If no `name` element is specified, the AIR application installer displays the
`filename` as the application name.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:**[text](WSfffb011ac560372f-1f98376f1293df83869-7ffa.html)

<div>

#### Content

If you specify a single text node (instead of multiple `<text>` elements), the
AIR application installer uses this name, regardless of the system language.

The AIR 1.0 application descriptor schema allows only one simple text node to be
defined for the name (not multiple `text` elements). In AIR 1.1 (or above), you
can specify multiple languages in the `name` element.

The `xml:lang` attribute for each text element specifies a language code, as
defined in [RFC4646](http://www.ietf.org/rfc/rfc4646.txt)
(http://www.ietf.org/rfc/rfc4646.txt).

The AIR application installer uses the name that most closely matches the user
interface language of the user’s operating system. For example, consider an
installation in which the `name` element of the application descriptor file
includes a value for the en (English) locale. The AIR application installer uses
the en name if the operating system identifies en (English) as the user
interface language. It also uses the en name if the system user interface
language is en-US (U.S. English). However, if the user interface language is
en-US and the application descriptor file defines both en-US and en-GB names,
then the AIR application installer uses the en-US value. If the application
defines no name that matches the system user interface languages, the AIR
application installer uses the first `name` value defined in the application
descriptor file.

The `name` element only defines the application title used in the AIR
application installer. The AIR application installer supports multiple
languages: Traditional Chinese, Simplified Chinese, Czech, Dutch, English,
French, German, Italian, Japanese, Korean, Polish, Brazilian Portuguese,
Russian, Spanish, Swedish, and Turkish. The AIR application installer selects
its displayed language (for text other than the application title and
description) based on the system user interface language. This language
selection is independent of the settings in the application descriptor file.

The `name` element does _not_ define the locales available for the running,
installed application. For details on developing multi-language applications,
see [Localizing AIR applications](WSB2927578-20D8-4065-99F3-00ACE6511EEE.html).

</div>

<div>

#### Example

The following example defines a name with a simple text node:

    <name>Test Application</name>

The following example, valid in AIR 1.1 and later, specifies the name in three
languages (English, French, and Spanish) using \<text\> element nodes:

    <name>
        <text xml:lang="en">Hello AIR</text>
        <text xml:lang="fr">Bonjour AIR</text>
        <text xml:lang="es">Hola AIR</text>
    </name>

</div>

</div>

</div>

<div>

## name

<div>

Identifies the name of a file type.

**Parent element:**[fileType](WSfffb011ac560372f2fea1812938a6e463-7fdc.html)

**Child elements:** none

<div>

#### Content

A string representing the name of the file type.

</div>

<div>

#### Example

    <name>adobe.VideoFile</name>

</div>

</div>

</div>

<div>

## programMenuFolder

<div>

Identifies the location in which to place shortcuts to the application in the
All Programs menu of the Windows operating system or in the Applications menu on
Linux. (This setting is currently ignored on other operating systems.)

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

The string used for the `programMenuFolder` value can contain any Unicode
(UTF-8) character except those that are prohibited from use as folder names on
various file systems (see the `filename` element for the list of exceptions). Do
_not_ use a forward slash (/) character as the last character of this value.

</div>

<div>

#### Example

    <programMenuFolder>Example Company/Sample Application</programMenuFolder>

</div>

</div>

</div>

<div>

## publisherID

<div>

Identifies the publisher ID for updating an AIR application originally created
with AIR version 1.5.2 or earlier.

Only specify a publisher ID when creating an application update. The value of
the `publisherID` element must match the publisher ID generated by AIR for the
earlier version of the application. For an installed application, the publisher
ID can be found in the folder in which an application is installed, in the
`META-INF/AIR/publisherid` file.

New applications created with AIR 1.5.3 or later should not specify a publisher
ID.

For more information, see
[About AIR publisher identifiers](WS5b3ccc516d4fbf351e63e3d118666ade46-7cca.html).

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

A publisher ID string.

</div>

<div>

#### Example

    <publisherID>B146A943FBD637B68C334022D304CEA226D129B4.1</publisherID>

</div>

</div>

</div>

<div>

## renderMode

<div>

Specifies whether to use graphics processing unit (GPU) acceleration, if
supported on the current computing device.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

One of the following values:

- `auto` (default) — currently falls back to CPU mode.

- `cpu` — hardware acceleration is not used.

- `direct` — rendering composition occurs in the CPU; blitting uses the GPU.
  Available in AIR 3+.

  <div>

  Note: In order to leverage GPU acceleration of Flash content with AIR for
  mobile platforms, Adobe recommends that you use renderMode="direct" (that is,
  Stage3D) rather than renderMode="gpu". Adobe officially supports and
  recommends the following Stage3D based frameworks: Starling (2D) and Away3D
  (3D). For more details on Stage3D and Starling/Away3D, see
  <http://gaming.adobe.com/getstarted/>.

  </div>

- `gpu` — hardware acceleration is used, if available.

  <div>

  Important: Do not use GPU rendering mode for Flex applications.

  </div>

</div>

<div>

#### Example

    <renderMode>direct</renderMode>

</div>

</div>

</div>

<div>

## requestedDisplayResolution

<div>

Specifies whether the application desires to use the standard or high resolution
on a device or computer monitor with a high-resolution screen. When set to
_standard_, the default, the screen will appear to the application as a
standard-resolution screen. When set to _high_, the application can address each
high-resolution pixel.

For example, on a 640x960 high-resolution iPhone screen, if the setting is
_standard_ the fullscreen stage dimensions are 320x480, and each application
pixel is rendered using four screen pixels. If the setting is _high_, the
fullscreen stage dimensions are 640x960.

On devices with standard-resolution screens, the stage dimensions match the
screen dimensions no matter which setting is used.

If the `requestedDisplayResolution` element is nested in the `iPhone` element,
it applies to iOS devices. In that case, the `excludeDevices` attribute can be
used to specify devices for which the setting is not applied.

If the `requestedDisplayResolution` element is nested in the `initialWindow`
element, it applies to desktop AIR applications on MacBook Pro computers that
support high-resolution displays. The specified value applies to all native
windows used in the application. Nesting the `requestedDisplayResolution`
element in the `initialWindow` element is supported in AIR 3.6 and later.

**Parent element:**[iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html),
[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

Either _standard_, the default, or _high_.

</div>

<div>

#### Attribute:

excludeDevices — a space-separated list of iOS model names or model name
prefixes. This allows the developer to have some devices use high resolution and
others use standard resolution. This attribute is only available on iOS (the
`requestedDisplayResolution` element is nested in the `iPhone` element). The
`excludeDevices` attribute is available in AIR 3.6 and later.

For any device whose model name is specified in this attribute, the
`requestedDisplayResolution` value is the opposite of the specified value. In
other words, if the `requestedDisplayResolution` value is _high_, the excluded
devices use standard resolution. If the `requestedDisplayResolution` value is
_standard_, the excluded devices use high resolution.

The values are iOS device model names or model name prefixes. For example, the
value iPad3,1 refers specificially to a Wi-Fi 3rd-generation iPad (but not GSM
or CDMA 3rd-generation iPads). Alternatively, the value iPad3 refers to any
3rd-generation iPad. An unofficial list of iOS model names is available at
[the iPhone wiki Models page](http://theiphonewiki.com/wiki/Models).

</div>

<div>

#### Examples

Desktop:

    <initialWindow>
        <requestedDisplayResolution>high</requestedDisplayResolution>
    </initialWindow>

iOS:

    <iPhone>
        <requestedDisplayResolution excludeDevices="iPad3 iPad4">high</requestedDisplayResolution>
    </iPhone>

</div>

</div>

</div>

<div>

## resizable

<div>

Specifies whether the window can be resized.

<div>

Note: On operating systems, such as Mac OS X, for which maximizing windows is a
resizing operation, both maximizable and resizable must be set to `false` to
prevent the window from being zoomed or resized.

</div>

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:**

<div>

#### Content

`true` (default) or `false`

</div>

<div>

#### Example

    <resizable>false</resizable>

</div>

</div>

</div>

<div>

## softKeyboardBehavior

<div>

Specifies the default behavior of the application when a virtual keyboard is
displayed. The default behavior is to pan the application upward. The runtime
keeps the focused text field or interactive object on the screen. Use the _pan_
option if your application does not provide its own keyboard handling logic.

You can also turn off the automatic behavior by setting the
`softKeyboardBehavior` element to _none_. In this case, text fields and
interactive objects dispatch a SoftKeyboardEvent when the soft keyboard is
raised, but the runtime does not pan or resize the application. It is your
application’s responsibility to keep the text entry area in view.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

Either _none_ or _pan_. The default value is _pan_.

</div>

<div>

#### Example

    <softKeyboardBehavior>none</softKeyboardBehavior>

</div>

</div>

</div>

<div>

## supportedLanguages

<div>

Identifies the languages supported by the application. This element is only used
by iOS, Mac captive runtime, and Android applications. This element is ignored
by all other application types.

If you do not specify this element, then by default the packager performs the
following actions based on the application type:

<div>

- iOS — All languages supported by the AIR runtime are listed in the iOS app
  store as supported languages of the application.

- Mac captive runtime — Application packaged with captive bundle has no
  localization information.

- Android — Application bundle has resources for all languages supported by the
  AIR runtime.

</div>

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

A space delimited list of supported languages. Valid language values are
ISO 639‑1 values for the languages supported by the AIR runtime: `en`, `de`,
`es`, `fr`, `it`, `ja`, `ko`, `pt`, `ru`, `cs`, `nl`, `pl`, `sv`, `tr`, `zh`,
`da`, `nb`, `iw`.

The packager generates an error for an empty value for the
`<supportedLanguages>` element.

<div>

<div>

Note: Localized tags (such as the name tag) ignore the value of a language if
you use the `<supportedLanguages>` tag and it does not contain that language. If
a native extension has resources for a language which is not specified by the
`<supportedLangauges>` tag, a warning is issued and the resources are ignored
for that language.

</div>

</div>

</div>

<div>

#### Example

    <supportedLanguages>en ja fr es</supportedLanguages>

</div>

</div>

</div>

<div>

## supportedProfiles

<div>

Identifies the profiles that are supported for the application.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

You can include any of these values in the `supportedProfiles` element:

<div>

- `desktop`—The desktop profile is for AIR applications that are installed on a
  desktop computer using an AIR file. These applications do not have access to
  the NativeProcess class (which provides communication with native
  applications).

- `extendedDesktop`—The extended desktop profile is for AIR applications that
  are installed on a desktop computer using a native application installer.
  These applications have access to the NativeProcess class (which provides
  communication with native applications).

- `mobileDevice`—The mobile device profile is for mobile applications.

- `extendedMobileDevice`—The extended mobile device profile is not currently in
  use.

</div>

The `supportedProfiles` property is optional. When you do not include this
element in the application descriptor file, the application can be compiled and
deployed for any profile.

To specify multiple profiles, separate each with a space character. For example,
the following setting specifies that the application is only available in the
desktop and extended profiles:

    <supportedProfiles>desktop extendedDesktop</supportedProfiles>

<div>

Note: When you run an application with ADL and do not specify a value for the
ADL `-profile` option, then the first profile in the application descriptor is
used. (If no profiles are specified in the application descriptor either, then
the desktop profile is used.)

</div>

</div>

<div>

#### Example

    <supportedProfiles>desktop mobileDevice</supportedProfiles>

</div>

</div>

</div>

<div>

## systemChrome

<div>

Specifies whether the initial application window is created with the standard
title bar, borders, and controls provided by the operating system.

The system chrome setting of the window cannot be changed at run time.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

One of the following values:

- `none` — No system chrome is provided. The application (or an application
  framework such as Flex) is responsible for displaying window chrome.

- `standard` (default) — System chrome is provided by the operating system.

</div>

<div>

#### Example

    <systemChrome>standard</systemChrome>

</div>

</div>

</div>

<div>

## text

<div>

Specifies a localized string.

The `xml:lang` attribute of a text element specifies a language code, as defined
in [RFC4646](http://www.ietf.org/rfc/rfc4646.txt)
(http://www.ietf.org/rfc/rfc4646.txt).

The AIR application installer uses the `text` element with the `xml:lang`
attribute value that most closely matches the user interface language of the
user’s operating system.

For example, consider an installation in which a `text` element includes a value
for the en (English) locale. The AIR application installer uses the en name if
the operating system identifies en (English) as the user interface language. It
also uses the en name if the system user interface language is en-US (U.S.
English). However, if the user interface language is en-US and the application
descriptor file defines both en-US and en-GB names, then the AIR application
installer uses the en-US value.

If the application defines no `text` element that matches the system user
interface languages, the AIR application installer uses the first `name` value
defined in the application descriptor file.

<div>

**Parent elements:**

- [name](WSfffb011ac560372f2fea1812938a6e463-7ffd.html)

- [description](WSfffb011ac560372f2fea1812938a6e463-7ff8.html)

</div>

**Child elements:** none

<div>

#### Content

An `xml:lang` attribute specifying a locale and a string of localized text.

</div>

<div>

#### Example

    <text xml:lang="fr">Bonjour AIR</text>

</div>

</div>

</div>

<div>

## title

<div>

Specifies the title displayed in the title bar of the initial application
window.

A title is only displayed if the `systemChrome` element is set to `standard`.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

A string containing the window title.

</div>

<div>

#### Example

    <title>Example Window Title</title>

</div>

</div>

</div>

<div>

## transparent

<div>

Specifies whether the initial application window is alpha-blended with the
desktop.

A window with transparency enabled may draw more slowly and require more memory.
The transparent setting cannot be changed at run time.

<div>

Important: You can only set `transparent` to `true` when `systemChrome` is
`none`_._

</div>

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

`true` or `false` (default)

</div>

<div>

#### Example

    <transparent>true</transparent>

</div>

</div>

</div>

<div>

## version

<div>

Specifies the version information for the application.

The version string is an application-defined designator. AIR does not interpret
the version string in any way. Thus, version “3.0” is not assumed to be more
current than version “2.0.” Examples: `"1.0"`, "`.4"`, "`0.5`", `"4.9"`,
`"1.3.4a"`.

In AIR 2.5 and later, the `version` element is superseded by the `versionNumber`
and `versionLabel` elements.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

A string containing the application version.

</div>

<div>

#### Example

    <version>0.1 Alpha</version>

</div>

</div>

</div>

<div>

## versionLabel

<div>

Specifies a human-readable version string.

The value of the version label is displayed in installation dialogs instead of
the value of the `versionNumber` element. If `versionLabel` is not used, then
the `versionNumber` is used for both.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

A string containing the publicly displayed version text.

</div>

<div>

#### Example

    <versionLabel>0.9 Beta</versionlabel>

</div>

</div>

</div>

<div>

## versionNumber

<div>

The application version number.

**Parent element:**[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

**Child elements:** none

<div>

#### Content

The version number can contain a sequence of up to three integers separated by
periods. Each integer must be a number between 0 and 999 (inclusive).

</div>

<div>

#### Examples

    <versionNumber>1.0.657</versionNumber>

    <versionNumber>10</versionNumber>

    <versionNumber>0.01</versionNumber>

</div>

</div>

</div>

<div>

## visible

<div>

Specifies whether the initial application window is visible as soon as it is
created.

AIR windows, including the initial window, are created in an invisible state by
default. You can display a window by calling the `activate()` method of the
NativeWindow object or by setting the `visible` property to `true`. You may want
to leave the main window hidden initially, so that changes to the window’s
position, the window’s size, and the layout of its contents are not shown.

The Flex `mx:WindowedApplication` component automatically displays and activates
the window immediately before the `applicationComplete` event is dispatched,
unless the `visible` attribute is set to `false` in the MXML definition.

On devices in the mobile profile, which does not support windows, the visible
setting is ignored.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

`true` or `false` (default)

</div>

<div>

#### Example

    <visible>true</visible>

</div>

</div>

</div>

<div>

## width

<div>

The initial width of the main window of the application.

If you do not set a width, it is determined by the settings in the root SWF file
or, in the case of an HTML-based AIR application, by the operating system.

The maximum width of a window changed from 2048 pixels to 4096 pixels in AIR 2.

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

A positive integer with a maximum value of 4095.

</div>

<div>

#### Example

    <width>1024</width>

</div>

</div>

</div>

<div>

## x

<div>

The horizontal position of the initial application window.

In most cases, it is better to let the operating system determine the initial
position of the window rather than assigning a fixed value.

The origin of the screen coordinate system (0,0) is the top, left-hand corner of
the main desktop screen (as determined by the operating system).

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

An integer value.

</div>

<div>

#### Example

    <x>120</x>

</div>

</div>

</div>

<div>

## y

<div>

The vertical position of the initial application window.

In most cases, it is better to let the operating system determine the initial
position of the window rather than assigning a fixed value.

The origin of the screen coordinate system (0,0) is the top, left-hand corner of
the main desktop screen (as determined by the operating system).

**Parent
element:**[initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)

**Child elements:** none

<div>

#### Content

An integer value.

</div>

<div>

#### Example

    <y>250</y>

</div>

</div>

</div>

<div>

<div>

More Help topics

</div>

<div>

[Android settings](WSfffb011ac560372f-5d0f4f25128cc9cd0cb-7ffc.html)

[iOS Settings](WSfffb011ac560372f7e64a7f12cd2dd1867-8000.html)

[Device profiles](WS144092a96ffef7cc16ddeea2126bb46b82f-8000.html)

[Supported profiles](WS901d38e593cd1bac1e63e3d12991865ede-8000.html)

</div>

[The AndroidManifest.xml File](http://developer.android.com/guide/topics/manifest/manifest-intro.html "http://developer.android.com/guide/topics/manifest/manifest-intro.html")

![](../img/flashplatformLinkIndicator.png) 
[SoftKeyboardEvent](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/SoftKeyboardEvent.html "http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/SoftKeyboardEvent.html")

<div>

</div>

</div>
