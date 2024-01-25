# iOS packages

<div>

On iOS, ADT converts the SWF file byte code and other source files into a native
iOS application.

1.  Create the SWF file using Flash Builder, Flash Professional, or a
    command-line compiler.

2.  Open a command shell or a terminal and navigate to the project folder of
    your iPhone application.

3.  Next, use the ADT tool to create the IPA file, using the following syntax:

        adt     -package
                                            -target [ipa-test | ipa-debug | ipa-app-store | ipa-ad-hoc |
                                            ipa-debug-interpreter | ipa-debug-interpreter-simulator
                                            ipa-test-interpreter | ipa-test-interpreter-simulator]
                                            -provisioning-profile PROFILE_PATH
                                            SIGNING_OPTIONS
                                            TARGET_IPA_FILE
                                            APP_DESCRIPTOR
                                            SOURCE_FILES
                                            -extdir extension-directory
                                            -platformsdk path-to-iossdk or path-to-ios-simulator-sdk

    Change the reference `adt` to include the full path to the adt application.
    The adt application is installed in the bin subdirectory of the AIR SDK.

    Select the `-target` option that corresponds to the type of iPhone
    application you want to create:

    - `-target ipa-test`—Choose this option to quickly compile a version of the
      application for testing on your developer iPhone. You can also use
      `ipa-test-interpreter` for even faster compilation or
      `ipa-test-interpreter-simulator` to run in the iOS Simulator.

    - `-target ipa-debug`—Choose this option to compile a debug version of the
      application for testing on your developer iPhone. With this option, you
      can use a debug session to receive `trace()` output from the iPhone
      application.

      You can include one of the following `-connect` options
      (`CONNECT_OPTIONS`) to specify the IP address of the development computer
      running the debugger:

      - `-connect`—The application will attempt to connect through wifi to a
        debug session on the development computer used to compile the
        application.

      - `-connect IP_ADDRESS`—The application will attempt to connect through
        wifi to a debug session on the computer with the specified IP address.
        For example:

            -target ipa-debug -connect 192.0.32.10

      - `-connect HOST_NAME`—The application will attempt to connect through
        wifi to a debug session on the computer with the specified host name.
        For example:

            -target ipa-debug -connect bobroberts-mac.example.com

      The `-connect` option is optional. If not specified, the resulting debug
      application will not attempt to connect to a hosted debugger.
      Alternatively, you can specify `‑listen` instead of `‑connect` to enable
      USB debugging, described in
      [Remote debugging with FDB over USB](WS901d38e593cd1bac7b2281cc12cd6bced97-8000.html).

      If a debug connection attempt fails, the application presents a dialog
      asking the user to enter the IP address of the debugging host machine. A
      connection attempt can fail if the device is not connected to wifi. It can
      also occur if the device is connected but not behind the firewall of the
      debugging host machine.

      You can also use `ipa-debug-interpreter` for faster compilation or
      `ipa-debug-interpreter-simulator` to run in the iOS Simulator.

      For more information, see
      [Debugging a mobile AIR application](WSfffb011ac560372f-5d0f4f25128cc9cd0cb-7ffa.html).

    - `-target ipa-ad-hoc`—Choose this option to create an application for ad
      hoc deployment. See the Apple iPhone developer center

    - `-target ipa-app-store`—Choose this option to create a final version of
      the IPA file for deployment to the Apple App Store.

    Replace the _`PROFILE_PATH`_ with the path to the provisioning profile file
    for your application. For more information on provisioning profiles, see
    [iOS setup](WSfffb011ac560372f46768d8712cd1d13954-8000.html).

    Use the `-platformsdk` option to point to the iOS Simulator SDK when you are
    building to run your application in the iOS Simulator.

    Replace the _`SIGNING_OPTIONS`_ to reference your iPhone developer
    certificate and password. Use the following syntax:

        -storetype pkcs12 -keystore P12_FILE_PATH -storepass PASSWORD

    Replace _P12_FILE_PATH_ with the path to your P12 certificate file. Replace
    _PASSWORD_ with the certificate password. (See the example below.) For more
    information on the P12 certificate file, see
    [Converting a developer certificate into a P12 keystore file](WSfffb011ac560372f46768d8712cd1d13954-7ffc.html).

    <div>

    Note: You can use a self-signed certificate when packaging for the iOS
    Simulator.

    </div>

    Replace the _`APP_DESCRIPTOR`_ to reference the application descriptor file.

    Replace the _`SOURCE_FILES`_ to reference the main SWF file of your project
    followed by any other assets to include. Include the paths to all icon files
    you defined in the application settings dialog box in Flash Professional or
    in a custom application descriptor file. Also, add the initial screen art
    file, Default.png.

    Use the `-extdir `_`extension-directory`_ option to specify the directory
    that contains the ANE files (native extensions) that the application uses.
    If the application uses no native extensions, do not include this option.

    <div>

    Important: Do not create a subdirectory in your application directory named
    `Resources`. The runtime automatically creates a folder with this name to
    conform to the IPA package structure. Creating your own Resources folder
    results in a fatal conflict.

    </div>

<div>

#### Creating an iOS package for debugging

To create an iOS package for installing on test devices, use the ADT package
command, setting the target type to _ios-debug_. Before running this command,
you must have already obtained a development code signing certificate and
provisioning profile from Apple.

    adt     -package
                                    -target ipa-debug
                                    -storetype pkcs12 -keystore ../AppleDevelopment.p12
                                    -provisioning-profile AppleDevelopment.mobileprofile
                                    -connect 192.168.0.12 | -listen
                                    myApp.ipa
                                    myApp-app.xml
                                    myApp.swf icons Default.png

