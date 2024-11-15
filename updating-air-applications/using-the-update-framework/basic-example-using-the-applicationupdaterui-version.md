# Basic example: Using the ApplicationUpdaterUI version

The ApplicationUpdaterUI version of the update framework provides a basic
interface that you can easily use in your application. The following is a basic
example.

First, create an AIR application that calls the update framework:

1.  If your application is an HTML-based AIR application, load the
    applicationupdaterui.swf file:

        <script src="ApplicationUpdater_UI.swf" type="application/x-shockwave-flash"/>

2.  In your AIR application program logic, instantiate an ApplicationUpdaterUI
    object.

    In ActionScript, use the following code:

        var appUpdater:ApplicationUpdaterUI = new ApplicationUpdaterUI();

    In JavaScript, use the following code:

        var appUpdater = new runtime.air.update.ApplicationUpdaterUI();

    You may want to add this code in an initialization function that executes
    when the application has loaded.

3.  Create a text file named updateConfig.xml and add the following to it:

        <?xml version="1.0" encoding="utf-8"?>
        <configuration xmlns="http://ns.adobe.com/air/framework/update/configuration/1.0">
            <url>http://example.com/updates/update.xml</url>
            <delay>1</delay>
        </configuration>

    Edit the `URL` element of the updateConfig.xml file to match the eventual
    location of the update descriptor file on your web server (see the next
    procedure).

    The `delay` is the number of days the application waits between checks for
    updates.

4.  Add the updateConfig.xml file to the project directory of your AIR
    application.

5.  Have the updater object reference the updateConfig.xml file, and call the
    object's `initialize()` method.

    In ActionScript, use the following code: appUpdater.configurationFile = new
    File("app:/updateConfig.xml"); appUpdater.initialize();

    In JavaScript, use the following code: appUpdater.configurationFile = new
    air.File("app:/updateConfig.xml"); appUpdater.initialize();

6.  Create a second version of the AIR application that has a different version
    than the first application. (The version is specified in the application
    descriptor file, in the `version` element.)

Next, add the update version of the AIR application to your web server:

1.  Place the update version of the AIR file on your web server.

2.  Create a text file named updateDescriptor.2.5.xml, and add the following
    contents to it:

        <?xml version="1.0" encoding="utf-8"?>
        <update xmlns="http://ns.adobe.com/air/framework/update/description/2.5">
            <versionNumber>1.1</versionNumber>
            <url>http://example.com/updates/sample_1.1.air</url>
            <description>This is the latest version of the Sample application.</description>
        </update>

    Edit the `versionNumber`, `URL`, and `description` of the
    updateDescriptor.xml file to match your update AIR file. This update
    descriptor format is used by applications using the update framework
    included with the AIR 2.5 SDK (and later).

3.  Create a text file named updateDescriptor.1.0.xml, and add the following
    contents to it:

        <?xml version="1.0" encoding="utf-8"?>
        <update xmlns="http://ns.adobe.com/air/framework/update/description/1.0">
            <version>1.1</version>
            <url>http://example.com/updates/sample_1.1.air</url>
            <description>This is the latest version of the Sample application.</description>
        </update>

    Edit the `version`, `URL`, and `description` of the updateDescriptor.xml
    file to match your update AIR file. This update descriptor format is used by
    applications using the update framework included with the AIR 2 SDK (and
    earlier).

    > **Note:** Creating this second update descriptor file is only necessary
    > when you are supporting updates to applications created prior to AIR 2.5.

4.  Add the updateDescriptor.2.5.xml and updateDescriptor.1.0.xml file to the
    same web server directory that contains the update AIR file.

This is a basic example, but it provides update functionality that is sufficient
for many applications. The remainder of this document describes how to use the
update framework to best suit your needs.

For another example of using the update framework, see the following sample
application at the Adobe AIR developer center:

- [Update Framework in a Flash-based Application](https://web.archive.org/web/20120502163951/http://www.adobe.com/devnet/air/flash/quickstart/articles/update_framework.html)
