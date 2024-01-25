# Updating to AIR 2.5

Because the rules for assigning version numbers to applications changed in AIR
2.5, the AIR 2 update framework cannot parse the version information in an AIR
2.5 application descriptor. This incompatibility means that you must update your
application to use the new update framework BEFORE you update your application
to use the AIR 2.5 SDK. Thus, updating your application to AIR 2.5 or later from
any version of AIR before 2.5, requires TWO updates. The first update must use
the AIR 2 namespace and include the AIR 2.5 update framework library (you can
still create the application package using the AIR 2.5 SDK). The second update
can use the AIR 2.5 namespace and include the new features of your application.

You can also have the intermediate update do nothing except update to your AIR
2.5 application using the AIR Updater class directly.

The following example illustrates how to update an application from version 1.0
to 2.0. Version 1.0 uses the old 2.0 namespace. Version 2.0 uses the 2.5
namespace and has new features implemented using AIR 2.5 APIs.

1.  Create an intermediate version of the application, version 1.0.1, based on
    version 1.0 of the application.

    1.  Use AIR 2.5 Application Updater framework while creating the
        application.

        Note: Use `applicationupdater.swc` or `applicationupdater_ui.swc` for
        AIR applications based on Flash technology and `applicationupdater.swf`
        or `applicationupdater_ui.swf` for HTML-based AIR applications.

    2.  Create an update descriptor file for version 1.0.1 by using the old
        namespace and the version as shown below:

            <?xml version="1.0" encoding="utf-8"?>
            <update xmlns="http://ns.adobe.com/air/framework/update/description/2.0">
                <version>1.0.1</version>
                <url>http://example.com/updates/sample_1.0.1.air</url>
                <description>This is the intermediate version.</description>
            </update>

2.  Create the version 2.0 of the application that uses AIR 2.5 APIs and 2.5
    namespace.

3.  Create an update descriptor to update the application from the 1.0.1 version
    to 2.0 version.

        <?xml version="1.0" encoding="utf-8"?>
        <update xmlns="http://ns.adobe.com/air/framework/update/description/2.5">
            <version>2.0</version>
            <url>http://example.com/updates/sample_2.0.air</url>
            <description>This is the intermediate version.</description>
        </update>
