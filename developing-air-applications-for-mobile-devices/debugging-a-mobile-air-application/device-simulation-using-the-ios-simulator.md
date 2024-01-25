# Device simulation using the iOS Simulator

The iOS Simulator (Mac-only) offers a fast way to run and debug iOS
applications. When testing with the iOS simulator, you do not need a developer
certificate or a provisioning profile. You must still create a p12 certificate,
although it can be self-signed.

By default ADT always launches the iPhone simulator. To change the simulator
device, do the following:

- Use the command below to view the available simulators.

      xcrun simctl list devices

  The output appears similar to the one shown below.

                              == Devices ==
                              -iOS 10.0 –
                              iPhone 5 (F6378129-A67E-41EA-AAF9-D99810F6BCE8) (Shutdown)
                              iPhone 5s (5F640166-4110-4F6B-AC18-47BC61A47749) (Shutdown)
                              iPhone 6 (E2ED9D38-C73E-4FF2-A7DD-70C55A021000) (Shutdown)
                              iPhone 6 Plus (B4DE58C7-80EB-4454-909A-C38C4106C01B) (Shutdown)
                              iPhone 6s (9662CB8A-2E88-403E-AE50-01FB49E4662B) (Shutdown)
                              iPhone 6s Plus (BED503F3-E70C-47E1-BE1C-A2B7F6B7B63E) (Shutdown)
                              iPhone 7 (71880D88-74C5-4637-AC58-1F9DB43BA471) (Shutdown)
                              iPhone 7 Plus (2F411EA1-EE8B-486B-B495-EFC421E0A494) (Shutdown)
                              iPhone SE (DF52B451-ACA2-47FD-84D9-292707F9F0E3) (Shutdown)
                              iPad Retina (C4EF8741-3982-481F-87D4-700ACD0DA6E1) (Shutdown)
                              ....

- You can choose a specific simulator by setting the environment variable
  `AIR_IOS_SIMULATOR_DEVICE`, as follows:

      export AIR_IOS_SIMULATOR_DEVICE = 'iPad Retina'

Restart the process after setting the environment variable and run the
application on the simulator device of your choice.

Note: When using ADT with the iOS Simulator, you must always include the
`‑platformsdk` option, specifying the path to the iOS Simulator SDK.

To run an application in the iOS Simulator:

1.  Use the adt -package command with either
    `-target ipa-test-interpreter-simulator` or
    `-target ipa-debug-interpreter-simulator`, as the following example shows:

        adt     -package
                                        -target ipa-test-interpreter-simulator
                                        -storetype pkcs12 -keystore Certificates.p12
                                        -storepass password
                                        myApp.ipa
                                        myApp-app.xml
                                        myApp.swf
                                        -platformsdk /Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator5.0.sdk

    Note: Signing options are no longer required in case of simulators now, so
    any value can be provided in `-keystore` flag as it will not be honored by
    ADT.

2.  Use the adt ‑installApp command to install the application in the iOS
    Simulator, as the following example shows:

        adt     -installApp
                                        -platform ios
                                        -platformsdk /Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator5.0.sdk
                                        -device ios-simulator
                                        -package sample_ipa_name.ipa

3.  Use the adt ‑launchApp command to run the application in the iOS Simulator,
    as the following example shows:

    Note: By default, the command `adt -launchApp` runs the application in the
    iPhone simulator. To run the application in the iPad simulator, export the
    environment variable, `AIR_IOS_SIMULATOR_DEVICE` = "iPad" and then use the
    command `adt -launchApp`.

        adt     -launchApp
                                        -platform ios
                                        -platformsdk /Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator5.0.sdk
                                        -device ios-simulator
                                        -appid sample_ipa_name

To test a native extension in the iOS Simulator, use the `iPhone-x86` platform
name in the extension.xml file and specify `library.a` (static library) in the
`nativeLibrary` element, as the following extension.xml example shows:

    <extension xmlns="http://ns.adobe.com/air/extension/3.1">
                              <id>com.cnative.extensions</id>
                              <versionNumber>1</versionNumber>
                              <platforms>
                                <platform name="iPhone-x86">
                                  <applicationDeployment>
                                    <nativeLibrary>library.a</nativeLibrary>
                                    <initializer>TestNativeExtensionsInitializer </initializer>
                                    <finalizer>TestNativeExtensionsFinalizer </finalizer>
                                  </applicationDeployment>
                                </platform>
                              </platforms>
                            </extension>

Note: When testing a native extension in the iOS Simulator, do not use the
static library (`.a` file) that is compiled for the device. Instead, be sure to
use the static library that is compiled for the simulator.
