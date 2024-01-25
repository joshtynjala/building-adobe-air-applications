# Remote debugging with FDB over a network connection

<div>

To debug an app running on a device with the command-line Flash Debugger (FDB),
first run the debugger on your development computer and then start the
application on the device. The following procedure uses the AMXMLC, FDB and ADT
tools to compile, package, and debug an application on the device. The examples
assume that you are using a combined Flex and AIR SDK and that the bin directory
is included in your path environment variable. (This assumption is made merely
to simplify the command examples.)

1.  Open a terminal or command prompt window and navigate to the directory
    containing the source code for the application.

2.  Compile the application with amxmlc, enabling debugging:

        amxmlc -debug DebugExample.as

3.  Package the application using either the `apk-debug` or `ipa-debug` targets:

        Android
                                            adt -package -target apk-debug -connect -storetype pkcs12 -keystore ../../AndroidCert.p12 DebugExample.apk DebugExample-app.xml DebugExample.swf

                                            iOS
                                            adt -package -target ipa-debug -connect -storetype pkcs12 -keystore ../../AppleDeveloperCert.p12 -provisioning-profile test.mobileprovision DebugExample.apk DebugExample-app.xml DebugExample.swf

    If you always use the same host name or IP address for debugging, you can
    put that value after the `-connect` flag. The app will attempt to connect to
    that IP address or host name automatically. Otherwise, you must enter the
    information on the device each time you start debugging.

4.  Install the application.

    On Android, you can use the ADT `-installApp` command:

        adt -installApp -platform android -package DebugExample.apk

    On iOS, you can install the application using the ADT `-installApp` command
    or using iTunes.

5.  In a second terminal or command window and run FDB:

        fdb

6.  In the FDB window, type the `run` command:

        Adobe fdb (Flash Player Debugger) [build 14159]
                                            Copyright (c) 2004-2007 Adobe, Inc. All rights reserved.
                                            (fdb) run
                                            Waiting for Player to connect

7.  Launch the application on the device.

8.  Once the app launches on the device or emulator, the Adobe AIR connection
    dialog opens. (If you specified a host name or IP address with the -connect
    option when you packaged the app it will attempt to connect automatically
    using that address.) Enter the appropriate address and tap OK.

    In order to connect to the debugger in this mode, the device must be able to
    resolve the address or host name and connect to TCP port 7935. A network
    connection is required.

9.  When the remote runtime connects to the debugger, you can set breakpoints
    with the FDB `break` command and then start execution with the `continue`
    command:

        (fdb) run
                                            Waiting for Player to connect
                                            Player connected; session starting.
                                            Set breakpoints and then type 'continue' to resume the session.
                                            [SWF] Users:juser:Documents:FlashProjects:DebugExample:DebugExample.swf - 32,235 bytes after decompression
                                            (fdb) break clickHandler
                                            Breakpoint 1 at 0x5993: file DebugExample.as, line 14
                                            (fdb) continue

</div>

<div>

<div>



</div>

</div>
