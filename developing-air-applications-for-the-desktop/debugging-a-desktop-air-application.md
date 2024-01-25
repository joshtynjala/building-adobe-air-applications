# Debugging a desktop AIR application

<div>

If you are developing your application with an IDE such as Flash Builder, Flash
Professional, or Dreamweaver, debugging tools are normally built in. You can
debug your application simply be launching it in debug mode. If you are not
using an IDE that supports debugging directly, you can use the AIR Debug
Launcher (ADL) and the Flash Debugger (FDB) to assist in debugging your
application.

</div>

<div>

## Running an application with ADL

<div>

You can run an AIR application without packaging and installing it using ADL.
Pass the application descriptor file to ADL as a parameter as shown in the
following example (ActionScript code in the application must be compiled first):

    adl myApplication-app.xml

ADL prints trace statements, runtime exceptions, and HTML parsing errors to the
terminal window. If an FDB process is waiting for an incoming connection, ADL
will connect to the debugger.

You can also use ADL to debug an AIR application that uses native extensions.
For example:

    adl -extdir extensionDirs myApplication-app.xml

</div>

</div>

<div>

## Printing trace statements

<div>

To print trace statements to the console used to run ADL, add trace statements
to your code with the `trace()` function.

<div>

Note: If your `trace()` statements do not display on the console, ensure that
you have not specified `ErrorReportingEnable` or `TraceOutputFileEnable` in the
mm.cfg file. For more information on the platform-specific location of this
file, see
[Editing the mm.cfg file](http://help.adobe.com/en_US/flex/using/WS2db454920e96a9e51e63e3d11c0bf69084-7fc9.html).

</div>

ActionScript example:

    //ActionScript
    trace("debug message");

JavaScript example:

    //JavaScript
    air.trace("debug message");

<div>

In JavaScript code, you can use the `alert()` and `confirm()` functions to
display debugging messages from your application. In addition, the line numbers
for syntax errors as well as any uncaught JavaScript exceptions are printed to
the console.

<div>

Note: To use the air prefix shown in the JavaScript example, you must import the
AIRAliases.js file into the page. This file is located inside the frameworks
directory of the AIR SDK.

</div>

</div>

</div>

</div>

<div>

## Connecting to the Flash Debugger (FDB)

<div>

To debug AIR applications with the Flash Debugger, start an FDB session and then
launch your application using ADL.

<div>

Note: In SWF-based AIR applications, the ActionScript source files must be
compiled with the `-debug` flag. (In Flash Professional, check the Permit
debugging option in the Publish Settings dialog.)

</div>

1.  Start FDB. The FDB program can be found in the `bin` directory of the Flex
    SDK.

    The console displays the FDB prompt: `<fdb>`

2.  Execute the `run` command: `<fdb>run [Enter]`

3.  In a different command or shell console, start a debug version of your
    application:

        adl myApp.xml

4.  Using the FDB commands, set breakpoints as desired.

5.  Type: `continue [Enter]`

If an AIR application is SWF-based, the debugger only controls the execution of
ActionScript code. If the AIR application is HTML-based, then the debugger only
controls the execution of JavaScript code.

To run ADL without connecting to the debugger, include the `-nodebug` option:

<div>

    adl myApp.xml -nodebug

</div>

For basic information on FDB commands, execute the `help` command:

    <fdb>help [Enter]

For details on the FDB commands, see
[Using the command-line debugger commands](http://livedocs.adobe.com/flex/3/html/debugging_05.html)
in the Flex documentation.

</div>

</div>

<div>

<div>

More Help topics

</div>

<div>

[Debugging with the AIR HTML Introspector](WS5b3ccc516d4fbf351e63e3d118666ade46-7ed2.html)

[AIR Debug Launcher (ADL)](WSfffb011ac560372f-6fa6d7e0128cca93d31-8000.html)

</div>

[De Monsters: Monster Debugger](http://demonsterdebugger.com/home "http://demonsterdebugger.com/home")

<div>



</div>

</div>
