# ADT uninstallApp command

<div>

The -uninstallApp command completely removes an installed app on a remote device
or emulator. The command uses the following syntax:

    adt -uninstallApp -platform platformName -platformsdk path_to_sdk -device deviceID -appid applicationID

**-platform** The name of the platform of the device. Specify _ios_ or
_android_.

<div>

**-platformsdk** The path to the platform SDK for the target device:

- Android - The AIR 2.6+ SDK includes the tools from the Android SDK needed to
  implement the relevant ADT commands. Only set this value to use a different
  version of the Android SDK. Also, the platform SDK path does not need to be
  supplied on the command line if the AIR_ANDROID_SDK_HOME environment variable
  is already set. (If both are set, then the path provided on the command line
  is used.)

- iOS - The AIR SDK ships with a captive iOS SDK. The -platformsdk option lets
  you package applications with an external SDK so that you are not restricted
  to using the captive iOS SDK. For example, if you have built an extension with
  the latest iOS SDK, you can specify that SDK when packaging your application.
  Additionally, when using ADT with the iOS Simulator, you must always include
  the -platformsdk option, specifying the path to the iOS Simulator SDK.

</div>

**-device** Specify _ios_simulator_ or the serial number of the device. The
device only needs to be specified when more than one Android device or emulator
is attached to your computer and running. If the specified device is not
connected, ADT returns exit code 14: Device error. If more than one device or
emulator is connected and a device is not specified, ADT returns exit code 2:
Usage error.

On Android, use the Android ADB tool to list the serial numbers of attached
devices and running emulators:

    adb devices

**-appid** The AIR application ID of the installed application. If no
application with the specified ID is installed on the device, then ADT returns
exit code 14: Device error.

</div>

<div>

<div>



</div>

</div>
