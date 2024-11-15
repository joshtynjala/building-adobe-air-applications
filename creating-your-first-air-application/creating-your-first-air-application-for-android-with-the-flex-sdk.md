# Creating your first AIR application for Android with the Flex SDK

To begin, you must have installed and set up the AIR and Flex SDKs. This
tutorial uses the _AMXMLC_ compiler from the Flex SDK and the _AIR Debug
Launcher_ (ADL), and the _AIR Developer Tool_ (ADT) from the AIR SDK. See
[Setting up the Flex SDK](WS2d8d13466044a733190f0432124114d9a19-8000.html).

You must also download and install the Android SDK from the Android website, as
described in:
[Android Developers: Installing the SDK](http://developer.android.com/sdk/installing.html).

> **Note:** For information on iPhone development, see
> [Creating a Hello World iPhone application with Flash Professional CS5](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/iphone/WS789ea67d3e73a8b2-240138de1243a7725e7-7ffc.html).

## Create the AIR application descriptor file

This section describes how to create the application descriptor, which is an XML
file with the following structure:

    <application xmlns="...">
        <id>...</id>
        <versionNumber>...</versionNumber>
        <filename>…</filename>
        <initialWindow>
            <content>…</content>
        </initialWindow>
        <supportedProfiles>...</supportedProfiles>
    </application>

1.  Create an XML file named `HelloWorld-app.xml` and save it in the project
    directory.

2.  Add the `<application>` element, including the AIR namespace attribute:

    **\<application xmlns="http://ns.adobe.com/air/application/2.7"\>** The last
    segment of the namespace, "2.7," specifies the version of the runtime
    required by the application.

3.  Add the `<id>` element:

    **\<id\>samples.android.HelloWorld\</id\>** The application ID uniquely
    identifies your application along with the publisher ID (which AIR derives
    from the certificate used to sign the application package). The recommended
    form is a dot-delimited, reverse-DNS-style string, such as
    `"com.company.AppName"`.

4.  Add the `<versionNumber>` element:

    **\<versionNumber\>0.0.1\</versionNumber\>** Helps users to determine which
    version of your application they are installing.

5.  Add the `<filename>` element:

    **\<filename\>HelloWorld\</filename\>** The name used for the application
    executable, install directory, and similar for references in the operating
    system.

6.  Add the `<initialWindow>` element containing the following child elements to
    specify the properties for your initial application window:

    **\<content\>HelloWorld.swf\</content\>** Identifies the root HTML file for
    AIR to load.

7.  Add the `<supportedProfiles>` element.

    **\<supportedProfiles\>mobileDevice\</supportedProfiles\>** Specifies that
    the application only runs in the mobile profile.

8.  Save the file. Your complete application descriptor file should look like
    this:

        <?xml version="1.0" encoding="UTF-8"?>
        <application xmlns="http://ns.adobe.com/air/application/2.7">
            <id>samples.android.HelloWorld</id>
            <versionNumber>0.0.1</versionNumber>
            <filename>HelloWorld</filename>
            <initialWindow>
                <content>HelloWorld.swf</content>
            </initialWindow>
            <supportedProfiles>mobileDevice</supportedProfiles>
        </application>

This example only sets a few of the possible application properties. There are
other settings that you can use in the application descriptor file. For example,
you can add \<fullScreen\>true\</fullScreen\> to the initialWindow element to
build a full-screen application. To enable remote debugging and
access-controlled features on Android, you also will have to add Android
permissions to the application descriptor. Permissions are not needed for this
simple application, so you do not need to add them now.

For more information, see
[Setting mobile application properties](WSfffb011ac560372f-5d0f4f25128cc9cd0cb-7ffe.html).

## Write the application code

Create a file named HelloWorld.as and add the following code using a text
editor:

    package
    {
        import flash.display.Sprite;
        import flash.text.TextField;

        public class HelloWorld extends Sprite
        {
            public function HelloWorld()
            {
                var textField:TextField = new TextField();
                textField.text = "Hello, World!";
                stage.addChild( textField );
            }
        }
    }

## Compile the application

Before you can run and debug the application, compile the MXML code into a SWF
file using the amxmlc compiler. The amxmlc compiler can be found in the `bin`
directory of the Flex SDK. If desired, you can set the path environment of your
computer to include the Flex SDK bin directory. Setting the path makes it easier
to run the utilities on the command line.

1.  Open a command shell or a terminal and navigate to the project folder of
    your AIR application.

2.  Enter the following command:

        amxmlc HelloWorld.as

Running `amxmlc` produces `HelloWorld.swf`, which contains the compiled code of
the application.

> **Note:** If the application does not compile, fix syntax or spelling errors.
> Errors and warnings are displayed in the console window used to run the amxmlc
> compiler.

For more information, see
[Compiling MXML and ActionScript source files for AIR](WS2d929364fa0b8137-4622b98b129dc3cff3f-7ffe.html).

## Test the application

To run and test the application from the command line, use the AIR Debug
Launcher (ADL) to launch the application using its application descriptor file.
(ADL can be found in the bin directory of the AIR and Flex SDKs.)

![](../img/dingbat.png) From the command prompt, enter the following command:

    adl HelloWorld-app.xml

For more information, see
[Device simulation using ADL](WSfffb011ac560372f-5d0f4f25128cc9cd0cb-7ff9.html).

## Create the APK package file

When your application runs successfully, you can use the ADT utility to package
the application into an APK package file. An APK package file is the native
Android application file format, which you can distribute to your users.

All Android applications must be signed. Unlike AIR files, it customary to sign
Android apps with a self-signed certificate. The Android operating system does
not attempt to establish the identity of the application developer. You can use
a certificate generated by ADT to sign Android packages. Certificates used for
apps submitted to the Android market must have a validity period of at least 25
years.

#### Generate a self-signed certificate and key pair

![](../img/dingbat.png) From the command prompt, enter the following command
(the ADT executable can be found in the `bin` directory of the Flex SDK):

    adt -certificate -validityPeriod 25 -cn SelfSigned 1024-RSA sampleCert.pfx samplePassword

This example uses the minimum number of attributes that can be set for a
certificate. The key type must be either _1024-RSA_ or _2048-RSA_ (see the
[ADT certificate command](WS901d38e593cd1bac1e63e3d128fc240122-7ffc.html)).

#### Create the AIR package

![](../img/dingbat.png) From the command prompt, enter the following command (on
a single line):

    adt -package -target apk -storetype pkcs12 -keystore sampleCert.p12 HelloWorld.apk HelloWorld-app.xml HelloWorld.swf

You will be prompted for the keystore file password. Type the password and press
Enter.

For more information, see
[Packaging a mobile AIR application](WSfffb011ac560372f-5d0f4f25128cc9cd0cb-7ffb.html).

#### Install the AIR runtime

You can install the latest version of the AIR runtime on your device from the
Android Market. You can also install the runtime included in your SDK on either
a device or an Android emulator.

![](../img/dingbat.png) From the command prompt, enter the following command (on
a single line):

    adt -installRuntime -platform android -platformsdk

Set the `-platformsdk` flag to your Android SDK directory (specify the parent of
the tools folder).

ADT installs the Runtime.apk included in the SDK.

For more information, see
[Install the AIR runtime and applications for development](WS2d929364fa0b81373f5793e012a24c349f8-7fff.html).

#### Install the AIR app

![](../img/dingbat.png) From the command prompt, enter the following command (on
a single line):

    adt -installApp -platform android -platformsdk path-to-android-sdk -package path-to-app

Set the `-platformsdk` flag to your Android SDK directory (specify the parent of
the tools folder).

For more information, see
[Install the AIR runtime and applications for development](WS2d929364fa0b81373f5793e012a24c349f8-7fff.html).

You can launch your app by tapping the application icon on the screen of the
device or emulator.
