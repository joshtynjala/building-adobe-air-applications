# Use push notifications

Push notifications let remote notification providers send notifications to
applications running on a mobile device. AIR 3.4 supports push notifications for
iOS devices using the Apple Push Notification service (APNs).

Note: To enable push notifications for an AIR for Android application, use a
native extension, such as
[as3c2dm](https://web.archive.org/web/20120112184645/http://www.riaspace.com/2011/09/as3c2dm-air-native-extension-to-push-notifications-with-c2dm/),
developed by Adobe evangelist Piotr Walczyszyn.

The remainder of this section describes how to enable push notifications in AIR
for iOS applications.

Note: This discussion assumes that you have an Apple developer ID, are familiar
with the iOS development workflow,and have deployed at least one application on
an iOS device.

## Overview of push notifications

The Apple Push Notification service (APNs) lets remote notification providers
send notifications to applications running on iOS devices. APNs supports the
following notification types:

- Alerts

- Badges

- Sounds

For complete information on APNs, see
[developer.apple.com](http://developer.apple.com/library/mac/#documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/ApplePushService/ApplePushService.html).

Using push notifications in your application involves multiple aspects:

- **Client application** - Registers for push notifications, communicates with
  the remote notification providers, and receives push notifications.

- **iOS** - Manages interaction between the client application and APNs.

- **APNs** - Provides a tokenID during client registration and passes
  notifications from the remote notification providers to iOS.

- **Remote notification provider** - Stores tokenId-client application
  information and pushes notifications to APNs.

### Regstration workflow

The workflow for registering push notifications with a server-side service is as
follows:

1.  The client application requests that iOS enable push notifications.

2.  iOS forwards the request to APNs.

3.  The APNs server returns a tokenId to iOS.

4.  iOS returns the tokenId to the client application.

5.  The client application (using an application-specific mechanism) provides
    the tokenId to the remote notification provider, which stores the tokenId to
    use for push notifications.

### Notification workflow

The notification workflow is as follows:

1.  The remote notification provider generates a notification and passes the
    notification payload to APNs, along with the tokenId.

2.  APNs forwards the notification to iOS on the device.

3.  iOS pushes the notification payload to the application.

### Push notification API

AIR 3.4 introduced a set of APIs that support iOS push notifications. These APIs
are in the `flash.notifications` package, and inlude the following classes:

- [`NotificationStyle`](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/notifications/NotificationStyle.html) -
  Defines constants for notification types: `ALERT`, `BADGE`, and `SOUND`.C

- [`RemoteNotifier`](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/notifications/RemoteNotifier.html) -
  Lets you subscribe to and unsubscribe from push notifications.

- [`RemoteNotifierSubscribeOptions`](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/notifications/RemoteNotifierSubscribeOptions.html) -
  Lets you select which notification types to receive. Use the
  `notificationStyles` property to define a vector of strings that register for
  multiple notification types.

AIR 3.4 also includes `flash.events.RemoteNotificationEvent`, which is
dispatched by `RemoteNotifier`, as follows:

- When an application's subscription is successfully created and a new tokenId
  is received from APNs.

- Upon receiving a new remote notification.

Additionally, `RemoteNotifier` dispatches `flash.events.StatusEvent` if it
encounters an error during the subscription process.

## Manage push notifications in an application

To register your application for push notifications, you must perform the
following steps:

- Create code that subscribes to push notifications in your application.

- Enable push notifications in the application XML file.

- Create a provisioning profile and certificate that enable iOS Push Services.

The following annotated sample code subscribes to push notification and handles
push notification events:

    package
                            {
                            import flash.display.Sprite;
                            import flash.display.StageAlign;
                            import flash.display.StageScaleMode;
                            import flash.events.*;
                            import flash.events.Event;
                            import flash.events.IOErrorEvent;
                            import flash.events.MouseEvent;
                            import flash.net.*;
                            import flash.text.TextField;
                            import flash.text.TextFormat;
                            import flash.ui.Multitouch;
                            import flash.ui.MultitouchInputMode;
                            // Required packages for push notifications
                            import flash.notifications.NotificationStyle;
                            import flash.notifications.RemoteNotifier;
                            import flash.notifications.RemoteNotifierSubscribeOptions;
                            import flash.events.RemoteNotificationEvent;
                            import flash.events.StatusEvent;
                            [SWF(width="1280", height="752", frameRate="60")]

                            public class TestPushNotifications extends Sprite
                            {
                            private var notiStyles:Vector.<String> = new Vector.<String>;;
                            private var tt:TextField = new TextField();
                            private var tf:TextFormat = new TextFormat();
                            // Contains the notification styles that your app wants to receive
                            private var preferredStyles:Vector.<String> = new Vector.<String>();
                            private var subscribeOptions:RemoteNotifierSubscribeOptions = new RemoteNotifierSubscribeOptions();
                            private var remoteNot:RemoteNotifier = new RemoteNotifier();

                            private var subsButton:CustomButton = new CustomButton("Subscribe");
                            private var unSubsButton:CustomButton = new CustomButton("UnSubscribe");
                            private var clearButton:CustomButton = new CustomButton("clearText");

                            private var urlreq:URLRequest;
                            private var urlLoad:URLLoader = new URLLoader();
                            private var urlString:String;

                            public function TestPushNotifications()
                            {
                            super();

                            Multitouch.inputMode = MultitouchInputMode.TOUCH_POINT;
                            stage.align = StageAlign.TOP_LEFT;
                            stage.scaleMode = StageScaleMode.NO_SCALE;

                            tf.size = 20;
                            tf.bold = true;


                            tt.x=0;
                            tt.y =150;
                            tt.height = stage.stageHeight;
                            tt.width = stage.stageWidth;
                            tt.border = true;
                            tt.defaultTextFormat = tf;

                            addChild(tt);

                            subsButton.x = 150;
                            subsButton.y=10;
                            subsButton.addEventListener(MouseEvent.CLICK,subsButtonHandler);
                            stage.addChild(subsButton);

                            unSubsButton.x = 300;
                            unSubsButton.y=10;
                            unSubsButton.addEventListener(MouseEvent.CLICK,unSubsButtonHandler);
                            stage.addChild(unSubsButton);

                            clearButton.x = 450;
                            clearButton.y=10;
                            clearButton.addEventListener(MouseEvent.CLICK,clearButtonHandler);
                            stage.addChild(clearButton);

                            //
                            tt.text += "\n SupportedNotification Styles: " + RemoteNotifier.supportedNotificationStyles.toString() + "\n";

                            tt.text += "\n Before Preferred notificationStyles: " + subscribeOptions.notificationStyles.toString() + "\n";

                            // Subscribe to all three styles of push notifications:
                            // ALERT, BADGE, and SOUND.
                            preferredStyles.push(NotificationStyle.ALERT ,NotificationStyle.BADGE,NotificationStyle.SOUND );

                            subscribeOptions.notificationStyles= preferredStyles;

                            tt.text += "\n After Preferred notificationStyles:" + subscribeOptions.notificationStyles.toString() + "\n";


                            remoteNot.addEventListener(RemoteNotificationEvent.TOKEN,tokenHandler);
                            remoteNot.addEventListener(RemoteNotificationEvent.NOTIFICATION,notificationHandler);
                            remoteNot.addEventListener(StatusEvent.STATUS,statusHandler);

                            this.stage.addEventListener(Event.ACTIVATE,activateHandler);


                            }
                            // Apple recommends that each time an app activates, it subscribe for
                            // push notifications.
                            public function activateHandler(e:Event):void{
                            // Before subscribing to push notifications, ensure the device supports it.
                            // supportedNotificationStyles returns the types of notifications
                            // that the OS platform supports
                            if(RemoteNotifier.supportedNotificationStyles.toString() != "")
                            {
                            remoteNot.subscribe(subscribeOptions);
                            }
                            else{
                            tt.appendText("\n Remote Notifications not supported on this Platform !");
                            }
                            }
                            public function subsButtonHandler(e:MouseEvent):void{
                            remoteNot.subscribe(subscribeOptions);
                            }
                            // Optionally unsubscribe from push notfications at runtime.
                            public function unSubsButtonHandler(e:MouseEvent):void{
                            remoteNot.unsubscribe();
                            tt.text +="\n UNSUBSCRIBED";
                            }

                            public function clearButtonHandler(e:MouseEvent):void{
                            tt.text = " ";
                            }
                            // Receive notification payload data and use it in your app
                            public function notificationHandler(e:RemoteNotificationEvent):void{
                            tt.appendText("\nRemoteNotificationEvent type: " + e.type +
                            "\nbubbles: "+ e.bubbles + "\ncancelable " +e.cancelable);

                            for (var x:String in e.data) {
                            tt.text += "\n"+ x + ":  " + e.data[x];
                            }
                            }
                            // If the subscribe() request succeeds, a RemoteNotificationEvent of
                            // type TOKEN is received, from which you retrieve e.tokenId,
                            // which you use to register with the server provider (urbanairship, in
                            // this example.
                            public function tokenHandler(e:RemoteNotificationEvent):void
                            {
                            tt.appendText("\nRemoteNotificationEvent type: "+e.type +"\nBubbles: "+ e.bubbles + "\ncancelable " +e.cancelable +"\ntokenID:\n"+ e.tokenId +"\n");

                            urlString = new String("https://go.urbanairship.com/api/device_tokens/" +
                            e.tokenId);
                            urlreq = new URLRequest(urlString);

                            urlreq.authenticate = true;
                            urlreq.method = URLRequestMethod.PUT;

                            URLRequestDefaults.setLoginCredentialsForHost
                            ("go.urbanairship.com",
                            "1ssB2iV_RL6_UBLiYMQVfg","t-kZlzXGQ6-yU8T3iHiSyQ");

                            urlLoad.load(urlreq);
                            urlLoad.addEventListener(IOErrorEvent.IO_ERROR,iohandler);
                            urlLoad.addEventListener(Event.COMPLETE,compHandler);
                            urlLoad.addEventListener(HTTPStatusEvent.HTTP_STATUS,httpHandler);

                            }

                            private function iohandler(e:IOErrorEvent):void
                            {
                            tt.appendText("\n In IOError handler" + e.errorID +" " +e.type);

                            }
                            private function compHandler(e:Event):void{
                            tt.appendText("\n In Complete handler,"+"status: " +e.type + "\n");
                            }

                            private function httpHandler(e:HTTPStatusEvent):void{
                            tt.appendText("\n in httpstatus handler,"+ "Status: " + e.status);
                            }

                            // If the subscription request fails, StatusEvent is dispatched with
                            // error level and code.
                            public function statusHandler(e:StatusEvent):void{
                            tt.appendText("\n statusHandler");
                            tt.appendText("event Level" + e.level +"\nevent code " +
                            e.code + "\ne.currentTarget: " + e.currentTarget.toString());
                            }
                            }
                            }

### Enable push notifications in the application XML file

To use push notifications in your application, provide the following in the
`Entitlements` tag (under the `iphone` tag):

    <iphone>
                                ...
                                   <Entitlements>
                                      <![CDATA[
                                         <key>aps-environment</key>
                                         <string>development</string>
                                      ]]>
                                   </Entitlements>
                                </iphone>

When you are ready to push the application to the App Store, a `<string>`
element for development to production:

          <string>production</string>

If your application supports localized strings, specify the languages in the
`supportedLanguages` tag, beneath the `intialWindow` tag, as the following
example shows:

    <supportedLanguages>en de cs es fr it ja ko nl pl pt</supportedLanguages>

### Create a provisioning profile and certificate that enable iOS Push Services

To enable application-APNs communication, you must package the application with
a provisioning profile and certificate that enable iOS Push Services, as
follows:

1.  Log in to your Apple developer account.

2.  Navigate to the Provisioning Portal.

3.  Click the App IDs tab.

4.  Click the New App ID button.

5.  Specify a description and bundle identifier (you should not use \* in the
    bundle identifier).

6.  Click Submit. The Provisioning Portal generates your App ID and redisplays
    the App IDs page.

7.  Clik Configure (to the right of your App ID). The Configure App ID page
    displays.

8.  Select the Enable for Apple Push Notification service checkbox. Note that
    there are twotypes of push SSL certificates: one for development/testing and
    one for production.

9.  Click the Configure button to the right of Development Push SSL Certificate.
    The Generate Certificate Signing Request (CSR) page displays.

10. Generate a CSR using the Keychain Access utility, as instructed by the page.

11. Generate the SSL certificate.

12. Download and install the SSL certificate.

13. (Optional) Repeat steps 9 through 12 for the production Push SSL
    certificate.

14. Click Done. The Configure App ID page displays.

15. Click Done. The App IDs page displays. Notice the green circle beside Push
    Notification for your App ID.

16. Be sure to save your SSL certificates, as they are used later for
    application and provider communication.

17. Click the Provisioning tab todisplay the Provisioning Profiles page.

18. Create a provisioning profile for your new App ID and download it.

19. Click the Certificates tab and download a new certificate for the new
    provisioning profile.

### Use sound for push notifications

To enable sound notifications for your application, bundle the sound files as
you would any other asset, but in same directory as the SWF and app-xml files.
For example:

    Build/adt -package -target ipa-app-store -provisioning-profile _-_.mobileprovision -storetype pkcs12 -keystore _-_.p12 test.ipa test-app.xml test.swf sound.caf sound1.caf

Apple supports the following sound data formats (in aiff, wav, or caf files):

- Linear PCM

- MA4 (IMA/ADPCM)

- uLaw

- aLaw

### Use localized alert notifications

To use localized alert notifications in your application, bundle localized
strings in the form of lproj folders. For example, you support alerts in
Spanish, as follows:

1.  Create an es.lproj folder within the project at the same level as the
    app-xml file.

2.  Within the es.lproj folder, create a text file named Localizable.Strings.

3.  Open Localizable.Strings in a text editor and add message keys and the
    corresponding localized strings. For example:

        "PokeMessageFormat" = "La notificación de alertas en español."

4.  Save the file.

5.  When the application receives an alert notification with this key value and
    the device language is Spanish, the translated alert text displays.

## Configure a remote notification provider

You need a remote notification provider to send push notifications to your
application. This server application acts as a provider, accepting your push
input, and passing the notification and notification data to APNs, which, in
turn, sends the push notification to a client application.

For detailed information on pushing notifications from a remote notification
provider, see
[Provider Communication with Apple Push Notification Service](http://developer.apple.com/library/mac/#documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CommunicatingWIthAPS/CommunicatingWIthAPS.html#//apple_ref/doc/uid/TP40008194-CH101-SW1)
in the Apple Developer Library.

### Remote notification provider options

Options for a remote notification provider include the following:

- Create your own provider, based on the APNS-php open-source server. You can
  set up a PHP server using <http://code.google.com/p/apns-php/>. This Google
  Code project lets you design an interface that matches your specific
  requirements.

- Use a service provider. For example, <http://urbanairship.com/> offers a
  readymade APNs provider. After registering with this service, you start by
  providing your device token using code similar to the following:

      private var urlreq:URLRequest;
                                          private var urlLoad:URLLoader = new URLLoader();
                                          private var urlString:String;

                                          //When subscription is successful then only call the following code
                                          urlString = new String("https://go.urbanairship.com/api/device_tokens/" + e.tokenId);
                                          urlreq = new URLRequest(urlString);

                                          urlreq.authenticate = true;
                                          urlreq.method = URLRequestMethod.PUT;
                                          URLRequestDefaults.setLoginCredentialsForHost("go.urbanairship.com",
                                             "Application Key","Application Secret");
                                          urlLoad.load(urlreq);
                                          urlLoad.addEventListener(IOErrorEvent.IO_ERROR,iohandler);
                                          urlLoad.addEventListener(Event.COMPLETE,compHandler);
                                          urlLoad.addEventListener(HTTPStatusEvent.HTTP_STATUS,httpHandler);

                                          private function iohandler(e:IOErrorEvent):void{
                                             trace("\n In IOError handler" + e.errorID +" " +e.type);
                                          }

                                          private function compHandler(e:Event):void{
                                             trace("\n In Complete handler,"+"status: " +e.type + "\n");
                                          }

                                          private function httpHandler(e:HTTPStatusEvent):void{
                                             tt.appendText("\n in httpstatus handler,"+ "Status: " + e.status);
                                          }

  You can then send test notifications using Urban Airship tools.

### Certificates for the remote notification provider

You must copy the SSL certificate and private key (generated earlier )to the
appropriate location on the remote notification provider's server. You typically
combine these two files into a single `.pem` file. To do this, perform the
following steps:

1.  Open a terminal window.

2.  Create a `.pem` file from the SSL certificate by typing the following
    command:

        openssl x509 -in aps_developer_identity.cer -inform der -out TestPushDev.pem

3.  Create a .pem file of the private key (`.p12`) file by typing the following
    command:

        openssl pkcs12 -nocerts -out TestPushPrivateKey.pem -in certificates.p12

4.  Combine the two .pem files into a single file by typing the following
    command:

        cat TestPushDev.pem TestPushPrivateKey.pem > FinalTestPush.pem

5.  Provide the combined `.pem` file to the server provider when creating your
    server-side push application.

For more information, see
[Installing the SSL Certificate and Key on the Server](http://developer.apple.com/library/mac/#documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/ProvisioningDevelopment/ProvisioningDevelopment.html#//apple_ref/doc/uid/TP40008194-CH104-SW6)
in the Apple Local and Push Notification Programming Guide.

## Handle push notifications in an application

Handling push notifications in an application involves the following:

- Global user configuration and acceptance of push notifications

- User acceptance of individual push notifications

- Handling push notifications and notification payload data

### Configuration and acceptance of push notifications

The first time a user launches a push notification-enabled application, iOS
displays an **_appname_ Would Like to Send You Push Notifications** dialog with
Don't Allow and OK buttons. If the user selects OK, the application can receive
all styles of notifications for which it has subscribed. If the user selects
Don't Allow, it receives no notifications.

Note: Users can also go to Settings \> Notifications to control the specific
notification types it can receive for each push-enabled application.

Apples recommends that each time an application activates it should subscribe
for push notifications. When your application calls
`RemoteNotifier.subscribe()`, it receives a `RemoteNotificationEvent` of type
`token`, , which contains a 32-byte unique numeric tokenId that uniquely
identifies that application on that device.

When the device receives a push notification, it displays a popup with Close and
Launch buttons. If the user touches Close, nothing happens; if the user touches
Launch, iOS invokes the application and the application receives a
`flash.events.RemoteNotificationEvent` of type `notification`, as described
below.

### Handling push notifications and payload data

When the remote notification provider sends a notification to a device (using
the tokenID), your application receives a `flash.events.RemoteNotificationEvent`
of type `notification`, regardless of whether or not the application is running.
At this point, your application performs app-specific notification processing.
If your application handles notification data, you access it through the
JSON-formatted `RemoteNotificationEvent.data` property.
