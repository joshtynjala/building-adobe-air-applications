# AIR for TV application descriptor properties

<div>

As with other AIR applications, you set the basic application properties in the
application descriptor file. TV profile applications ignore some of the
desktop-specific properties, such as window size and transparency. Applications
targeting devices in the `extendedTV` profile can use native extensions. These
applications identify the native extensions used in an `extensions` element.

</div>

<div>

## Common settings

<div>

Several application descriptor settings are important for all TV profile
applications.

</div>

<div>

### Required AIR runtime version

<div>

Specify the version of the AIR runtime required by your application using the
namespace of the application descriptor file.

The namespace, assigned in the
[`application`](WSfffb011ac560372f2fea1812938a6e463-7fff.html) element,
determines, in large part, which features your application can use. For example,
consider an application that uses the AIR 2.5 namespace, but the user has some
future version installed. In this case, the application still sees the AIR 2.5
behavior, even if the behavior is different in the future AIR version. Only when
you change the namespace and publish an update can your application have access
to the new behavior and features. Security fixes are an important exception to
this rule.

Specify the namespace using the `xmlns` attribute of the root `application`
element:

    <application xmlns="http://ns.adobe.com/air/application/2.5">

AIR 2.5 is the first version of AIR to support TV applications.

</div>

</div>

<div>

### Application identity

<div>

Several settings should be unique for each application that you publish. These
settings include the elements
[`id`](WSfffb011ac560372f2fea1812938a6e463-7ffe.html),
[`name`](WSfffb011ac560372f2fea1812938a6e463-7ffd.html), and
[`filename`](WSfffb011ac560372f2fea1812938a6e463-7ff9.html).

    <id>com.example.MyApp</id>
    <name>My Application</name>
    <filename>MyApplication</filename>

</div>

</div>

<div>

### Application version

<div>

Specify the application version in the
[`versionNumber`](WSfffb011ac560372f2fea1812938a6e463-7ffb.html) element. When
specifying a value for `versionNumber`, you can use a sequence of up to three
numbers separated by dots, such as: “0.1.2”. Each segment of the version number
can have up to three digits. (In other words, “999.999.999” is the largest
version number permitted.) You do not have to include all three segments in the
number; “1” and “1.0” are legal version numbers as well.

You can also specify a label for the version using the
[`versionLabel`](WSfffb011ac560372f2fea1812938a6e463-7ffa.html) element. When
you add a version label, it is displayed instead of the version number.

    <versionNumber>1.23.7<versionNumber>
    <versionLabel>1.23 Beta 7</versionLabel>

</div>

</div>

<div>

### Main application SWF

<div>

Specify the main application SWF file in the
[`versionLabel`](WSfffb011ac560372f2fea1812938a6e463-7ffa.html) child of the
[`initialWindow`](WSfffb011ac560372f2fea1812938a6e463-7ff5.html) element. When
you target devices in the tv profile, you must use a SWF file (HTML-based
applications are not supported).

    <initialWindow>
        <content>MyApplication.swf</content>
    </initialWindow>

You must include the file in the AIR package (using ADT or your IDE). Simply
referencing the name in the application descriptor does not cause the file to be
included in the package automatically.

</div>

</div>

<div>

### Main screen properties

<div>

Several child elements of the
[`initialWindow`](WSfffb011ac560372f2fea1812938a6e463-7ff5.html) element control
the initial appearance and behavior of the main application screen. While most
of these properties are ignored on devices in the TV profiles, you can use the
[`fullScreen`](WSfffb011ac560372f2fea1812938a6e463-7fe4.html) element:

- **`fullScreen`** — Specifies whether the application should take up the full
  device display, or should share the display with the normal operating system
  chrome.

      <fullScreen>true</fullScreen>

</div>

</div>

<div>

### The visible element

<div>

The [`visible`](WSfffb011ac560372f2fea1812938a6e463-7ff0.html) element is a
child element of the
[`initialWindow`](WSfffb011ac560372f2fea1812938a6e463-7ff5.html) element. AIR
for TV ignores the `visible` element because your application’s content is
always visible on AIR for TV devices.

