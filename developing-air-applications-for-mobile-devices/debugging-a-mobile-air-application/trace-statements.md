# Trace statements

When you run your mobile application on the desktop, trace output is printed to
either the debugger or the terminal window used to launch ADL. When you run your
application on a device or emulator, you can set up a remote debugging session
to view trace output. Where supported, you can also view trace output using the
software development tools provided by the device or operating system maker.

In all cases, the SWF files in the application must be compiled with debugging
enabled in order for the runtime to output any trace statements.

#### Remote trace statements on Android

When running on an Android device or emulator, you can view trace statement
output in the Android system log using the Android Debug Bridge (ADB) utility
included in the Android SDK. To view the output of your application, run the
following command from a command prompt or terminal window on your development
computer:

    tools/adb logcat air.MyApp:I *:S

where _MyApp_ is the AIR application ID of your application. The argument `*:S`
suppresses output from all other processes. To view system information about
your application in addition to the trace output, you can include the
ActivityManager in the logcat filter specification:

    tools/adb logcat air.MyApp:I ActivityManager:I *:S

These command examples assume that you are running ADB from the Android SDK
folder or that you have added the `SDK` folder to your path environment
variable.

> **Note:** In AIR 2.6+, the ADB utility is included in the AIR SDK and can be
> found in the lib/android/bin folder.

#### Remote trace statements on iOS

To view the output of trace statements from an application running on an iOS
device, you must establish a remote debugging session using the Flash Debugger
(FDB).

More Help topics

[Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html)

[Android Debug Bridge: Enable logcat Logging](http://developer.android.com/guide/developing/tools/adb.html#logcat)
