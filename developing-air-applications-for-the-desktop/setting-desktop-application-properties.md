# Setting desktop application properties

Set the basic application properties in the application descriptor file. This
section covers the properties relevant to desktop AIR applications. The elements
of the application descriptor file are fully described in
[AIR application descriptor files](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html).

## Required AIR runtime version

Specify the version of the AIR runtime required by your application using the
namespace of the application descriptor file.

The namespace, assigned in the `application` element, determines, in large part,
which features your application can use. For example, if your application uses
the AIR 1.5 namespace, and the user has AIR 3.0 installed, then your application
sees the AIR 1.5 behavior (even if the behavior has been changed in AIR 3.0).
Only when you change the namespace and publish an update will your application
have access to the new behavior and features. Security and WebKit changes are
the primary exceptions to this policy.

Specify the namespace using the xmlns attribute of the root `application`
element:

    <application xmlns="http://ns.adobe.com/air/application/3.0">

## Application identity

Several settings should be unique for each application that you publish. The
unique settings include the ID, the name, and the filename.

    <id>com.example.MyApplication</id>
    <name>My Application</name>
    <filename>MyApplication</filename>

## Application version

In versions of AIR earlier than AIR 2.5, specify the application in the
`version` element. You can use any string. The AIR runtime does not interpret
the string; "2.0" is not treated as a higher version than "1.0."

    <!-- AIR 2 or earlier -->
    <version>1.23 Beta 7</version>

In AIR 2.5 and later, specify the application version in the `versionNumber`
element. The `version` element can no longer be used. When specifying a value
for `versionNumber`, you must use a sequence of up to three numbers separated by
dots, such as: "0.1.2". Each segment of the version number can have up to three
digits. (In other words, "999.999.999" is the largest version number permitted.)
You do not have to include all three segments in the number; "1" and "1.0" are
legal version numbers as well.

You can also specify a label for the version using the `versionLabel` element.
When you add a version label, it is displayed instead of the version number in
such places as the AIR application installer dialogs.

    <!-- AIR 2.5 and later -->
    <versionNumber>1.23.7<versionNumber>
    <versionLabel>1.23 Beta 7</versionLabel>

## Main window properties

When AIR starts an application on the desktop, it creates a window and loads the
main SWF file or HTML page into it. AIR uses the child elements of the
`initialWindow` element control the initial appearance and behavior of this
initial application window.

- **content** — The main application SWF file in the `content` child of the
  `initalWindow` element. When you target devices in the desktop profile, you
  can use a SWF or an HTML file.

      <initialWindow>
          <content>MyApplication.swf</content>
      </initialWindow>

  You must include the file in the AIR package (using ADT or your IDE). Simply
  referencing the name in the application descriptor does not cause the file to
  be included in the package automatically.

- **depthAndStencil** — Specifies to use the depth or stencil buffer. You
  typically use these buffers when working with 3D content.

      <depthAndStencil>true</depthAndStencil>

- **height** — The height of the initial window.

- **maximizable** — Whether the system chrome for maximizing the window is
  shown.

- **maxSize** — The maximum size allowed.

- **minimizable** — Whether the system chrome for minimizing the window is
  shown.

- **minSize** — The minimum size allowed.

- **renderMode** — In AIR 3 or later, the render mode can be set to _auto_,
  _cpu_, _direct_, or _gpu_ for desktop applications. In earlier versions of
  AIR, this setting is ignored on desktop platforms. The renderMode setting
  cannot be changed at run time.

  - auto — essentially the same as cpu mode.

  - cpu — display objects are rendered and copied to display memory in software.
    StageVideo is only available when a window is in fullscreen mode. Stage3D
    uses the software renderer.

  - direct — display objects are rendered by the runtime software, but copying
    the rendered frame to display memory (blitting) is hardware accelerated.
    StageVideo is available. Stage3D uses hardware acceleration, if otherwise
    possible. If window transparency is set to true, then the window "falls
    back" to software rendering and blitting.

    > **Note:** In order to leverage GPU acceleration of Flash content with AIR
    > for mobile platforms, Adobe recommends that you use renderMode="direct"
    > (that is, Stage3D) rather than renderMode="gpu". Adobe officially supports
    > and recommends the following Stage3D based frameworks: Starling (2D) and
    > Away3D (3D). For more details on Stage3D and Starling/Away3D, see
    > <http://gaming.adobe.com/getstarted/>.

  - gpu — hardware acceleration is used, if available.

- **requestedDisplayResolution** — Whether your application should use the
  _standard_ or _high_ resolution mode on MacBook Pro computers with
  high-resolution screens. On all other platforms the value is ignored. If the
  value is _standard_, each stage pixel renders as four pixels on the screen. If
  the value is _high_, each stage pixel corresponds to a single physical pixel
  on the screen. The specified value is used for all application windows. Using
  the `requestedDisplayResolution` element for desktop AIR applications (as a
  child of the `intialWindow` element) is available in AIR 3.6 and later.

- **resizable** — Whether the system chrome for resizing the window is shown.

- **systemChrome** — Whether the standard operating system window dressing is
  used. The systemChrome setting of a window cannot be changed at run time.

- **title** — The title of the window.

- **transparent** — Whether the window is alpha-blended against the background.
  The window cannot use system chrome if transparency is turned on. The
  transparent setting of a window cannot be changed at run time.

- **visible** — Whether the window is visible as soon as it is created. By
  default, the window is not visible initially so that your application can draw
  its contents before making itself visible.

- **width** — The width of the window.

- **x** — The horizontal position of the window.

- **y** — The vertical position of the window.

## Desktop features

The following elements control desktop installation and update features.

- customUpdateUI — Allows you to provide your own dialogs for updating an
  application. If set to `false`, the default, then the standard AIR dialogs are
  used.

