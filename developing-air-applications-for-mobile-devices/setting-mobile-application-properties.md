# Setting mobile application properties

As with other AIR applications, you set the basic application properties in the
application descriptor file. Mobile applications ignore some of the
desktop-specific properties, such as window size and transparency. Mobile
applications can also use their own platform-specific properties. For example,
you can include an `android` element for Android apps and an `iPhone` element
for iOS apps.

## Common settings

Several application descriptor settings are important for all mobile device
applications.

### Required AIR runtime version

Specify the version of the AIR runtime required by your application using the
namespace of the application descriptor file.

The namespace, assigned in the `application` element, determines, in large part,
which features your application can use. For example, if your application uses
the AIR 2.7 namespace, and the user has some future version installed, then your
application will still see the AIR 2.7 behavior (even if the behavior has been
changed in the future version). Only when you change the namespace and publish
an update will your application have access to the new behavior and features.
Security fixes are an important exception to this rule.

On devices that use a runtime separate from the application, such as Android on
AIR 3.6 and earlier, the user will be prompted to install or upgrade AIR if they
do not have the required version. On devices that incorporate the runtime, such
as iPhone, this situation does not occur (since the required version is packaged
with the app in the first place).

Note: (AIR 3.7 and higher) By default, ADT packages the runtime with Android
applications.

Specify the namespace using the xmlns attribute of the root `application`
element. The following namespaces should be used for mobile applications
(depending on which mobile platform you are targeting):

    iOS 4+ and iPhone 3Gs+ or Android:
                                <application xmlns="http://ns.adobe.com/air/application/2.7">
                                iOS only:
                                <application xmlns="http://ns.adobe.com/air/application/2.0">

Note: Support for iOS 3 devices is provided by the Packager for iPhone SDK,
based on the AIR 2.0 SDK. For information about building AIR applications for
iOS 3, see
[Building iPhone apps](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/iphone/index.html).
The AIR 2.6 SDK (and later) support iOS 4, and above on iPhone 3Gs, iPhone 4,
and iPad devices.

### Application identity

Several settings should be unique for each application that you publish. These
include the ID, the name, and the filename.

#### Android application IDs

On Android, the ID is converted to the Android package name by prefixing "air."
to the AIR ID. Thus, if your AIR ID is _com.example.MyApp_, then the Android
package name is _air.com.example.MyApp_.

    <id>com.example.MyApp</id>
                                    <name>My Application</name>
                                    <filename>MyApplication</filename>

In addition, if the ID is not a legal package name on the Android operating
system, it is converted to a legal name. Hyphen characters are changed to
underscores and leading digits in any ID component are preceded by a capital
"A". For example, the ID: _3-goats.1-boat_, is transformed to the package name:
_air.A3_goats.A1_boat_.

