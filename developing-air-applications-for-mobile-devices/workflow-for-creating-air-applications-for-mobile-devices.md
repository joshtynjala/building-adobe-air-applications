# Workflow for creating AIR applications for mobile devices

<div>

The workflow for creating an AIR application for mobile (or other) devices is,
in general, very similar to that for creating a desktop application. The primary
workflow differences occur when it is time to package, debug, and install an
application. For example, AIR for Android apps use the native Android APK
package format rather than the AIR package format. Hence, they also use the
standard Android install and update mechanisms.

</div>

<div>

## AIR for Android

<div>

The following steps are typical when developing an AIR application for Android:

- Write the ActionScript or MXML code.

- Create an AIR application descriptor file (using the 2.5, or later,
  namespace).

- Compile the application.

- Package the application as an Android package (.apk).

- Install the AIR runtime on the device or Android emulator (if using an
  external runtime; captive runtime is the default in AIR 3.7 and higher).

- Install the application on device (or Android emulator).

- Launch the application on the device.

You can use Adobe Flash Builder, Adobe Flash Professional CS5, or the
command-line tools to accomplish these steps.

Once your AIR app is finished and packaged as an APK file, you can submit it to
the Android Market or distribute it through other means.

</div>

</div>

<div>

## AIR for iOS

<div>

The following steps are typical when developing AIR applications for iOS:

- Install iTunes.

- Generate the required developer files and IDs on the Apple iOS Provisioning
  Portal. These items include:

  - Developer certificate

  - App ID

  - Provisioning profile

  You must list the IDs of any test devices on which you plan to install the
  application when creating the provisioning profile.

- Convert the development certificate and private key to a P12 keystore file.

- Write the application ActionScript or MXML code.

- Compile the application with an ActionScript or MXML compiler.

- Create icon art and initial screen art for the application.

- Create the application descriptor (using the 2.6, or greater, namespace).

- Package the IPA file using ADT.

- Use iTunes to place your provisioning profile on your test device.

- Install and test the application on your iOS device. You can use either iTunes
  or ADT over USB (USB support in AIR 3.4 and above) to install the IPA file.

Once your AIR app is finished, you can repackage it using a distribution
certificate and provisioning profile. It is then ready to submit to the Apple
App Store.

</div>

</div>

<div>

<div>



</div>

</div>
