# Installing AIR and AIR applications on mobile devices

End users of your app can install the AIR runtime and AIR applications using the
normal application and distribution mechanism for their device.

On Android, for example, users can install applications from the Android Market.
Or, if they have allowed the installation of apps from unknown sources in the
Application settings, users can install an app by clicking a link on a web page,
or by copying the application package to their device and opening it. If a user
attempts to install an Android app, but doesn't have the AIR runtime installed
yet, then they will be automatically directed to the Market where they can
install the runtime.

On iOS, there are two ways to distribute applications to end users. The primary
distribution channel is the Apple App Store. You can also use ad hoc
distribution to allow a limited number of users to install your application
without going though the App Store.

## Install the AIR runtime and applications for development

Since AIR applications on mobile devices are installed as native packages, you
can use the normal platform facilities for installing applications for testing.
Where supported, you can use ADT commands to install the AIR runtime and AIR
applications. Currently, this approach is supported on Android.

On iOS, you can install applications for testing using iTunes. Test applications
must be signed with an Apple code-signing certificate issued specifically for
application development and packaged with a development provisioning profile. An
AIR application is a self-contained package on iOS. A separate runtime is not
used.

#### Installing AIR applications using ADT

While developing AIR applications, you can use ADT to install and uninstall both
the runtime and your apps. (Your IDE may also integrate these commands so that
you do not have to run ADT yourself.)

You can install AIR runtime on a device or emulator using the AIR ADT utility.
The SDK provided for the device must be installed. Use the `-installRuntime`
command:

    adt -installRuntime -platform android -device deviceID -package path-to-runtime

If the `-package` parameter is not specified, the runtime package appropriate to
the device or emulator is chosen from those available in your installed AIR SDK.

To install an AIR application on Android or iOS (AIR 3.4 and higher), use the
similar `-installApp` command:

    adt -installApp -platform android -device deviceID -package path-to-app

The value set for the `-platform` argument should match the device on which you
are installing.

> **Note:** Existing versions of the AIR runtime or the AIR application must be
> removed before reinstalling.

#### Installing AIR applications on iOS devices using iTunes

To install an AIR application on an iOS device for testing:

1.  Open the iTunes application.

2.  If you have not already done so, add the provisioning profile for this
    application to iTunes. In iTunes, select File \> Add To Library. Then,
    select the provisioning profile file (which has mobileprovision as the file
    type).

3.  Some versions of iTunes do not replace the application if the same version
    of the application is already installed. In this case, delete the
    application from your device and from the list of applications in iTunes.

4.  Double-click the IPA file for your application. It should appear in the list
    of applications in iTunes.

5.  Connect your device to the USB port on your computer.

6.  In iTunes, check the Application tab for the device, and ensure that the
    application is selected in the list of applications to be installed.

7.  Select the device in the left-hand list of the iTunes application. Then
    click the Sync button. When the sync completes, the Hello World application
    appears on your iPhone.

If the new version is not installed, delete it from your device and from the
list of applications in iTunes, and then redo this procedure. This may be the
case if the currently installed version uses the same application ID and
version.

## Running AIR applications on a device

You can launch installed AIR applications using the device user interface. Where
supported, you can also launch applications remotely using the AIR ADT utility:

    adt -launchApp -platform android -device deviceID -appid applicationID

The value of the `-appid` argument must be the AIR application ID of the AIR app
to launch. Use the value specified in the AIR application descriptor (without
the _air._ prefix added during packaging).

If only a single device or emulator is attached and running, then you can omit
the `-device` flag. The value set for the `-platform` argument should match the
device on which you are installing. Currently, the only supported value is
_android_.

## Removing the AIR runtime and applications

You can use the normal means for removing applications provided by the device
operating system. Where supported, you can also use the AIR ADT utility to
remove the AIR runtime and applications. To remove the runtime, use the
`-uninstallRuntime` command:

    adt -uninstallRuntime -platform android -device deviceID

To uninstall an application use the `-uninstallApp` command:

    adt -uninstallApp -platform android -device deviceID -appid applicationID

If only a single device or emulator is attached and running, then you can omit
the `-device` flag. The value set for the `-platform` argument should match the
device on which you are installing. Currently, the only supported value is
_android_.

## Setting up an emulator

To run your AIR application on a device emulator, you must typically use the SDK
for the device to create and run an emulator instance on your development
computer. You can then install the emulator version of the AIR runtime and your
AIR application on the emulator. Note that applications on an emulator typically
run much slower than they do on an actual device.

### Create an Android emulator

1.  Launch the Android SDK and AVD Manager application:

    - On Windows, run the SDK Setup.exe file, at the root of the Android SDK
      directory.

    - On Mac OS, run the android application, in the tools subdirectory of the
      Android SDK directory

2.  Select the Settings option and select the "Force https://" option.

3.  Select the Available Packages option. You should see a list of available
    Android SDKs.

4.  Select a compatible Android SDK (Android 2.3 or later) and click the Install
    Selected button.

5.  Select the Virtual Devices option and click the New button.

6.  Make the following settings:

    - A name for your virtual device

    - The target API, such as Android 2.3, API level 8

    - A size for the SD Card (such as 1024)

    - A skin (such as Default HVGA)

7.  Click the Create AVD button.

Note that Virtual Device creation may take some time depending on your system
configuration.

Now you can launch the new Virtual Device.

1.  Select Virtual Device in the AVD Manager application. The virtual device you
    created above should be listed.

2.  Select the Virtual Device, and click the Start button.

3.  Click the Launch button on the next screen.

You should see an emulator window open on your desktop. This may take a few
seconds. It may also take some time for the Android operating system to
initialize. You can install applications packaged with the _apk-debug_ and
_apk-emulator_ on an emulator. Applications packaged with the _apk_ target do
not work on an emulator.

More Help topics

[ADT installRuntime command](WS901d38e593cd1bac1e63e3d128fc240122-7ff6.html)

[ADT installApp command](WS901d38e593cd1bac1e63e3d128fc240122-7ffa.html)

<http://developer.android.com/guide/developing/tools/othertools.html#android>

<http://developer.android.com/guide/developing/tools/emulator.html>
