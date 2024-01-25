# Packaging an AIR for TV application

## Packaging with ADT

You can use the AIR ADT command-line tool to package an AIR for TV application.
Starting with the AIR SDK version 2.5, ADT supports packaging for TV devices.
Before packaging, compile all your ActionScript and MXML code. You must also
have a code signing certificate. You can create a certificate using the ADT
-certificate command.

For a detailed reference on ADT commands and options, see
[AIR Developer Tool (ADT)](WS5b3ccc516d4fbf351e63e3d118666ade46-7fd9.html).

#### Creating an AIR package

To create an AIR package, use the ADT package command:

    adt -package -storetype pkcs12 -keystore ../codesign.p12 myApp.air myApp-app.xml myApp.swf icons

The example assumes that:

- The path to the ADT tool is on your command-line shell's path definition. (See
  [Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html).)

- The certificate codesign.p12 is in the parent directory from where you are
  running the ADT command.

Run the command from the directory containing the application files. The
application files in the example are myApp-app.xml (the application descriptor
file), myApp.swf, and an icons directory.

When you run the command as shown, ADT prompts you for the keystore password.
Not all shell programs display the password characters you type; just press
Enter when you are done typing. Alternatively, you can use the `storepass`
parameter to include the password in the ADT command.

#### Creating an AIRN package

If your AIR for TV application uses a native extension, create an AIRN package
instead of an AIR package. To create an AIRN package, use the ADT package
command, setting the target type to `airn`.

    adt -package -storetype pkcs12 -keystore ../codesign.p12 -target airn myApp.airn myApp-app.xml myApp.swf icons -extdir C:\extensions

The example assumes that:

- The path to the ADT tool is on your command-line shell's path definition. (See
  [Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html).)

- The certificate codesign.p12 is in the parent directory from where you are
  running the ADT command.

- The parameter `-extdir` names a directory that contains the ANE files that the
  application uses.

  These ANE files contain an ActionScript-only stub or simulator version of the
  extension. The version of the extension that contains the native code is
  installed on the AIR for TV device.

Run the command from the directory containing the application files. The
application files in the example are myApp-app.xml (the application descriptor
file), myApp.swf, and an icons directory.

When you run the command as shown, ADT prompts you for the keystore password.
Not all shell programs display the password characters you type; just press
Enter when you are done typing. Alternatively, you can use the `storepass`
parameter to include the password in the command.

You can also create an AIRI file for an AIR for TV application that uses native
extensions. The AIRI file is just like the AIRN file, except it is not signed.
For example:

    adt -prepare myApp.airi myApp.xml myApp.swf icons -extdir C:\extensions

You can then create an AIRN file from the AIRI file when you are ready to sign
the application:

    adt -package -storetype pkcs12 -keystore ../codesign.p12 -target airn myApp.airn myApp.airi

For more information, see
[Developing Native Extensions for Adobe AIR](https://web.archive.org/web/20150414032840/https://help.adobe.com/en_US/air/extensions/index.html).

## Packaging with Flash Builder or Flash Professional

Flash Professional and Flash Builder allow you to publish or export the AIR
packages without having to run ADT yourself. The procedure for creating an AIR
package for an AIR application is covered in the documentation for these
programs.

Currently, however, only ADT can create AIRN packages, the application packages
for AIR for TV applications that use native extensions.

For more information, see the following:

- [Package AIR applications with Flash Builder](http://www.adobe.com/go/learn_dev_AIR_Flash_Builder_en)

- [Publishing for Adobe AIR using Flash Professional](http://www.adobe.com/go/learn_publish_AIR_Flash_Pro_en)
