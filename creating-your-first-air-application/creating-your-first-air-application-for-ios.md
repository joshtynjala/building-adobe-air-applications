# Creating your first AIR application for iOS

You can code, build, and test the basic features of an iOS application using
only Adobe tools. However, to install an iOS application on a device and to
distribute that application, you must join the Apple iOS Developer program
(which is a fee-based service). Once you join the iOS Developer program you can
access the iOS Provisioning Portal where you can obtain the following items and
files from Apple that are required to install an application on a device for
testing and for subsequent distribution. These items and files include:

- Development and distribution certificates

- Application IDs

- Development and distribution provisioning files

## Create the application content

Create a SWF file that displays the text, "Hello world!" You can perform this
task using Flash Professional, Flash Builder, or another IDE. This example
simply uses a text editor and the command line SWF compiler included in the Flex
SDK.

1.  Create a directory in a convenient location to store your application files.
    Create a file named, _HelloWorld.as_ and edit the file in your favorite code
    editor.

2.  Add the following code:

        package{

            import flash.display.Sprite;
            import flash.text.TextField;
            import flash.text.TextFormat;
            import flash.text.TextFieldAutoSize;

            public class HelloWorld extends Sprite
            {
                public function HelloWorld():void
                {
                    var textField:TextField = new TextField();
                    textField.text = "Hello World!";
                    textField.autoSize = TextFieldAutoSize.LEFT;

                    var format:TextFormat = new TextFormat();
                    format.size = 48;

                    textField.setTextFormat ( format );
                    this.addChild( textField );
                }
            }
        }

3.  Compile the class using the amxmlc compiler:

        amxmlc HelloWorld.as

    A SWF file, _HelloWorld.swf_, is created in the same folder.

    Note: This example assumes that you have set up your environment path
    variable to include the directory containing amxmlc. For information on
    setting the path, see
    [Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html).
    Alternately, you can type the full path to amxmlc and the other command-line
    tools used in this example.

## Create icon art and initial screen art for the application

All iOS applications have icons that appear in the user interface of the iTunes
application and on the device screen.

1.  Create a directory within your project directory, and name it icons.

2.  Create three PNG files in the icons directory. Name them Icon_29.png,
    Icon_57.png, and Icon_512.png.

3.  Edit the PNG files to create appropriate art for your application. The files
    must be 29-by-29 pixels, 57-by-57 pixels, and 512-by-512 pixels. For this
    test, you can simply use solid color squares as the art.

    Note: When you submit an application to the Apple App Store, you use a JPG
    version (not a PNG version) of the 512-pixel file. You use the PNG version
    while testing development versions of an application.

All iPhone applications display an initial image while the application loads on
the iPhone. You define the initial image in a PNG file:

1.  In the main development directory, create a PNG file named Default.png. (Do
    _not_ put this file in the icons subdirectory. Be sure to name the file
    Default.png, with an uppercase D.)

2.  Edit the file so that it is 320 pixels wide and 480 pixels high. For now,
    the content can be a plain white rectangle. (You will change this later.)

For detailed information on these graphics, see
[Application icons](WS901d38e593cd1bac1e63e3d129907d2886-8000.html).

## Create the application descriptor file

Create an application descriptor file that specifies the basic properties for
the application. You can complete this task using an IDE such as Flash Builder
or a text editor.

1.  In the project folder that contains HelloWorld.as, create an XML file named,
    _HelloWorld-app.xml_. Edit this file in your favorite XML editor.

2.  Add the following XML:

        <?xml version="1.0" encoding="utf-8" ?>
        <application xmlns="http://ns.adobe.com/air/application/2.7" minimumPatchLevel="0">
            <id>change_to_your_id</id>
            <name>Hello World iOS</name>
            <versionNumber>0.0.1</versionNumber>
            <filename>HelloWorld</filename>
            <supportedProfiles>mobileDevice</supportedProfiles>
            <initialWindow>
                <content>HelloWorld.swf</content>
                <title>Hello World!</title>
            </initialWindow>
            <icon>
                <image29x29>icons/AIRApp_29.png</image29x29>
                <image57x57>icons/AIRApp_57.png</image57x57>
                <image512x512>icons/AIRApp_512.png</image512x512>
            </icon>
        </application>

    For the sake of simplicity, this example only sets a few of the available
    properties.

    Note: If you are using AIR 2, or earlier, you must use the `<version>`
    element instead of the `<versionNumber>` element.

