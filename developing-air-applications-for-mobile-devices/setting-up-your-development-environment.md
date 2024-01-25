# Setting up your development environment

Mobile platforms have additional setup requirements beyond the normal AIR, Flex,
and Flash development environment setup. (For more information about setting up
the basic AIR development environment, see
[Adobe Flash Platform tools for AIR development](WS2d8d13466044a7337d7adee012406959c52-8000.html).)

## Android setup

No special setup is normally required for Android in AIR 2.6+. The Android ADB
tool is included in the AIR SDK (in the lib/android/bin folder). The AIR SDK
uses the ADB tool to install, uninstall, and run application packages on the
device. You can also use ADB to view system logs. To create and run an Android
emulator you must download the separate Android SDK.

If your application adds elements to the `<manifestAdditions>` element in the
application descriptor that the current version of AIR does not recognize as
valid, then you must install a more recent version of the Android SDK. Set the
AIR_ANDROID_SDK_HOME environment variable or the `-platformsdk` command line
parameter to the file path of the SDK. The AIR packaging tool, ADT, uses this
SDK to validate the entries in the `<manifestAdditions>` element.

In AIR 2.5, you must download a separate copy of the Android SDK from Google.
You can set the AIR_ANDROID_SDK_HOME environment variable to reference the
Android SDK folder. If you do not set this environment variable, you must
specify the path to the Android SDK in the `-platformsdk` argument on the ADT
command line.

## iOS setup

To install and test an iOS application on a device and to distribute that
application, you must join the Apple iOS Developer program (which is a fee-based
service). Once you join the iOS Developer program you can access the iOS
Provisioning Portal where you can obtain the following items and files from
Apple that are required to install an application on a device for testing and
for subsequent distribution. These items and files include:

- Development and distribution certificates

- App IDs

- Development and distribution provisioning files

More Help topics

[ADT environment variables](WS901d38e593cd1bac1e63e3d129cf8c19f1-8000.html)

[Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html)