However, set the `visible` element to `true` if your application also targets
desktop devices.

On desktop devices, this element’s value defaults to `false`. Therefore, if you
do not include the `visible` element, the application’s content is not visible
on desktop devices. Although you can use the ActionScript class NativeWindow to
make the content visible on desktop devices, the TV device profiles do not
support the NativeWindow class. If you try to use the NativeWindow class on an
application running on an AIR for TV device, the application fails to load.
Whether you call a method of the NativeWindow class does not matter; an
application using the class does not load on an AIR for TV device.

</div>

</div>

<div>

### Supported profiles

<div>

If your application only makes sense on a television device, then you can
prevent its installation on other types of computing devices. Exclude the other
profiles from the supported list in the
[`supportedProfiles`](WSfffb011ac560372f2fea1812938a6e463-7fe2.html) element:

    <supportedProfiles>tv extendedTV</supportedProfiles>

If an application uses a native extension, include only the `extendedTV` profile
in the supported profile list:

    <supportedProfiles>extendedTV</supportedProfiles>

If you omit the `supportedProfiles` element, then the application is assumed to
support all profiles.

Do not include _only_ the `tv` profile in the `supportedProfiles` list. Some TV
devices always run AIR for TV in a mode that corresponds to the `extendedTV`
profile. This behavior is so that AIR for TV can run applications that use
native extensions. If your `supportedProfiles` element specifies only `tv`, it
is declaring that your content is incompatible with the AIR for TV mode for
`extendedTV`. Therefore, some TV devices do not load an application that
specifies only the `tv` profile.

For a list of ActionScript classes supported in the `tv` and `extendedTV`
profiles, see
[Capabilities of different profiles](WS144092a96ffef7cc16ddeea2126bb46b82f-7ffe.html).

</div>

</div>

</div>

<div>

## Required native extensions

<div>

Applications that support the `extendedTV` profile can use native extensions.

Declare all native extensions that the AIR application uses in the application
descriptor using the
[`extensions`](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffd.html) and
[`extensionID`](WSfffb011ac560372f2fea1812938a6e463-7fda.html) elements. The
following example illustrates the syntax for specifying two required native
extensions:

    <extensions>
         <extensionID>com.example.extendedFeature</extensionID>
        <extensionID>com.example.anotherFeature</extensionID>
    </extensions>

If an extension is not listed, the application cannot use it.

The `extensionID` element has the same value as the `id` element in the
extension descriptor file. The extension descriptor file is an XML file called
extension.xml. It is packaged in the ANE file you receive from the device
manufacturer.

If you list an extension in the `extensions` element, but the AIR for TV device
does not have the extension installed, the application cannot run. The exception
to this rule is if the ANE file that you package with your AIR for TV
application has a stub version of the extension. If so, the application can run,
and it uses the stub version of the extension. The stub version has ActionScript
code, but no native code.

</div>

</div>

<div>

## Application icons

<div>

<div>

Requirements for application icons in televisions devices are device-dependent.
For example, the device manufacturer specifies:

- Required icons and icon sizes.

- Required file types and naming conventions.

- How to provide the icons for your application, such as whether to package the
  icons with your application.

- Whether to specify the icons in an
  [`icon`](WSfffb011ac560372f2fea1812938a6e463-7ff6.html) element in the
  application descriptor file.

- Behavior if the application does not provide icons.

Consult the device manufacturer for details.

</div>

</div>

</div>

<div>

## Ignored settings

<div>

Applications on television devices ignore application settings that apply to
mobile, native window, or desktop operating system features. The ignored
settings are:

- allowBrowserInvocation

- aspectRatio

- autoOrients

- customUpdateUI

- fileTypes

- height

- installFolder

- maximizable

- maxSize

- minimizable

- minSize

- programMenuFolder

- renderMode

- resizable

- systemChrome

- title

- transparent

- visible

- width

- x

- y

</div>

</div>

<div>

<div>



</div>

</div>