3.  Change the application ID to match the application ID specified in the iOS
    Provisioning Portal. (Do not include the random bundle seed portion at the
    beginning of the ID.

4.  Test the application using ADL:

        adl HelloWorld-app.xml -screensize iPhone

    ADL should open a window on your desktop that displays the text: _Hello
    World!_ If it does not, check the source code and application descriptor for
    errors.

## Compile the IPA file

You can now compile the IPA installer file using ADT. You must have your Apple
certificate and private key in P12 file format and your Apple development
provisioning profile.Here is a summary of how certificates and provisioning
profile provided by Apple are to be utilized for packaging.

- Distribution Certificate and Distribution provisioning profile are to be used
  to package the application for App Store upload. Application packaged is to be
  used solely for App Store upload. Installing such an application directly on
  the device would give error.

- Distribution Certificate and Ad hoc provisioning profile are to be used to
  package the application for beta testing the application on the devices.

- Development Certificate and Development provisioning profile are to be used to
  package the application for debugging and testing the application on device.

Run the ADT utility with the following options, replacing the keystore,
storepass, and provisioning-profile values with your own:

    adt -package -target ipa-debug
        -keystore iosPrivateKey.p12 -storetype pkcs12 -storepass qwerty12
        -provisioning-profile ios.mobileprovision
        HelloWorld.ipa
        HelloWorld-app.xml
        HelloWorld.swf icons Default.png

(Use a single command line; the line breaks in this example are just added to
make it easier to read.)

ADT generates the iOS application installer file, _HelloWorld.ipa_, in the
project directory. Compiling the IPA file can take a few minutes.

## Install the application on a device

To install the iOS application for testing:

1.  Open the iTunes application.

2.  If you have not already done so, add the provisioning profile for this
    application to iTunes. In iTunes, select File \> Add To Library. Then,
    select the provisioning profile file (which has mobileprovision as the file
    type).

    For now, to test the application on your developer device, use the
    development provisioning profile.

    Later, when distributing an application to the iTunes Store, use the
    distribution profile. To distribute the application ad-hoc (to multiple
    devices without going through the iTunes Store), use the ad-hoc provisioning
    profile.

    For more information on provisioning profiles, see
    [iOS setup](WSfffb011ac560372f46768d8712cd1d13954-8000.html).

3.  Some versions of iTunes do not replace the application if the same version
    of the application is already installed. In this case, delete the
    application from your device and from the list of applications in iTunes.

4.  Double-click the IPA file for your application. It should appear in the list
    of applications in iTunes.

5.  Connect your device to the USB port on your computer.

6.  In iTunes, check the Application tab for the device, and ensure that the
    application is selected in the list of applications to be installed.

7.  Select the device in the left-hand list of the iTunes application. Then
    click the Sync button. When the sync completes, the Hello World application
    appears on your iPhone.

If the new version is not installed, delete it from your device and from the
list of applications in iTunes, and then redo this procedure. This may be the
case if the currently installed version uses the same application ID and
version.

## Edit the initial screen graphic

Before you compiled your application, you created a Default.png file (see
[Create icon art and initial screen art for the application](WSfffb011ac560372f3cb56e2a12cc36970aa-7ffe.html)).
This PNG file serves as the startup image while the application loads. When you
tested the application on your iPhone, you may have noticed this blank screen at
startup.

You should change this image to match the startup screen of your application
("Hello World!"):

1.  Open your application on your device. When the first "Hello World" text
    appears, press and hold the Home button (below the screen). While holding
    the Home button, press the Power/Sleep button (at the top of the iPhone).
    This takes a screenshot and sends it to the Camera Roll.

2.  Transfer the image to your development computer by transferring photos from
    iPhoto or another photo transfer application. (On Mac OS, you can also use
    the Image Capture application.)

    You can also e-mail the photo to your development computer:

    - Open the Photos application.

    - Open the Camera Roll.

    - Open the screenshot image you captured.

    - Tap the image and then tap the "forward" (arrow) button in the
      bottom-left-hand corner. Then click the Email Photo button and send the
      image to yourself.

3.  Replace the Default.png file (in your development directory) with a PNG
    version of the screen capture image.

4.  Recompile the application (see
    [Compile the IPA file](WSfffb011ac560372f3cb56e2a12cc36970aa-7ffc.html)) and
    reinstall it on your device.

The application now uses the new startup screen as it loads.

Note: You can create any art you'd like for the Default.png file, as long as it
is the correct dimensions (320 by 480 pixels). However, it is often best to have
the Default.png image match the initial state of your application.
