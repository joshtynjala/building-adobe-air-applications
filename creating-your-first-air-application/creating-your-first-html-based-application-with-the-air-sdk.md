# Creating your first HTML-based AIR application with the AIR SDK

For a quick, hands-on illustration of how Adobe® AIR® works, use these
instructions to create and package a simple HTML-based AIR "Hello World"
application.

To begin, you must have installed the runtime and set up the AIR SDK. You will
use the _AIR Debug Launcher_ (ADL) and the _AIR Developer Tool_ (ADT) in this
tutorial. ADL and ADT are command-line utility programs and can be found in the
`bin` directory of the AIR SDK (see
[Installing the AIR SDK](WS2d8d13466044a73328ed2239124110d12b3-8000.html)). This
tutorial assumes that you are already familiar with running programs from the
command line and know how to set up the necessary path environment variables for
your operating system.

Note: If you are an Adobe® Dreamweaver® user, read
[Create your first HTML-based AIR application with Dreamweaver](WS5b3ccc516d4fbf351e63e3d118666ade46-7f7f.html).

Note: HTML-based AIR applications can only be developed for the desktop and the
extendedDesktop profiles. The mobile profile is not supported.

## Create the project files

Every HTML-based AIR project must contain the following two files: an
application descriptor file, which specifies the application metadata, and a
top-level HTML page. In addition to these required files, this project includes
a JavaScript code file, `AIRAliases.js`, that defines convenient alias variables
for the AIR API classes.

1.  Create a directory named `HelloWorld` to contain the project files.

2.  Create an XML file, named `HelloWorld-app.xml`.

3.  Create an HTML file named `HelloWorld.html`.

4.  Copy `AIRAliases.js` from the frameworks folder of the AIR SDK to the
    project directory.

## Create the AIR application descriptor file

To begin building your AIR application, create an XML application descriptor
file with the following structure:

    <application xmlns="...">
        <id>…</id>
        <versionNumber>…</versionNumber>
        <filename>…</filename>
        <initialWindow>
            <content>…</content>
            <visible>…</visible>
            <width>…</width>
            <height>…</height>
        </initialWindow>
    </application>

1.  Open the `HelloWorld-app.xml` for editing.

2.  Add the root `<application>` element, including the AIR namespace attribute:

    **\<application xmlns="http://ns.adobe.com/air/application/2.7"\>** The last
    segment of the namespace, "2.7", specifies the version of the runtime
    required by the application.

3.  Add the `<id>` element:

    **\<id\>examples.html.HelloWorld\</id\>** The application ID uniquely
    identifies your application along with the publisher ID (which AIR derives
    from the certificate used to sign the application package). The application
    ID is used for installation, access to the private application file-system
    storage directory, access to private encrypted storage, and interapplication
    communication.

4.  Add the `<versionNumber>` element:

    **\<versionNumber\>0.1\</versionNumber\>** Helps users to determine which
    version of your application they are installing.

    Note: If you are using AIR 2, or earlier, you must use the `<version>`
    element instead of the `<versionNumber>` element.

5.  Add the `<filename>` element:

    **\<filename\>HelloWorld\</filename\>** The name used for the application
    executable, install directory, and other references to the application in
    the operating system.

6.  Add the `<initialWindow>` element containing the following child elements to
    specify the properties for your initial application window:

    **\<content\>HelloWorld.html\</content\>** Identifies the root HTML file for
    AIR to load.

    **\<visible\>true\</visible\>** Makes the window visible immediately.

    **\<width\>400\</width\>** Sets the window width (in pixels).

    **\<height\>200\</height\>** Sets the window height.

7.  Save the file. The completed application descriptor file should look like
    the following:

        <?xml version="1.0" encoding="UTF-8"?>
        <application xmlns="http://ns.adobe.com/air/application/2.7">
            <id>examples.html.HelloWorld</id>
            <versionNumber>0.1</versionNumber>
            <filename>HelloWorld</filename>
            <initialWindow>
                <content>HelloWorld.html</content>
                <visible>true</visible>
                <width>400</width>
                <height>200</height>
            </initialWindow>
        </application>

This example only sets a few of the possible application properties. For the
full set of application properties, which allow you to specify such things as
window chrome, window size, transparency, default installation directory,
associated file types, and application icons, see
[AIR application descriptor files](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html).

## Create the application HTML page

You now need to create a simple HTML page to serve as the main file for the AIR
application.

1.  Open the `HelloWorld.html` file for editing. Add the following HTML code:

        <html>
        <head>
            <title>Hello World</title>
        </head>
        <body onLoad="appLoad()">
            <h1>Hello World</h1>
        </body>
        </html>

