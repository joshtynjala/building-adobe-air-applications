# Android APK packages

<div>

<div>

#### Creating an APK package

To create an APK package, use the ADT package command, setting the target type
to _apk_ for release builds, _apk-debug_ for debug builds, or _apk-emulator_ for
release-mode builds for running on an emulator.

    adt     -package
                                    -target apk
                                    -storetype pkcs12 -keystore ../codesign.p12
                                    myApp.apk
                                    myApp-app.xml
                                    myApp.swf icons

Type the entire command on a single line; line breaks in the above example are
only present to make it easier to read. Also, the example assumes that the path
to the ADT tool is on your command-line shell’s path definition. (See
[Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html)
for help.)

You must run the command from the directory containing the application files.
The application files in the example are myApp-app.xml (the application
descriptor file), myApp.swf, and an icons directory.

When you run the command as shown, ADT will prompt you for the keystore
password. (The password characters you type are not displayed; just press Enter
when you are done typing.)

<div>

Note: By default, all AIR Android applications have the `air.` prefix in the
package name. To opt out of this default behavior, set the environment variable,
`AIR_NOANDROIDFLAIR` to _true_, on your computer.

</div>

</div>

<div>

#### Creating an APK package for an application that uses native extensions

To create an APK package for an application that uses native extensions, add the
`-extdir` option in addition to the normal packaging options. In case of
multiple ANEs that share resources/libraries, the ADT only picks a single
resource/library and ignores other duplicate entries before issuing a warning.
This option specifies the directory that contains the ANE files that the
application uses. For example:

    adt     -package
                                    -target apk
                                    -storetype pkcs12 -keystore ../codesign.p12
                                    myApp.apk
                                    myApp-app.xml
                                    -extdir extensionsDir
                                    myApp.swf icons

</div>

<div>

#### Creating an APK package that includes its own version of the AIR runtime

To create an APK package that contains both the application and a captive
version of the AIR runtime, use the `apk-captive-runtime` target. This option
specifies the directory that contains the ANE files that the application uses.
For example:

    adt     -package
                                    -target apk-captive-runtime
                                    -storetype pkcs12 -keystore ../codesign.p12
                                    myApp.apk
                                    myApp-app.xml
                                    myApp.swf icons

Possible drawbacks of this technique include:

- Critical security fixes are not automatically available to users when Adobe
  publishes a security patch

- Larger application RAM footprint

<div>

Note: When you bundle the runtime, ADT adds the `INTERNET` and
`BROADCAST_STICKY` permissions to your application. These permissions are
required by the AIR runtime.

</div>

</div>

<div>

#### Creating a debug APK package

To create a version of the app that you can use with a debugger, use apk-debug
as the target and specify connection options:

    adt     -package
                                    -target apk-debug
                                    -connect 192.168.43.45
                                    -storetype pkcs12 -keystore ../codesign.p12
                                    myApp.apk
                                    myApp-app.xml
                                    myApp.swf icons

The -connect flag tells the AIR runtime on the device where to connect to a
remote debugger over the network. To debug over USB, you must specify the
`-listen` flag instead, specifying the TCP port to use for the debug connection:

    adt     -package
                                    -target apk-debug
                                    -listen 7936
                                    -storetype pkcs12 -keystore ../codesign.p12
                                    myApp.apk
                                    myApp-app.xml
                                    myApp.swf icons

For most debugging features to work, you must also compile the application SWFs
and SWCs with debugging enabled. See
[Debugger connection options](WS901d38e593cd1bac1e63e3d128fc240122-7ff1.html)
for a full description of the `-connect` and `-listen` flags.

<div>

Note: By default, ADT packages a captive copy of the AIR runtime with your
Android app while packaging app with apk-debug target. To force ADT to create an
APK that uses an external runtime, set the `AIR_ANDROID_SHARED_RUNTIME`
environment variable to `true`.

</div>

On Android, the app must also have permission to access the Internet in order
for it to connect to the computer running the debugger over the network. See
[Android permissions](WS901d38e593cd1bac1e63e3d129d39606f2-8000.html).

</div>

<div>

#### Creating an APK package for use on an Android emulator

You can use a debug APK package on an Android emulator, but not a release mode
package. To create a release mode APK package for use on an emulator, use the
ADT package command, setting the target type to _apk-emulator_:

    adt -package -target apk-emulator -storetype pkcs12 -keystore ../codesign.p12 myApp.apk myApp-app.xml myApp.swf icons

The example assumes that the path to the ADT tool is on your command-line
shell’s path definition. (See
[Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html)
for help.)

</div>

<div>

#### Creating an APK package from an AIR or AIRI file

You can create an APK package directly from an existing AIR or AIRI file:

    adt -target apk -storetype pkcs12 -keystore ../codesign.p12 myApp.apk myApp.air

The AIR file must use the AIR 2.5 (or later) namespace in the application
descriptor file.

</div>

<div>

#### Creating an APK package for the Android x86 platform

Begining AIR 14, the argument, `-arch`, can be used to package an APK for the
Android x86 platform. For example:

        adt     -package
                                    -target apk-debug
                                    -listen 7936
                                    -arch x86
                                    -storetype pkcs12 -keystore ../codesign.p12
                                    myApp.apk
                                    myApp-app.xml
                                    myApp.swf icons

</div>

</div>

<div>

<div>



</div>

</div>
