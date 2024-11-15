# Remote debugging with FDB over USB

To debug an app over a USB connection, you package the application using the
`‑listen` option instead of the `-connect` option. When you specify the
`‑listen` option, the runtime listens for a connection from the Flash debugger
(FDB) on TCP port 7936 when you launch the application. You then run FDB with
the `-p` option, and FDB initiates the connection.

**USB debugging procedure for Android**

In order for the Flash debugger running on the desktop computer to connect to
the AIR runtime running on the device or emulator, you must use the Android
Debug Bridge (ADB - utility from the Android SDK) or the iOS Debug Bridge (IDB -
utility from the AIR SDK) to forward the device port to the desktop port.

1.  Open a terminal or command prompt window and navigate to the directory
    containing the source code for the application.

2.  Compile the application with amxmlc, enabling debugging:

        amxmlc -debug DebugExample.as

3.  Package the application using the appropriate debug target (such as
    `apk-debug`) and specify the `‑listen` option:

        adt -package -target apk-debug -listen -storetype pkcs12 -keystore ../../AndroidCert.p12 DebugExample.apk DebugExample-app.xml DebugExample.swf

4.  Connect the device to the debug computer with a USB cable. (You can also use
    this procedure to debug an application running in an emulator, in which
    case, a USB connection is not necessary — or possible.)

5.  Install the application.

    You can use the ADT `-installApp` command:

        adt -installApp -platform android -package DebugExample.apk

6.  Forward TCP port 7936 from the device or emulator to the desktop computer
    using the Android ADB utility:

        adb forward tcp:7936 tcp:7936

7.  Launch the application on the device.

8.  In a terminal or command window run FDB using the -p option:

        fdb -p 7936

9.  In the FDB window, type the `run` command:

        Adobe fdb (Flash Player Debugger) [build 14159]
                                            Copyright (c) 2004-2007 Adobe, Inc. All rights reserved.
                                            (fdb) run

10. The FDB utility attempts to connect to the application.

11. When the remote connection is established, you can set breakpoints with the
    FDB `break` command and then start execution with the `continue` command:

        (fdb) run
                                            Player connected; session starting.
                                            Set breakpoints and then type 'continue' to resume the session.
                                            [SWF] Users:juser:Documents:FlashProjects:DebugExample:DebugExample.swf - 32,235 bytes after decompression
                                            (fdb) break clickHandler
                                            Breakpoint 1 at 0x5993: file DebugExample.as, line 14
                                            (fdb) continue

> **Note:** Port number 7936 is used as the default for USB debugging by both
> the AIR runtime and FDB. You can specify different ports to use with the ADT
> -listen port parameter and the FDB -p port parameter. In this case you must
> use the Android Debug Bridge utility to forward the port number specified in
> ADT to the port specified in FDB:
> `adb forward tcp:adt_listen_port# tcp:fdb_port#`

**USB debugging procedure for iOS**

In order for the Flash debugger running on the desktop computer to connect to
the AIR runtime running on the device or emulator, you must use the iOS Debug
Bridge (IDB - utility from the AIR SDK) to forward the device port to the
desktop port.

1.  Open a terminal or command prompt window and navigate to the directory
    containing the source code for the application.

2.  Compile the application with amxmlc, enabling debugging:

        amxmlc -debug DebugExample.as

3.  Package the application using the appropriate debug target (such as
    `ipa-debug` or `ipa-debug-interpreter`, and specify the `‑listen` option:

        adt -package -target ipa-debug-interpreter -listen 16000
                                            -provisioning-profile xyz.mobileprovision -storetype pkcs12 -keystore Certificates.p12
                                            -storepass pass123 OutputFile.ipa InputFile-app.xml InputFile.swf

4.  Connect the device to the debug computer with a USB cable. (You can also use
    this procedure to debug an application running in an emulator, in which
    case, a USB connection is not necessary — or possible.)

5.  Install and launch the application on the iOS device. In AIR 3.4 and higher,
    you can use `adt ‑installApp` to install the application over USB.

6.  Determine the device handle by using the `idb -devices` command (IDB is
    located in _`air_sdk_root`_`/lib/aot/bin/iOSBin/idb`):

        ./idb -devices

                                            List of attached devices
                                            Handle    UUID
                                                1     91770d8381d12644df91fbcee1c5bbdacb735500

    Note: (AIR 3.4 and higher) You can use `adt ‑devices` instead of
    `idb ‑devices` to determine the device handle.

7.  Forward a port on your desktop to the port specified in the
    `adt ‑listen`parameter (in this case, 16000; the default is 7936) using the
    IDB utility and the Device ID found in the previous step:

        idb -forward 7936 16000 1

    In this example, 7936 is the desktop port, 16000 is the port that the
    connected device listens on, and 1 is the Device ID of the connected device.

8.  In a terminal or command window run FDB using the -p option:

        fdb -p 7936

9.  In the FDB window, type the `run` command:

        Adobe fdb (Flash Player Debugger) [build 23201]
                                            Copyright (c) 2004-2007 Adobe, Inc. All rights reserved.
                                            (fdb) run

10. The FDB utility attempts to connect to the application.

11. When the remote connection is established, you can set breakpoints with the
    FDB `break` command and then start execution with the `continue` command:

> **Note:** Port number 7936 is used as the default for USB debugging by both
> the AIR runtime and FDB. You can specify different ports to use with the IDB
> -listen port parameter and the FDB -p port parameter.