2.  In the `<head>` section of the HTML, import the `AIRAliases.js` file:

        <script src="AIRAliases.js" type="text/javascript"></script>

    AIR defines a property named `runtime` on the HTML window object. The
    runtime property provides access to the built-in AIR classes, using the
    fully qualified package name of the class. For example, to create an AIR
    File object you could add the following statement in JavaScript:

        var textFile = new runtime.flash.filesystem.File("app:/textfile.txt");

    The `AIRAliases.js` file defines convenient aliases for the most useful AIR
    APIs. Using `AIRAliases.js`, you could shorten the reference to the File
    class to the following:

        var textFile = new air.File("app:/textfile.txt");

3.  Below the AIRAliases script tag, add another script tag containing a
    JavaScript function to handle the `onLoad` event:

        <script type="text/javascript">
        function appLoad(){
            air.trace("Hello World");
        }
        </script>

    The `appLoad()` function simply calls the `air.trace()` function. The trace
    message print to the command console when you run the application using ADL.
    Trace statements can be very useful for debugging.

4.  Save the file.

Your `HelloWorld.html` file should now look like the following:

    <html>
    <head>
        <title>Hello World</title>
        <script type="text/javascript" src="AIRAliases.js"></script>
        <script type="text/javascript">
            function appLoad(){
                air.trace("Hello World");
            }
        </script>
    </head>
    <body onLoad="appLoad()">
        <h1>Hello World</h1>
    </body>
    </html>

## Test the application

To run and test the application from the command line, use the AIR Debug
Launcher (ADL) utility. The ADL executable can be found in the `bin` directory
of the AIR SDK. If you haven't already set up the AIR SDK, see
[Installing the AIR SDK](WS2d8d13466044a73328ed2239124110d12b3-8000.html).

1.  Open a command console or shell. Change to the directory you created for
    this project.

2.  Run the following command:

        adl HelloWorld-app.xml

    An AIR window opens, displaying your application. Also, the console window
    displays the message resulting from the `air.trace()` call.

    For more information, see
    [AIR application descriptor files](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html).

## Create the AIR installation file

When your application runs successfully, you can use the ADT utility to package
the application into an AIR installation file. An AIR installation file is an
archive file that contains all the application files, which you can distribute
to your users. You must install Adobe AIR before installing a packaged AIR file.

To ensure application security, all AIR installation files must be digitally
signed. For development purposes, you can generate a basic, self-signed
certificate with ADT or another certificate generation tool. You can also buy a
commercial code-signing certificate from a commercial certificate authority such
as VeriSign or Thawte. When users install a self-signed AIR file, the publisher
is displayed as "unknown" during the installation process. This is because a
self-signed certificate only guarantees that the AIR file has not been changed
since it was created. There is nothing to prevent someone from self-signing a
masquerade AIR file and presenting it as your application. For publicly released
AIR files, a verifiable, commercial certificate is strongly recommended. For an
overview of AIR security issues, see
[AIR security](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7fa3.html)
(for ActionScript developers) or
[AIR security](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7d23.html)
(for HTML developers).

#### Generate a self-signed certificate and key pair

![](../img/dingbat.png) From the command prompt, enter the following command
(the ADT executable is located in the `bin` directory of the AIR SDK):

    adt -certificate -cn SelfSigned 1024-RSA sampleCert.pfx samplePassword

ADT generates a keystore file named _sampleCert.pfx_ containing a certificate
and the related private key.

This example uses the minimum number of attributes that can be set for a
certificate. The key type must be either _1024-RSA_ or _2048-RSA_ (see
[Signing AIR applications](WSfffb011ac560372f-19aa73f128cc9f05e8-8000.html)).

#### Create the AIR installation file

![](../img/dingbat.png) From the command prompt, enter the following command (on
a single line):

    adt -package -storetype pkcs12 -keystore sampleCert.pfx HelloWorld.air
    HelloWorld-app.xml HelloWorld.html AIRAliases.js

You will be prompted for the keystore file password.

The HelloWorld.air argument is the AIR file that ADT produces.
HelloWorld-app.xml is the application descriptor file. The subsequent arguments
are the files used by your application. This example only uses two files, but
you can include any number of files and directories. ADT verifies that the main
content file, HelloWorld.html is included in the package, but if you forget to
include AIRAliases.js, then your application simply won't work.

After the AIR package is created, you can install and run the application by
double-clicking the package file. You can also type the AIR filename as a
command in a shell or command window.

## Next Steps

In AIR, HTML and JavaScript code generally behaves the same as it would in a
typical web browser. (In fact, AIR uses the same WebKit rendering engine used by
the Safari web browser.) However, there are some important differences that you
must understand when you develop HTML applications in AIR. For more information
on these differences, and other important topics, see
[Programming HTML and JavaScript](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7fa7.html).