- fileTypes — Specifies the types of files that your application would like to
  register for as the default opening application. If another application is
  already the default opener for a file type, then AIR does not override the
  existing registration. However, your application can override the registration
  at runtime using the `setAsDefaultApplication()` method of the
  NativeApplication object. It is good form to ask for the user's permission
  before overriding their existing file type associations.

  > **Note:** File type registration is ignored when you package an application
  > as a captive runtime bundle (using the `-bundle` target). To register a
  > given file type, you must create an installer program that performs the
  > registration.

- installFolder — Specifies a path relative to the standard application
  installation folder into which the application is installed. You can use this
  setting to provide a custom folder name as well as to group multiple
  applications within a common folder.

- programMenuFolder — Specifies the menu hierarchy for the Windows All Programs
  menu. You can use this setting to group multiple applications within a common
  menu. If no menu folder is specified, the application shortcut is added
  directly to the main menu.

## Supported profiles

If your application only makes sense on the desktop, then you can prevent it
from being installed on devices in another profile by excluding that profile
from the supported profiles list. If your application uses the NativeProcess
class or native extensions, then you must support the `extendedDesktop` profile.

If you leave the `supportedProfile` element out of the application descriptor,
then it is assumed that your application supports all the defined profiles. To
restrict your application to a specific list of profiles, list the profiles,
separated by whitespace:

    <supportedProfiles>desktop extendedDesktop</supportedProfiles>

For a list of ActionScript classes supported in the `desktop` and
`extendedDesktop` profile, see
[Capabilities of different profiles](WS144092a96ffef7cc16ddeea2126bb46b82f-7ffe.html).

## Required native extensions

Applications that support the `extendedDesktop` profile can use native
extensions.

Declare all native extensions that the AIR application uses in the application
descriptor. The following example illustrates the syntax for specifying two
required native extensions:

    <extensions>
         <extensionID>com.example.extendedFeature</extensionID>
        <extensionID>com.example.anotherFeature</extensionID>
    </extensions>

The `extensionID` element has the same value as the `id` element in the
extension descriptor file. The extension descriptor file is an XML file called
extension.xml. It is packaged in the ANE file you receive from the native
extension developer.

## Application icons

On the desktop, the icons specified in the application descriptor are used as
the application file, shortcut, and program menu icons. The application icon
should be supplied as a set of 16x16-, 32x32-, 48x48-, and 128x128-pixel PNG
images. Specify the path to the icon files in the icon element of the
application descriptor file:

    <icon>
        <image16x16>assets/icon16.png</image16x16>
        <image32x32>assets/icon32.png</image32x32>
        <image48x48>assets/icon48.png</image48x48>
        <image128x128>assets/icon128.png</image128x128>
    </icon>

If you do not supply an icon of a given size, the next largest size is used and
scaled to fit. If you do not supply any icons, a default system icon is used.

## Ignored settings

Applications on the desktop ignore application settings that apply to mobile
profile features. The ignored settings are:

- android

- aspectRatio

- autoOrients

- fullScreen

- iPhone

- renderMode (prior to AIR 3)

- requestedDisplayResolution

- softKeyboardBehavior

More Help topics

[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

[id](WSfffb011ac560372f2fea1812938a6e463-7ffe.html)

[filename](WSfffb011ac560372f2fea1812938a6e463-7ff9.html)

[name](WSfffb011ac560372f2fea1812938a6e463-7ffd.html)

[version](WSfffb011ac560372f2fea1812938a6e463-7ffc.html)

[versionLabel](WSfffb011ac560372f2fea1812938a6e463-7ffa.html)

[versionNumber](WSfffb011ac560372f2fea1812938a6e463-7ffb.html)

[content](WSfffb011ac560372f2fea1812938a6e463-7ff4.html)

[depthAndStencil](WS99d2e2affb7f39bd-2d75e77d134e7ea3560-8000.html)

[height](WSfffb011ac560372f2fea1812938a6e463-7fe9.html)

[maximizable](WSfffb011ac560372f2fea1812938a6e463-7fee.html)

[maxSize](WSfffb011ac560372f2fea1812938a6e463-7fe7.html)

[minimizable](WSfffb011ac560372f2fea1812938a6e463-7fef.html)

[minSize](WSfffb011ac560372f2fea1812938a6e463-7fe8.html)

[renderMode](WSfffb011ac560372f2fea1812938a6e463-7fe3.html)

[requestedDisplayResolution](WSfffb011ac560372f-4cb7055d12d779150e8-8000.html)

[resizable](WSfffb011ac560372f2fea1812938a6e463-7fed.html)

[systemChrome](WSfffb011ac560372f2fea1812938a6e463-7ff2.html)

[title](WSfffb011ac560372f2fea1812938a6e463-7ff3.html)

[transparent](WSfffb011ac560372f2fea1812938a6e463-7ff1.html)

[visible](WSfffb011ac560372f2fea1812938a6e463-7ff0.html)

[width](WSfffb011ac560372f2fea1812938a6e463-7fea.html)

[x](WSfffb011ac560372f2fea1812938a6e463-7fec.html)

[y](WSfffb011ac560372f2fea1812938a6e463-7feb.html)

[customUpdateUI](WSfffb011ac560372f2fea1812938a6e463-7fdf.html)

[fileTypes](WSfffb011ac560372f2fea1812938a6e463-7fdd.html)

[installFolder](WSfffb011ac560372f2fea1812938a6e463-7fe1.html)

[programMenuFolder](WSfffb011ac560372f2fea1812938a6e463-7fe0.html)

[supportedProfiles](WSfffb011ac560372f2fea1812938a6e463-7fe2.html)

[icon](WSfffb011ac560372f2fea1812938a6e463-7ff6.html)

[imageNxN](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html)