Note: The prefix added to the application ID can be used to identify AIR
applications in the Android Market. If you do not want your application to
identified as an AIR application because of the prefix, you must unpackage the
APK file, change the application ID, and repackage it as described in,
[Opt-out of AIR application analytics for Android](http://kb2.adobe.com/cps/875/cpsid_87562.html).

#### iOS application IDs

Set the AIR application ID to match the app ID you created in the Apple iOS
Provisioning Portal.

iOS App IDs contain a bundle seed ID followed by a bundle identifier. The bundle
seed ID is a string of characters, such as 5RM86Z4DJM, that Apple assigns to the
App ID. The bundle identifier contains a reverse-domain-style name that you
pick. The bundle identifier can end in an asterisk (\*), indicating a wildcard
app ID. If the bundle identifier ends in the wildcard character, you can replace
that wildcard with any legal string.

For example:

- If your Apple app ID is, `5RM86Z4DJM.com.example.helloWorld`, you must use
  `com.example.helloWorld` in the application descriptor.

- If your Apple app ID is `96LPVWEASL.com.example.*` (a wildcard app ID), then
  you could use `com.example.helloWorld`, or `com.example.anotherApp`, or some
  other ID that starts with `com.example`.

- Finally, if your Apple app ID is just the bundle seed ID and a wildcard, such
  as: `38JE93KJL.*`, then you can use any application ID in AIR.

When specifying the app ID, do not include the bundle seed ID portion of the app
ID.

### Application version

In AIR 2.5 and later, specify the application version in the `versionNumber`
element. The `version` element can no longer be used. When specifying a value
for `versionNumber`, you must use a sequence of up to three numbers separated by
dots, such as: "0.1.2". Each segment of the version number can have up to three
digits. (In other words, "999.999.999" is the largest version number permitted.)
You do not have to include all three segments in the number; "1" and "1.0" are
legal version numbers as well.

You can also specify a label for the version using the `versionLabel` element.
When you add a version label it is displayed instead of the version number in
such places as the Android Application info screen. A version label must be
specified for apps that are distributed using the Android Market. If you do not
specify a `versionLabel` value in the AIR application descriptor, then the
`versionNumber` value is assigned to the Android version label field.

    <!-- AIR 2.5 and later -->
                                <versionNumber>1.23.7<versionNumber>
                                <versionLabel>1.23 Beta 7</versionLabel>

On Android, the AIR `versionNumber` is translated to the Android integer
`versionCode` using the formula:` a*1000000 + b*1000 + c`, where a, b, and c are
the components of the AIR version number: `a.b.c`.

### Main application SWF

Specify the main application SWF file in the `content` child of the
`initialWindow` element. When you target devices in the mobile profile, you must
use a SWF file (HTML-based applications are not supported).

    <initialWindow>
                                <content>MyApplication.swf</content>
                                </initialWindow>

You must include the file in the AIR package (using ADT or your IDE). Simply
referencing the name in the application descriptor does not cause the file to be
included in the package automatically.

### Main screen properties

Several child elements of the initialWindow element control the initial
appearance and behavior of the main application screen.

- **aspectRatio** — Specifies whether the application should initially display
  in a _portrait_ format (height greater than width), a _landscape_ format
  (height less than width), or _any_ format (the stage automatically orients to
  all orientations).

      <aspectRatio>landscape</aspectRatio>

- **autoOrients** — Specifies whether the stage should automatically change
  orientation as the user rotates the device or performs another
  orientation-related gesture such as opening or closing a sliding keyboard. If
  _false_, which is the default, then the stage will not change orientation with
  the device.

      <autoOrients>true</autoOrients>

- **depthAndStencil** — Specifies to use the depth or stencil buffer. You
  typically use these buffers when working with 3D content.

      <depthAndStencil>true</depthAndStencil>

- **fullScreen** — Specifies whether the application should take up the full
  device display, or should share the display with the normal operating system
  chrome, such as a system status bar.

      <fullScreen>true</fullScreen>

- **renderMode** — Specifies whether the runtime should render the application
  with the graphics processing unit (GPU) or the main, central processing unit
  (CPU). In general, GPU rendering will increase rendering speed, but some
  features, such as certain blend modes and PixelBender filters, are unavailable
  in GPU mode. In addition, different devices, and different device drivers,
  have varying GPU capabilities and limitations. You should always test your
  application on the widest variety of devices possible, especially when using
  GPU mode.

  You can set the render mode to _gpu_, _cpu_, _direct_, or _auto_. The default
  value is _auto_, which currently falls back to cpu mode.

  Note: In order to leverage GPU acceleration of Flash content with AIR for
  mobile platforms, Adobe recommends that you use renderMode="direct" (that is,
  Stage3D) rather than renderMode="gpu". Adobe officially supports and
  recommends the following Stage3D based frameworks: Starling (2D) and Away3D
  (3D). For more details on Stage3D and Starling/Away3D, see
  <http://gaming.adobe.com/getstarted/>.

      <renderMode>direct</renderMode>

  Note: You cannot use renderMode="direct" for applications that run in the
  background.

  The limitations of GPU mode are:

  - The Flex framework does not support the GPU rendering mode.

  - Filters are not supported

  - PixelBender blends, and fills are not supported

  - The following blend modes are not supported: layer, alpha, erase, overlay,
    hardlight, lighten, and darken

  - Using GPU rendering mode in an app that plays video is not recommended.

  - In GPU rendering mode, text fields are not properly moved to a visible
    location when the virtual keyboard opens. To ensure that your text field is
    visible while the user enters text use the softKeyboardRect property of the
    stage and soft keyboard events to move the text field to the visible area.

  - If a display object cannot be rendered by the GPU, it is not displayed at
    all. For example, if a filter is applied to a display object, the object is
    not shown.

  Note: The GPU implementation for iOS in AIR 2.6+ is much different than the
  implementation used in the earlier, AIR 2.0 version. Different optimization
  considerations apply.

### Supported profiles

You can add the `supportedProfiles` element to specify which device profiles
your application supports. Use the mobileDevice profile for mobile devices. When
you run your application with the Adobe Debug Launcher (ADL), ADL uses the first
profile in the list as the active profile. You can also use the `-profile` flag
when running ADL to select a particular profile in the supported list. If your
application runs under all profiles, you can leave the `supportedProfiles`
element out altogether. ADL uses the desktop profile as the default active
profile in this case.

To specify that your application supports both the mobile device and desktop
profiles, and you normally want to test the app in the mobile profile, add the
following element:

    <supportedProfiles>mobileDevice desktop</supportedProfiles>

### Required native extensions

Applications that support the `mobileDevice` profile can use native extensions.

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

### Virtual keyboard behavior

Set the `softKeyboardBehavior` element to `none` in order to disable the
automatic panning and resizing behavior that the runtime uses to make sure that
the focused text entry field is in view after the virtual keyboard is raised. If
you disable the automatic behavior, then it is your application's responsibility
to make sure that the text entry area, or other relevant content is visible
after the keyboard is raised. You can use the `softKeyboardRect` property of the
stage in conjunction with the SoftKeyboardEvent to detect when the keyboard
opens and determine the area it obscures.

To enable the automatic behavior, set the element value to `pan`:

    <softKeyboardBehavior>pan</softKeyboardBehavior>

Since `pan` is the default value, omitting the `softKeyboardBehavior` element
also enables the automatic keyboard behavior.

Note: When you also use GPU rendering, the pan behavior is not supported.

## Android settings

On the Android platform, you can use the `android` element of the application
descriptor to add information to the Android application manifest, which is an
application properties file used by the Android operating system. ADT
automatically generates the Android Manifest.xml file when you create the APK
package. AIR sets a few properties to the values required for certain features
to work. Any other properties set in the android section of the AIR application
descriptor are added to the corresponding section of the Manifest.xml file.

Note: For most AIR applications, you must set the Android permissions needed by
your application within the `android` element, but you generally will not need
to set any other properties.

You can only set attributes that take string, integer, or boolean values.
Setting references to resources in the application package is not supported.

Note: The runtime requires a minimum SDK version equal to or greater than 14. If
you wish to create an application only for higher versions, you should ensure
that the Manifest includes `<uses-sdk android:minSdkVersion=""></uses-sdk>` with
correct version, accordingly.

### Reserved Android manifest settings

AIR sets several manifest entries in the generated Android manifest document to
ensure that application and runtime features work correctly. You cannot define
the following settings:

#### manifest element

You cannot set the following attributes of the manifest element:

- package

- android:versionCode

- android:versionName

- xmlns:android

#### activity element

You cannot set the following attributes for the main activity element:

- android:label

- android:icon

#### application element

You cannot set the following attributes of the application element:

- android:theme

- android:name

- android:label

- android:windowSoftInputMode

- android:configChanges

- android:screenOrientation

- android:launchMode

### Android permissions

The Android security model requires that each app request permission in order to
use features that have security or privacy implications. These permissions must
be specified when the app is packaged, and cannot be changed at runtime. The
Android operating system informs the user which permissions an app is requesting
when the user installs it. If a permission required for a feature is not
requested, the Android operating system might throw an exception when your
application access the feature, but an exception is not guaranteed. Exceptions
are transmitted by the runtime to your application. In the case of a silent
failure, a permission failure message is added to the Android system log.

In AIR, you specify the Android permissions inside the `android` element of the
application descriptor. The following format is used for adding permissions
(where PERMISSION_NAME is the name of an Android permission):

    <android>
                                <manifestAdditions>
                                <![CDATA[
                                <manifest>
                                <uses-permission android:name="android.permission.PERMISSION_NAME" />
                                </manifest>
                                ]]>
                                </manifestAdditions>
                                </android>

The uses-permissions statements inside the `manifest` element are added directly
to the Android manifest document.

The following permissions are required to use various AIR features:

ACCESS_COARSE_LOCATION  
Allows the application to access WIFI and cellular network location data through
the Geolocation class.

ACCESS_FINE_LOCATION  
Allows the application to access GPS data through the Geolocation class.

ACCESS_NETWORK_STATE and ACCESS_WIFI_STATE  
Allows the application to access network information the NetworkInfo class.

CAMERA  
Allows the application to access the camera.

Note: When you ask for permission to use the camera feature, Android assumes
that your application also requires the camera. If the camera is an optional
feature of your application, then you should add a `uses-feature` element to the
manifest for the camera, setting the required attribute to `false`. See
[Android compatibility filtering](WS2d929364fa0b81373f2c6cba12a3522f10c-7fff.html).

INTERNET  
Allows the application to make network requests. Also allows remote debugging.

READ_PHONE_STATE  
Allows the AIR runtime to mute audio during phone calls. You should set this
permission if your app plays audio while in the background.

RECORD_AUDIO  
Allows the application to access the microphone.

WAKE_LOCK and DISABLE_KEYGUARD  
Allows the application to prevent the device from going to sleep using the
SystemIdleMode class settings.

WRITE_EXTERNAL_STORAGE  
Allows the application to write to the external memory card on the device.

For example, to set the permissions for an app that impressively requires every
permission, you could add the following to the application descriptor:

    <android>
                                <manifestAdditions>
                                <![CDATA[
                                <manifest>
                                <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
                                <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
                                <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
                                <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
                                <uses-permission android:name="android.permission.CAMERA" />
                                <uses-permission android:name="android.permission.DISABLE_KEYGUARD" />
                                <uses-permission android:name="android.permission.INTERNET" />
                                <uses-permission android:name="android.permission.READ_PHONE_STATE" />
                                <uses-permission android:name="android.permission.RECORD_AUDIO" />
                                <uses-permission android:name="android.permission.WAKE_LOCK" />
                                <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
                                </manifest>
                                ]]>
                                </manifestAdditions>
                                </android>

### Android custom URI schemes

You can use a custom URI scheme to launch an AIR application from a web page or
a native Android application. Custom URI support relies on intent filters
specified in the Android manifest, so this technique cannot be used on other
platforms.

To use a custom URI, add an intent-filter to the application descriptor within
the `<android>` block. Both `intent-filter` elements in the following example
must be specified. Edit the `<data android:scheme="`_`my-customuri`_`"/>`
statement to reflect the URI string for your custom scheme.

    <android>
                                <manifestAdditions>
                                <![CDATA[
                                <manifest>
                                <application>
                                <activity>
                                <intent-filter>
                                <action android:name="android.intent.action.MAIN"/>
                                <category android:name="android.intent.category.LAUNCHER"/>
                                </intent-filter>
                                <intent-filter>
                                <action android:name="android.intent.action.VIEW"/>
                                <category android:name="android.intent.category.BROWSABLE"/>
                                <category android:name="android.intent.category.DEFAULT"/>
                                <data android:scheme="my-customuri"/>
                                </intent-filter>
                                </activity>
                                </application>
                                </manifest>
                                ]]>
                                </manifestAdditions>
                                </android>

An intent filter informs the Android operating system that your application is
available to perform a given action. In the case of a custom URI, this means
that the user has clicked a link using that URI scheme (and the browser does not
know how to handle it).

When your application is invoked through a custom URI, the NativeApplication
object dispatches an `invoke` event. The URL of the link, including query
parameters, is placed in the `arguments` array of the InvokeEvent object. You
can use any number of intent-filters.

Note: Links in a StageWebView instance cannot open URLs that use a custom URI
scheme.

### Android compatibility filtering

The Android operating system uses a number of elements in the application
manifest file to determine whether your application is compatible with a given
device. Adding this information to the manifest is optional. If you do not
include these elements, your application can be installed on any Android device.
However, it may not operate properly on any Android device. For example, a
camera app will not be very useful on a phone that does not have a camera.

The Android manifest tags that you can use for filtering include:

- supports-screens

- uses-configuration

- uses-feature

- uses-sdk (in AIR 3+)

#### Camera applications

If you request the camera permission for your application, Android assumes that
the app requires all available camera features, including auto-focus and flash.
If your app does not require all camera features, or if the camera is an
optional feature, you should set the various `uses-feature` elements for the
camera to indicate that these are optional. Otherwise, users with devices that
are missing one feature or that do not have a camera at all, will not be able to
find your app on the Android Market.

The following example illustrates how to request permission for the camera and
make all camera features optional:

    <android>
                                    <manifestAdditions>
                                    <![CDATA[
                                    <manifest>
                                    <uses-permission android:name="android.permission.CAMERA" />
                                    <uses-feature android:name="android.hardware.camera" android:required="false"/>
                                    <uses-feature android:name="android.hardware.camera.autofocus" android:required="false"/>
                                    <uses-feature android:name="android.hardware.camera.flash" android:required="false"/>
                                    </manifest>
                                    ]]>
                                    </manifestAdditions>
                                    </android>

#### Audio recording applications

If you request the permission to record audio, Android also assumes that the app
requires a microphone. If audio recording is an optional feature of your app,
you can add a uses-feature tag to specify that the microphone is not required.
Otherwise, users with devices that do not have a microphone, will not be able to
find your app on the Android Market.

The following example illustrates how to request permission to use the
microphone while still making the microphone hardware optional:

    <android>
                                    <manifestAdditions>
                                    <![CDATA[
                                    <manifest>
                                    <uses-permission android:name="android.permission.RECORD_AUDIO" />
                                    <uses-feature android:name="android.hardware.microphone" android:required="false"/>
                                    </manifest>
                                    ]]>
                                    </manifestAdditions>
                                    </android>

### Install location

You can permit your application to be installed or moved to the external memory
card by setting the `installLocation` attribute of the Android `manifest`
element to either `auto` or `preferExternal`:

    <android>
                                <manifestAdditions>
                                <![CDATA[
                                <manifest android:installLocation="preferExternal"/>
                                ]]>
                                </manifestAdditions>
                                </android>

The Android operating system doesn't guarantee that your app will be installed
to the external memory. A user can also move the app between internal and
external memory using the system settings app.

Even when installed to external memory, application cache and user data, such as
the contents of the app-storage directory, shared objects, and temporary files,
are still stored in the internal memory. To avoid using too much internal
memory, be selective about the data you save to the application storage
directory. Large amounts of data should be saved to the SDCard using the
`File.userDirectory` or `File.documentsDirectory` locations (which both map to
the root of the SD card on Android).

### Enabling Flash Player and other plug-ins in a StageWebView object

In Android 3.0+, an application must enable hardware acceleration in the Android
application element in order for plug-in content to be displayed in a
StageWebView object. To enable plug-in rendering, set the
`android:hardwareAccelerated` attribute of the `application` element to `true`:

    <android>
                                <manifestAdditions>
                                <![CDATA[
                                <manifest>
                                <application android:hardwareAccelerated="true"/>
                                </manifest>
                                ]]>
                                </manifestAdditions>
                                </android>

### Color depth

In AIR 3 and later, the runtime sets the display to render 32-bit colors. In
earlier versions of AIR, the runtime uses 16-bit color. You can instruct the
runtime to use 16-bit color using the \<colorDepth\> element of the application
descriptor:

    <android>
                                <colorDepth>16bit</colorDepth>
                                <manifestAdditions>...</manifestAdditions>
                                </android>

Using the 16-bit color depth can increase rendering performance, but at the
expense of color fidelity.

## iOS Settings

Settings that apply only to iOS devices are placed within the `<iPhone>` element
in the application descriptor. The `iPhone` element can have an `InfoAdditions`
element, a `requestedDisplayResolution` element, an `Entitlements` element, an
`externalSwfs` element, and a `forceCPURenderModeForDevices` element as
children.

The `InfoAdditions` element lets you specify key-value pairs that are added to
the Info.plist settings file for the application. For example, the following
values set the status bar style of the application and state that the
application does not require persistent Wi-Fi access.

    <InfoAdditions>
                                <![CDATA[
                                <key>UIStatusBarStyle</key>
                                <string>UIStatusBarStyleBlackOpaque</string>
                                <key>UIRequiresPersistentWiFi</key>
                                <string>NO</string>
                                ]]>
                                </InfoAdditions>

The InfoAdditions settings are enclosed in a `CDATA` tag.

Th `Entitlements` element lets you specify key-value pairs added to the
Entitlements.plist settings file for the application. Entitlements.plist
settings provide application access to certain iOS features, such as push
notifications.

For more detailed information on Info.plist and Entitlements.plist settings, see
the Apple developer documentation.

### Supporting background tasks on iOS

Adobe AIR 3.3 and higher supports multitasking on iOS by enabling certain
background behaviors:

- Audio

- Location updates

- Networking

- Opting out of background app execution

Note: With swf-version 21 and its earlier versions, AIR does not support
background execution on iOS and Android when render mode direct is set. Due to
this restriction, Stage3D based apps cannot execute background tasks like audio
playback, location updates, network upload or download, etc. iOS does not allow
OpenGLES or rendering of calls in the background. Applications which attempt to
make OpenGL calls in the background are terminated by iOS. Android does not
restrict applications from either making OpenGLES calls in the background or
performing other background tasks like audio playback. With swf-version 22 and
later, AIR mobile applications can execute in the background when renderMode
direct is set. The AIR iOS runtime results in an ActionScript error (3768 - The
Stage3D API may not be used during background execution) if OpenGLES calls are
made in the background. However, there are no errors on Android because its
native applications are allowed to make OpenGLES calls in the background. For
optimal utilization of mobile resource, do not make rendering calls while an
application is executing in the background.

#### Background audio

To enable background audio playback and recording, include the following
key-value pair in the `InfoAdditions` element:

    <InfoAdditions>
                                    <![CDATA[
                                    <key>UIBackgroundModes</key>
                                    <array>
                                    <string>audio</string>
                                    </array>
                                    ]]>
                                    </InfoAdditions>

#### Background location updates

To enable background location updates, include the following key-value pair in
the `InfoAdditions` element:

    <InfoAdditions>
                                    <![CDATA[
                                    <key>UIBackgroundModes</key>
                                    <array>
                                    <string>location</string>
                                    </array>
                                    ]]>
                                    </InfoAdditions>

Note: Use this feature only when necessary, as location APIs are a significant
drain on the battery.

#### Background networking

To execute short tasks in the background, your application sets the
`NativeApplication.nativeApplication.executeInBackground` property to `true`.

For example, your application may start a file upload operation after which the
user moves another application to the front. When the application receives an
upload completion event, it can set
`NativeApplication.nativeApplication.executeInBackground` to `false`.

Setting the `NativeApplication.nativeApplication.executeInBackground` property
to `true` does not guarantee the application will run indefinitely, as iOS
imposes a time limit on background tasks. When iOS stops background processing,
AIR dispatches the `NativeApplication.suspend` event.

#### Opting out of background execution

Your application can explicitly opt out of background execution by including the
following key-value pair in the `InfoAdditions` element:

    <InfoAdditions>
                                    <![CDATA[
                                    <key>UIApplicationExitsOnSuspend</key>
                                    <true/>
                                    ]]>
                                    </InfoAdditions>

### Reserved iOS InfoAdditions settings

AIR sets several entries in the generated Info.plist file to ensure that
application and runtime features work correctly. You cannot define the following
settings:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>CFBundleDisplayName</p>
<p>CFBundleExecutable</p>
<p>CFBundleIconFiles</p>
<p>CFBundleIdentifier</p>
<p>CFBundleInfoDictionaryVersion</p>
<p>CFBundlePackageType</p>
<p>CFBundleResourceSpecification</p>
<p>CFBundleShortVersionString</p>
<p>CFBundleSupportedPlatforms</p>
<p>CFBundleVersion</p>
<p>CTAutoOrients</p></td>
<td><p>CTInitialWindowTitle</p>
<p>CTInitialWindowVisible</p>
<p>CTIosSdkVersion</p>
<p>CTMaxSWFMajorVersion</p>
<p>DTPlatformName</p>
<p>DTSDKName</p>
<p>MinimumOSVersion (reserved till 3.2)</p>
<p>NSMainNibFile</p>
<p>UIInterfaceOrientation</p>
<p>UIStatusBarHidden</p>
<p>UISupportedInterfaceOrientations</p></td>
</tr>
</tbody>
</table>

Note: You can define the MinimumOSVersion. The MinimumOSVersion definition is
honoured in Air 3.3 and later.

### Supporting different iOS device models

For iPad support, include the proper key-value settings for `UIDeviceFamily`
within your `InfoAdditions` element. The `UIDeviceFamily` setting is an array of
strings. Each string defines supported devices. The `<string>1</string>` setting
defines support for the iPhone and iPod Touch. The `<string>2</string>` setting
defines support for the iPad.The `<string>3</string>` setting defines support
for the tvOS. If you specify only one of these strings, only that device family
is supported. For example, the following setting limits support to the iPad:

    <key>UIDeviceFamily</key>
                                <array>
                                <string>2</string>
                                </array>>

The following setting supports both device families (iPhone/iPod Touch and
iPad):

    <key>UIDeviceFamily</key>
                                <array>
                                <string>1</string>
                                <string>2</string>
                                </array>

The following setting limits support for tvOS:

    <key>UIDeviceFamily</key>
                                <array>
                                <string>3</string>
                                </array>

Note: If UIDeviceFamily is not provided and tvOS provisioning is given, then the
UIDeviceFamily value equal to 3 is added automatically in the final IPA that is
generated.

Note: Following warnings appear if there is a mismatch between the provisioning
profile and the UIDeviceFamily value:

- Warning: Provisioning profile specified for tvOS, ignoring iOS UIDeviceFamily
  value(s).

- Warning: Provisioning profile specified for iOS, ignoring tvOS UIDeviceFamily
  value(s).

Additionally, in AIR 3.7 and higher, you can use the
`forceCPURenderModeForDevices` tag to force CPU render mode for a specified set
of devices and enable GPU render mode for remaining iOS devices.

You add this tag as a child of the `iPhone` tag and specify a space-separated
list of device model names. For a list of valid device model names, see
[forceCPURenderModeForDevices](WS180fc5cb46642d10-3a65697f13da2342af2-8000.html).

For example, to use CPU mode in old iPods, iPhones, and iPads and enable GPU
mode for all other devices, specify the following in the application descriptor:

    ...
                                <renderMode>GPU</renderMode>
                                ...
                                <iPhone>
                                ...
                                   <forceCPURenderModeForDevices>iPad1,1 iPhone1,1 iPhone1,2 iPod1,1
                                   </forceCPURenderModeForDevices>
                                </iPhone>

### High-resolution displays

`The requestedDisplayResolution` element specifies whether your application
should use the _standard_ or _high_ resolution mode on iOS devices with
high-resolution screens.

    <requestedDisplayResolution>high</requestedDisplayResolution>

In high-resolution mode, you can address each pixel on a high-resolution display
individually. In the standard mode, the device screen will appear to your
application as a standard resolution screen. Drawing a single pixel in this mode
will set the color of four pixels on the high-resolution screen.

The default setting is `standard`. Note that for targeting iOS devices, you use
the `requestedDisplayResolution` element as a child of the `iPhone` element (not
the `InfoAdditions` element or `initialWindow` element).

If you want to use different settings on different devices, specify your default
value as the `requestedDisplayResolution` element's value. Use the
`excludeDevices` attribute to specify devices that should use the opposite
value. For example, with the following code, high resolution mode is used for
all devices that support it except 3rd-generation iPads, which use standard
mode:

    <requestedDisplayResolution excludeDevices="iPad3">high</requestedDisplayResolution>

The `excludeDevices` attribute is available in AIR 3.6 and later.

### iOS custom URI schemes

You can register a custom URI scheme to allow your application to be invoked by
a link in a web page or another, native application on the device. To register a
URI scheme, add a CFBundleURLTypes key to the InfoAdditions element. The
following example registers a URI scheme named _com.example.app_ to allow an
application to be invoked by URLs with the form: _example://foo_.

    <key>CFBundleURLTypes</key>
                                <array>
                                <dict>
                                <key>CFBundleURLSchemes</key>
                                <array>
                                <string>example</string>
                                </array>
                                <key>CFBundleURLName</key>
                                <string>com.example.app</string>
                                </dict>
                                </array>

When your application is invoked through a custom URI, the NativeApplication
object dispatches an `invoke` event. The URL of the link, including query
parameters, is placed in the `arguments` array of the InvokeEvent object. You
can use any number of custom URI schemes.

Note: Links in a StageWebView instance cannot open URLs that use a custom URI
scheme.

Note: If another application has already registered a scheme, then your
application cannot replace it as the application registered for that URI scheme.

### iOS compatibility filtering

Add entries to a UIRequiredDeviceCapabilities array within the `InfoAdditions`
element if your application should only be used on devices with specific
hardware or software capabilities. For example, the following entry indicates
that an application requires a still camera and a microphone:

    <key>UIRequiredDeviceCapabilities</key>
                                <array>
                                <string>microphone</string>
                                <string>still-camera</string>
                                </array>

If a device lacks the corresponding capability, the application cannot be
installed. The capability settings relevant to AIR applications include:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>telephony</p>
<p>wifi</p>
<p>sms</p>
<p>still-camera</p>
<p>auto-focus-camera</p>
<p>front-facing-camera</p></td>
<td><p>camera-flash</p>
<p>video-camera</p>
<p>accelerometer</p>
<p>location-services</p>
<p>gps</p>
<p>microphone</p></td>
</tr>
</tbody>
</table>

AIR 2.6+ automatically adds _armv7_ and _opengles-2_ to the list of required
capabilities.

Note: You do not need to include these capabilities in the application
descriptor in order for your application to use them. Use the
UIRequiredDeviceCapabilities settings only to prevent users from installing your
application on devices on which it cannot function properly.

### Exiting instead of pausing

When a user switches away from an AIR application it enters the background and
pauses. If you want your application to exit completely instead of pausing, set
the `UIApplicationExitsOnSuspend` property to `YES`:

    <key>UIApplicationExitsOnSuspend</key>
                                <true/>

### Minimize download size by loading external, asset-only SWFs

You can minimize your initial application download size by packaging a subset of
the SWFs used by your application and loading the remaining (asset-only)
external SWFs at runtime using the `Loader.load()` method. To use this feature,
you must package the application such that ADT moves all ActionScript ByteCode
(ABC) from the externally loaded SWF files to the main application SWF, leaving
a SWF file that contains only assets. This is to conform with the Apple Store's
rule that forbids downloading any code after an application is installed.

ADT does the following to support externally loaded SWFs (also called stripped
SWFs):

- Reads the text file specified in the `<iPhone>` element's `<externalSwfs>`
  subelement to access the line-delimited list of SWFs to be loaded at execution
  time:

      <iPhone>
                                             ...
                                             <externalSwfs>FilewithPathsOfSWFsThatAreToNotToBePackaged.txt</externalSwfs>
                                          </iPhone>

- Transfers the ABC code from each externally loaded SWF to the main executable.

- Omits the externally loaded SWFs from the .ipa file.

- Copies the stripped SWFs to the `.remoteStrippedSWFs` directory. You host
  these SWFs on a web server and your application loads them, as necessary, at
  runtime.

You indicate the SWF files to be loaded at runtime by specifying their names,
one per line in a text file, as the following example shows:

    assets/Level1/Level1.swf
                                assets/Level2/Level2.swf
                                assets/Level3/Level3.swf
                                assets/Level4/Level4.swf

The file path specified is relative to the application descriptor file.
Additionally, you must specify these swfs as assets in the `adt` command.

Note: This feature applies to standard packaging only. For fast packaging (using
for example, using interpreter, simulator, or debug) ADT does not create
stripped SWFs.

![](../img/byline.png) For more information on this feature, including sample
code, see
[External hosting of secondary SWFs for AIR apps on iOS](http://blogs.adobe.com/airodynamics/2013/03/08/external-hosting-of-secondary-swfs-for-air-apps-on-ios/),
a blog post by Adobe engineer Abhinav Dhandh.

### Geolocation Support

For Geolocation support, add one of the following key-value pairs to the
`InfoAdditions` element:

    <InfoAdditions>
                                <![CDATA[
                                <key>NSLocationAlwaysUsageDescription</key>
                                <string>Sample description to allow geolocation always</string>
                                <key>NSLocationWhenInUseUsageDescription</key>
                                <string>Sample description to allow geolocation when application is in foreground</string>
                                <key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
                                <string>Sample description to allow geolocation always and when application is in foreground</string>
                                ]]>
                                </InfoAdditions>

## Application icons

The following table lists the icon sizes used on each mobile platform:

| Icon size | Platform     |
| --------- | ------------ |
| 29x29     | iOS          |
| 36x36     | Android      |
| 40x40     | iOS          |
| 48x48     | Android, iOS |
| 50x50     | iOS          |
| 57x57     | iOS          |
| 58x58     | iOS          |
| 60x60     | iOS          |
| 72x72     | Android, iOS |
| 75x75     | iOS          |
| 76x76     | iOS          |
| 80x80     | iOS          |
| 87x87     | iOS          |
| 96x96     | Android      |
| 100x100   | iOS          |
| 114x114   | iOS          |
| 120x120   | iOS          |
| 144x144   | Android, iOS |
| 152x152   | iOS          |
| 167x167   | iOS          |
| 180x180   | iOS          |
| 192x192   | Android      |
| 512x512   | Android, iOS |
| 1024x1024 | iOS          |

Specify the path to the icon files in the icon element of the application
descriptor file:

    <icon>
                            <image36x36>assets/icon36.png</image36x36>
                            <image48x48>assets/icon48.png</image48x48>
                            <image72x72>assets/icon72.png</image72x72>
                            </icon>

If you do not supply an icon of a given size, the next largest size is used and
scaled to fit.

#### Icons on Android

On Android, the icons specified in the application descriptor are used as the
application Launcher icon. The application Launcher icon should be supplied as a
set of 36x36–pixel, 48x48–pixel, 72x72–pixel, 96x96–pixel, 144x144–pixel, and
192x192–pixel PNG images. These icon sizes are used for low-density,
medium-density, and high-density screens, respectively.

The developers are required to submit the 512x512–pixel icon at the time of
app-submission on Google Play Store.

#### Icons on iOS

The icons defined in the application descriptor are used in the following places
for an iOS application:

- A 29-by-29–pixel icon— Spotlight search icon for lower resolution
  iPhones/iPods and Settings icon for lower resolution iPads.

- A 40-by-40–pixel icon— Spotlight search icon for lower resolution iPads.

- A 48-by-48–pixel icon—AIR adds a border to this image and uses it as a 50x50
  icon for spotlight search on lower resolution iPads.

- A 50-by-50–pixel icon— Spotlight search for lower resolution iPads.

- A 57-by-57–pixel icon— Application icon for lower resolution iPhones/iPods.

- A 58-by-58–pixel icon— Spotlight icon for Retina Display iPhones/iPods and
  Settings icon for Retina Display iPads.

- A 60-by-60–pixel icon— Application icon for lower resolution iPhones/iPods.

- A 72-by-72–pixel icon (optional)—Application Icon for lower resolution iPads.

- A 76-by-76–pixel icon (optional)—Application Icon for lower resolution iPads.

- A 80-by-80–pixel icon— Spotlight search for high resolution
  iPhones/iPods/iPads.

- A 100-by-100–pixel icon— Spotlight search for Retina Display iPads.

- A 114-by-114–pixel icon— Application Icon for Retina display iPhone/iPods.

- A 120-by-120–pixel icon— Application icon for high resolution iPhones/iPods.

- A 152-by-152–pixel icon— Application icon for high resolution iPads.

- A 167-by-167–pixel icon— Application icon for high resolution iPad Pro.

- A 512-by-512–pixel icon— Application icon for lower resolution
  iPhones/iPods/iPads). iTunes displays this icon. The 512-pixel PNG file is
  used only for testing development versions of your application When you submit
  the final application to the Apple App Store, you submit the 512 image
  separately, as a JPG file. It is not included in the IPA.

- A 1024-by-1024-pixel icon— Application icon for Retina Display
  iPhones/iPods/iPads.

iOS adds a glare effect to the icon. You do not need to apply the effect to your
source image. To remove this default glare effect, add the following to the
`InfoAdditions` element in the application descriptor file:

    <InfoAdditions>
                                    <![CDATA[
                                    <key>UIPrerenderedIcon</key>
                                    <true/>
                                    ]]>
                                    </InfoAdditions>

Note: 1. Starting AIR 28, Assets.car needs to be packaged along with application
xml and swf file for the icons to be visible on devices having iOS 11 and
above. 2. On iOS, application metadata is inserted as png metadata into the
application icons so that Adobe can track the number of AIR applications
available in the Apple iOS app store. If you do not want your application to
identified as an AIR application because of this icon metadata, you must
unpackage the IPA file, remove the icon metadata, and repackage it. This
procedure is described in the article
[Opt-out of AIR application analytics for iOS](http://kb2.adobe.com/cps/893/cpsid_89362.html).

### iOS launch images

In addition to the application icons, you must also provide at least one launch
image named _Default.png_. Optionally, you can include separate launch images
for different starting orientations, different resolutions (including
high-resolution retina display and 16:9 aspect ratio), and different devices.
You can also include different launch images to be used when your application is
invoked through a URL.

Launch image files are not referenced in the application descriptor and must be
placed in the root application directory. (Do _not_ put the files in a
subdirectory.)

#### File naming scheme

Name the image according to the following scheme:

    basename + screen size modifier + urischeme + orientation + scale + device + .png

The _basename_ portion of the file name is the only required part. It is either
_Default_ (with a capital D) or the name you specify using the
`UILaunchImageFile` key in the `InfoAdditions` element in the application
descriptor.

The _screen size modifier_ portion designates the size of the screen when it is
not one of the standard screen sizes. This modifier only applies to iPhone and
iPod touch models with 16:9 aspect-ratio screens, such as the iPhone 5 and iPod
touch (5th generation). The only supported value for this modifier is `-568h`.
Since these devices support high-resolution (retina) displays, the screen size
modifier is always used with an image that has the `@2x` scale modifier as well.
The complete default launch image name for these devices is
`Default-568h@2x.png`.

The _urischeme_ portion is the string used to identify the URI scheme. This
portion only applies if your app supports one or more custom URL schemes. For
example, if your application can be invoked through a link such as
`example://foo`, use `-example` as the scheme portion of the launch image file
name.

The _orientation_ portion provides a way to specify multiple launch images to
use depending on the device orientation when the application is launched. This
portion only applies to images for iPad apps. It can be one of the following
values, referring to the orientation that the device is in when the application
starts up:

- -Portrait

- -PortraitUpsideDown

- -Landscape

- -LandscapeLeft

- -LandscapeRight

The _scale_ portion is `@2x` ( for iPhone 4, iPhone 5 and iPhone 6) or `@3x`
(for iPhone 6 plus) for the launch images used for high-resolution (retina)
displays. (Omit the scale portion entirely for the images used for standard
resolution displays.) For launch images for taller devices such as iPhone 5 and
iPod touch (5th generation), you must also specify the screen size modifier
`-528h` after the basename portion and before any other portion.

The _device_ portion is used to designate launch images for handheld devices and
phones. This portion is used when your app is a universal app that supports both
handheld devices and tablets with a single app binary. The possible value must
be either `~ipad` or `~iphone` (for both iPhone and iPod Touch).

For iPhone, you can only include portrait aspect-ratio images. However, in case
of iPhone 6 plus, landscape images can also be added. Use 320x480 pixel images
for standard resolution devices, 640x960 pixel images for high-resolution
devices, and 640x1136 pixel images for 16:9 aspect-ratio devices such as iPhone
5 and iPod touch (5th generation).

For iPad, you include images as follows:

- AIR 3.3 and earlier —Non-full-screen images: Include both landscape (1024x748
  for normal resolution, 2048x1496 for high resolution) and portrait (768x1004
  for normal resolution, 1536x2008 for high resolution) aspect-ratio images.

- AIR 3.4 and later — Full-screen images: Include both landscape (1024x768 for
  normal resolution, 2048x1536 for high resolution) and portrait (768x1024 for
  normal resolution, 1536x2048 for high resolution) aspect-ratio images. Note
  that when you package a full-screen image for a non-full-screen application,
  the top 20 pixels (top 40 pixels for high resolution ) are covered by the
  status bar. Avoid displaying important information in this area.

#### Examples

The following table shows an example set of launch images that you could include
for a hypothetical application that supports the widest possible range of
devices and orientations, and can be launched with URLs using the `example://`
scheme:

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>File name</p></th>
<th><p>Image size</p></th>
<th><p>Usage</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default.png</p></td>
<td><p>320 x 480</p></td>
<td><p>iPhone, standard resolution</p></td>
</tr>
<tr class="even">
<td><p>Default@2x.png</p></td>
<td><p>640 x 960</p></td>
<td><p>iPhone, high resolution</p></td>
</tr>
<tr class="odd">
<td><p>Default-568h@2x.png</p></td>
<td><p>640 x 1136</p></td>
<td><p>iPhone, high resolution, 16:9 aspect ratio</p></td>
</tr>
<tr class="even">
<td><p>Default-Portrait.png</p></td>
<td><p>768 x 1004 (AIR 3.3 and earlier)</p>
<p>768 x 1024 (AIR 3.4 and higher)</p></td>
<td><p>iPad, portrait orientation</p></td>
</tr>
<tr class="odd">
<td><p>Default-Portrait@2x.png</p></td>
<td><p>1536 x 2008 (AIR 3.3 and earlier)</p>
<p>1536 x 2048 (AIR 3.4 and higher)</p></td>
<td><p>iPad, high resolution, portrait orientation</p></td>
</tr>
<tr class="even">
<td><p>Default-PortraitUpsideDown.png</p></td>
<td><p>768 x 1004 (AIR 3.3 and earlier)768 x 1024 (AIR 3.4 and
higher)</p></td>
<td><p>iPad, upside down portrait orientation</p></td>
</tr>
<tr class="odd">
<td><p>Default-PortraitUpsideDown@2x.png</p></td>
<td><p>1536 x 2008 (AIR 3.3 and earlier)1536 x 2048 (AIR 3.4 and
higher)</p></td>
<td><p>iPad, high resolution, upside down portrait orientation</p></td>
</tr>
<tr class="even">
<td><p>Default-Landscape.png</p></td>
<td><p>1024 x 768</p></td>
<td><p>iPad, left landscape orientation</p></td>
</tr>
<tr class="odd">
<td><p>Default-LandscapeLeft@2x.png</p></td>
<td><p>2048 x 1536</p></td>
<td><p>iPad, high resolution, left landscape orientation</p></td>
</tr>
<tr class="even">
<td><p>Default-LandscapeRight.png</p></td>
<td><p>1024 x 768</p></td>
<td><p>iPad, right landscape orientation</p></td>
</tr>
<tr class="odd">
<td><p>Default-LandscapeRight@2x.png</p></td>
<td><p>2048 x 1536</p></td>
<td><p>iPad, high resolution, right landscape orientation</p></td>
</tr>
<tr class="even">
<td><p>Default-example.png</p></td>
<td><p>320 x 480</p></td>
<td><p>example:// URL on standard iPhone</p></td>
</tr>
<tr class="odd">
<td><p>Default-example@2x.png</p></td>
<td><p>640 x 960</p></td>
<td><p>example:// URL on high-resolution iPhone</p></td>
</tr>
<tr class="even">
<td><p>Default-example~ipad.png</p></td>
<td><p>768 x 1004</p></td>
<td><p>example:// URL on iPad in portrait orientations</p></td>
</tr>
<tr class="odd">
<td><p>Default-example-Landscape.png</p></td>
<td><p>1024 x 768</p></td>
<td><p>example:// URL on iPad in landscape orientations</p></td>
</tr>
</tbody>
</table>

This example only illustrates one approach. You could, for example, use the
`Default.png` image for the iPad, and specify specific launch images for the
iPhone and iPod with `Default~iphone.png` and `Default@2x~iphone.png`.

#### See also

[iOS Application Programming Guide: Application Launch Images](http://developer.apple.com/library/ios/#documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/App-RelatedResources/App-RelatedResources.html#//apple_ref/doc/uid/TP40007072-CH6-SW12)

#### Launch images to package for iOS devices

|                       |                         |                                           |                 |
| --------------------- | ----------------------- | ----------------------------------------- | --------------- |
| **Devices**           | **Resolution (pixels)** | **Launch image name**                     | **Orientation** |
| **iPhones**           |                         |                                           |                 |
| iPhone 4 (non-retina) | 640 x 960               | Default~iphone.png                        | Potrait         |
| iPhone 4, 4s          | 640 x 960               | Default@2x~iphone.png                     | Potrait         |
| iPhone 5, 5c, 5s      | 640 x 1136              | Default-568h@2x~iphone.png                | Potrait         |
| iPhone 6,7,8          | 750 x 1334              | Default-375w-667h@2x~iphone.png           | Potrait         |
| iPhone 6+,7+,8+       | 1242 x 2208             | Default-414w-736h@3x~iphone.png           | Potrait         |
| iPhone 6+,7+,8+       | 2208 x 1242             | Default-Landscape-414w-736h@3x~iphone.png | Landscape       |
| iPhone X,XS           | 1125 x 2436             | Default-812h@3x~iphone.png                | Portrait        |
| iPhone X,XS           | 2436 x 1125             | Default-Landscape-812h@3x~iphone.png      | Landscape       |
| iPhone XR             | 828 x 1792              | Default-896h@2x~iphone.png                | Portrait        |
| iPhone XR             | 1792 x 828              | Default-Landscape-896h@2x~iphone.png      | Landscape       |
| iPhone XS Max         | 1242 x 2688             | Default-414w-896h@3x~iphone.png           | Portrait        |
| iPhone XS Max         | 2688 x 1242             | Default-Landscape-414w-896h@3x~iphone.png | Landscape       |
| **iPads**             |                         |                                           |                 |
| iPad 1, 2             | 768 x 1024              | Default-Portrait~ipad.png                 | Potrait         |
| iPad 1, 2             | 1024 x 768              | Default-Landscape~ipad.png                | Landscape       |
| iPad 3, Air           | 1536 x 2048             | Default-Portrait@2x~ipad.png              | Potrait         |
| iPad 3, Air           | 2048 x 1536             | Default-LandscapeLeft@2x~ipad.png         | Landscape       |
| iPad Pro (10.5")      | 1668 x 2224             | Default-Portrait-1112h@2x.png             | Portrait        |
| iPad Pro (10.5")      | 2224 x 1668             | Default-Landscape-1112h@2x.png            | Landscape       |
| iPad Pro (11")        | 1668 x 2388             | Default-Portrait-1194h@2x.png             | Portrait        |
| iPad Pro (11")        | 2388 x 1668             | Default-Landscape-1194h@2x.png            | Landscape       |
| iPad Pro (12.9")      | 2048 x 2732             | Default-Portrait@2x.png                   | Portrait        |
| iPad Pro (12.9")      | 2732 x 2048             | Default-Landscape@2x.png                  | Landscape       |

#### Art guidelines

You can create any art you'd like for a launch image, as long as it is the
correct dimensions. However, it is often best to have the image match the
initial state of your application. You can create such a launch image by taking
a screenshot of the startup screen of your application:

1.  Open your application on the iOS device. When the first screen of the user
    interface appears, press and hold the Home button (below the screen). While
    holding the Home button, press the Power/Sleep button (at the top of the
    device). This takes a screenshot and sends it to the Camera Roll.

2.  Transfer the image to your development computer by transferring photos from
    iPhoto or another photo transfer application.

Do not include text in the launch image if your application is localized into
multiple languages. The launch image is static and the text would not match
other languages.

#### See also

[iOS Human Interface Guidelines: Launch images](https://developer.apple.com/ios/human-interface-guidelines/icons-and-images/launch-screen/)

## Icons and launch images for tvOS

Follow the steps below to create Assets.car using Xcode for generating
application icons, launch images, and TopShelf Images for your Apple TV
application.

Step 1. On your Mac, open Xcode and choose File \> New \> Project \> tvOS
Application \> Single View Application. Provide a name to the app and click
create. In the general tab of your project, select your Deployment Target.

Step 2. Click Assets.xcassets in the left column and drag your images to
different sections App Icon - Large, App Icon - Small, Top Shelf Image, and
Launch Image.

For icon sizes and specifications, follow Apple's guidelines for tvOS icons and
images.

Step 3.Run this native app on your tvOS device (tvOS 9.2+) and check if your
icons and images appear correctly. Go to the .app file created in your file
system where you created the project — right click on .app file and click on
show package contents.

Copy the Assets.car file from the package. You can package the app with the
extracted Assets.car as shown in the following ADT command.

    <path to adt> -package -target ipa-app-store -provisioning-profile <.mobileprovision> -keystore <.p12> -storetype pkcs12 -storepass <password> <.ipa> <.xml> <.swf> Assets.car

Add the tags mentioned below in the application descriptor file before packaging
for your images:

    <key>UILaunchImages</key>
    <array>
        <dict>
            <key>UILaunchImageSize</key>
            <string>{1920, 1080}</string>
            <key>UILaunchImageName</key>
            <string>LaunchImage</string>
            <key>UILaunchImageMinimumOSVersion</key>
            <string>9.0</string>
            <key>UILaunchImageOrientation</key>
            <string>Landscape</string>
        </dict>>
    </array>
    <key>TVTopShelfImage</key>
    <dict>
    <key>TVTopShelfPrimaryImage</key>
    <string>Top Shelf Image</string>
    <key>TVTopShelfPrimaryImageWide</key>
    <string>Top Shelf Image Wide</string>
    </dict>
    <key>CFBundleIcons</key>
    <dict>
    <key>CFBundlePrimaryIcon>/key>
    <string>App Icon - Small</string>
    </dict>

Note:

1\. If Assets.car is created from Xcode 9, icon tag in application descriptor
file should be:

    <key>CFBundlePrimaryIcon</key>
    <string>App Icon</string>

If Assets.car is created from Xcode 8, icon tag in application descriptor file
should be:

    <key>CFBundlePrimaryIcon</key>
    <string>App Icon - Small</string>

## Ignored settings

Applications on mobile devices ignore application settings that apply to native
windows or desktop operating system features. The ignored settings are:

- allowBrowserInvocation

- customUpdateUI

- fileTypes

- height

- installFolder

- maximizable

- maxSize

- minimizable

- minSize

- programMenuFolder

- resizable

- systemChrome

- title

- transparent

- visible

- width

- x

- y

More Help topics

[application](WSfffb011ac560372f2fea1812938a6e463-7fff.html)

[id](WSfffb011ac560372f2fea1812938a6e463-7ffe.html)

[filename](WSfffb011ac560372f2fea1812938a6e463-7ff9.html)

[name](WSfffb011ac560372f2fea1812938a6e463-7ffd.html)

[version](WSfffb011ac560372f2fea1812938a6e463-7ffc.html)

[versionLabel](WSfffb011ac560372f2fea1812938a6e463-7ffa.html)

[versionNumber](WSfffb011ac560372f2fea1812938a6e463-7ffb.html)

[aspectRatio](WSfffb011ac560372f2fea1812938a6e463-7fe6.html)

[autoOrients](WSfffb011ac560372f2fea1812938a6e463-7fe5.html)

[depthAndStencil](WS99d2e2affb7f39bd-2d75e77d134e7ea3560-8000.html)

[fullScreen](WSfffb011ac560372f2fea1812938a6e463-7fe4.html)

[renderMode](WSfffb011ac560372f2fea1812938a6e463-7fe3.html)

[supportedProfiles](WSfffb011ac560372f2fea1812938a6e463-7fe2.html)

[Device profiles](WS144092a96ffef7cc16ddeea2126bb46b82f-8000.html)

[AIR Debug Launcher (ADL)](WSfffb011ac560372f-6fa6d7e0128cca93d31-8000.html)

[softKeyboardBehavior](WSfffb011ac560372f1a6f6f1912d7748050e-7fff.html)

[requestedDisplayResolution](WSfffb011ac560372f-4cb7055d12d779150e8-8000.html)

[icon](WSfffb011ac560372f2fea1812938a6e463-7ff6.html)

[imageNxN](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html)

![](../img/as3LinkIndicator.png) 
[Virtual keyboards](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/WSfffb011ac560372f2e63562a12dedf852e9-8000.html)

![](../img/flashplatformLinkIndicator.png) 
[Stage.softKeyboardRect](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/Stage.html#softKeyboardRect)

![](../img/flashplatformLinkIndicator.png) 
[SoftKeyboardEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/SoftKeyboardEvent.html)

[Android Security and Permissions](http://developer.android.com/guide/topics/security/security.html)

[Android Manifest.permission class](http://developer.android.com/reference/android/Manifest.permission.html)

[Android intent filters](http://developer.android.com/guide/topics/intents/intents-filters.html#ifs)

[Android actions and categories](http://developer.android.com/reference/android/content/Intent.html#constants)

[Android Developers: Android Compatibility](http://developer.android.com/guide/practices/compatibility.html)

[Android Developers: Android feature name constants](http://developer.android.com/reference/android/content/pm/PackageManager.html#FEATURE_BLUETOOTH)

[Renaun Erickson: Developing for both retina and non-retina iOS screens using AIR 2.6](http://renaun.com/blog/2011/03/developing-for-both-retina-and-non-retina-ios-screens-using-air-2-6/)

[Android Developers: Icon Design Guidelines](http://developer.android.com/guide/practices/ui_guidelines/icon_design.html)

[iOS Human Interface Guidelines: Custom Icon and Image Creation Guidelines](https://developer.apple.com/library/ios/#documentation/UserExperience/Conceptual/MobileHIG/IconsImages/IconsImages.html)