<div>

Note: You can also use `ipa-debug-interpreter` for faster compilation or
`ipa-debug-interpreter-simulator` to run in the iOS Simulator

</div>

Type the entire command on a single line; line breaks in the above example are
only present to make it easier to read. Also, the example assumes that the path
to the ADT tool is on your command-line shell’s path definition. (See
[Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html)
for help.)

You must run the command from the directory containing the application files.
The application files in the example are myApp-app.xml (the application
descriptor file), myApp.swf, an icons directory, and the Default.png file.

You must sign the application using the correct distribution certificate issued
by Apple; other code signing certificates cannot be used.

Use the `-connect` option for wifi debugging. The application attempts to
initiate a debug session with the Flash Debugger (FDB) running on the specified
IP or host name. Use the `-listen` option for USB debugging. You first start the
application and then start FDB, which initiates a debug session for the running
application. See
[Connecting to the Flash debugger](WSfffb011ac560372f-5d0f4f25128cc9cd0cb-7ff7.html)
for more information.

</div>

<div>

#### Creating an iOS package for Apple App Store submission

To create an iOS package for submission to the Apple App store, use the ADT
package command, setting the target type to _ios-app-store_. Before running this
command, you must have already obtained a distribution code signing certificate
and provisioning profile from Apple.

    adt     -package
                                    -target ipa-app-store
                                    -storetype pkcs12 -keystore ../AppleDistribution.p12
                                    -provisioning-profile AppleDistribution.mobileprofile
                                    myApp.ipa
                                    myApp-app.xml
                                    myApp.swf icons Default.png

Type the entire command on a single line; line breaks in the above example are
only present to make it easier to read. Also, the example assumes that the path
to the ADT tool is on your command-line shell’s path definition. (See
[Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html)
for help.)

You must run the command from the directory containing the application files.
The application files in the example are myApp-app.xml (the application
descriptor file), myApp.swf, an icons directory, and the Default.png file.

You must sign the application using the correct distribution certificate issued
by Apple; other code signing certificates cannot be used.

<div>

Important: Apple requires that you use the Apple _Application Loader_ program in
order to upload applications to the App Store. Apple only publishes _Application
Loader_ for Mac OS X. Thus, while you can develop an AIR application for the
iPhone using a Windows computer, you must have access to a computer running OS X
(version 10.5.3, or later) to submit the application to the App Store. You can
get the Application Loader program from the Apple iOS Developer Center.

</div>

</div>

<div>

#### Creating an iOS package for ad hoc distribution

To create an iOS package for ad hoc distribution, use the ADT package command,
setting the target type to _ios-ad-hoc_. Before running this command, you must
have already obtained the appropriate ad hoc distribution code signing
certificate and provisioning profile from Apple.

    adt     -package
                                    -target ipa-ad-hoc
                                    -storetype pkcs12 -keystore ../AppleDistribution.p12
                                    -provisioning-profile AppleDistribution.mobileprofile
                                    myApp.ipa
                                    myApp-app.xml
                                    myApp.swf icons Default.png

Type the entire command on a single line; line breaks in the above example are
only present to make it easier to read. Also, the example assumes that the path
to the ADT tool is on your command-line shell’s path definition. (See
[Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html)
for help.)

You must run the command from the directory containing the application files.
The application files in the example are myApp-app.xml (the application
descriptor file), myApp.swf, an icons directory, and the Default.png file.

You must sign the application using the correct distribution certificate issued
by Apple; other code signing certificates cannot be used.

</div>

<div>

#### Creating an iOS package for an application that uses native extensions

To create an iOS package for an application that uses native extensions, use the
ADT package command with the `-extdir`option. Use the ADT command as appropriate
for the target (`ipa-app-store`, `ipa-debug`, `ipa-ad-hoc`, `ipa-test`). For
example:

    adt     -package
                                    -target ipa-ad-hoc
                                    -storetype pkcs12 -keystore ../AppleDistribution.p12
                                    -provisioning-profile AppleDistribution.mobileprofile
                                    myApp.ipa
                                    myApp-app.xml
                                    -extdir extensionsDir
                                    myApp.swf icons Default.png

Type the entire command on a single line; line breaks in the above example are
only present to make it easier to read.

Regarding native extensions, the example assumes that the directory named
`extensionsDir` is in the directory in which you run the command. The
`extensionsDir` directory contains the ANE files that the application uses.

</div>

<div>

#### To create an iOS/tvOS package with Assets.car

To create an iOS/tvOS package for submission to the Apple App store, use the ADT
package command, setting the target type to `ios-app-store`. Before running this
command, you must have already obtained a distribution code signing certificate
and provisioning profile from Apple, and have your `Assets.car` created using
Xcode ready. For example:

    adt     -package
                                    -target ipa-app-store
                                    -storetype pkcs12 -keystore ../AppleDistribution.p12
                                    -provisioning-profile AppleDistribution.mobileprofile
                                    myApp.ipa
                                    myApp-app.xml
                                    myApp.swf icons Default.png Assets.car

Type the entire command on a single line; line breaks in the above example are
only present to make it easier to read.

Also, the example assumes that the path to the ADT tool is on your command-line
shell's path definition (see
[Path environment variables](https://help.adobe.com/en_US/air/build/WSfffb011ac560372f-71994050128cca87097-8000.html)
for help). You must run the command from the directory containing the
application files. The application files in the example are `myApp-app xml`(the
application descriptor file), `myApp.swf`, icons directory, the `Default.png`
file and `Assets.car`.

</div>

</div>

<div>

<div>



</div>

</div>
