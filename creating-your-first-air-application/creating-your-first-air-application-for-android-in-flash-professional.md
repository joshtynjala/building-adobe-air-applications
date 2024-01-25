# Create your first AIR application for Android in Flash Professional

<div>

To develop AIR applications for Android, you must download the Flash
Professional CS5 extension for Android from [Adobe Labs](http://labs.adobe.com).

You must also download and install the Android SDK from the Android web site, as
described in:
[Android Developers: Installing the SDK](http://developer.android.com/sdk/installing.html).

<div>

#### Create a project

1.  Open Flash Professional CS5

2.  Create a new AIR for Android project.

    The Flash Professional home screen includes a link to create an AIR for
    Android application. You can also select File \> New, and then select the
    AIR for Android template.

3.  Save the document as HelloWorld.fla

</div>

<div>

#### Write the code

Since this tutorial isn't really about writing code, just use the Text tool to
write, "Hello, World!" on the stage.

</div>

<div>

#### Set the application properties

1.  Select File \> AIR Android Settings.

2.  In the General tab, make the following settings:

    - Output File: HelloWorld.apk

    - App name: HelloWorld

    - App ID: HelloWorld

    - Version number: 0.0.1

    - Aspect ratio: Portrait

3.  On the Deployment tab, make the following settings:

    - Certificate: Point to a valid AIR code-signing certificate. You can click
      the Create button to create a new certificate. (Android apps deployed via
      the Android Marketplace must have certificates that are valid until at
      least 2033.) Enter the certificate password in the Password field.

    - Android deployment type: Debug

    - After Publish: Select both options

    - Enter the path to the ADB tool in the tools subdirectory of the Android
      SDK.

4.  Close the Android settings dialog by clicking OK.

    The app does not need icons or permissions at this stage in its development.
    Most AIR apps for Android do require some permissions in order to access
    protected features. You should only set those permissions your app truly
    requires since users may reject your app if it asks for too many
    permissions.

5.  Save the file.

</div>

<div>

#### Package and Install the application on the Android device

1.  Make sure that USB debugging is enabled on your device. You can turn USB
    debugging on in the Settings app under Applications \> Development.

2.  Connect your device to your computer with a USB cable.

3.  Install the AIR runtime, if you have not already done so, by going to the
    Android Market and downloading Adobe AIR. (You can also install AIR locally
    using the
    [ADT installRuntime command](WS901d38e593cd1bac1e63e3d128fc240122-7ff6.html).
    Android packages for use on Android devices and emulators are included in
    the AIR SDK.)

4.  Select File \> Publish.

    Flash Professional creates the APK file, installs the app on the connected
    Android device, and launches it.

</div>

</div>

<div>

<div>



</div>

</div>
