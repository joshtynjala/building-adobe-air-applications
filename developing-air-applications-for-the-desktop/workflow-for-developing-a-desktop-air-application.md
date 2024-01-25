# Workflow for developing a desktop AIR application

The basic workflow for developing an AIR application is the same as most
traditional development models: code, compile, test, and, towards the end of the
cycle, package into an installer file.

You can write the application code using Flash, Flex, and ActionScript and
compile using Flash Professional, Flash Builder or the mxmlc and compc
command-line compilers. You can also write the application code using HTML and
JavaScript and skip the compilation step.

You can test desktop AIR applications with the ADL tool, which runs an
application without requiring it to be packaged and installed first. Flash
Professional, Flash Builder, Dreamweaver, and the Aptana IDE all integrate with
the Flash debugger. You can also launch the debugger tool, FDB, manually when
using ADL from the command line. ADL, itself, does display errors and trace
statement output.

All AIR applications must be packaged into an install file. The cross-platform
AIR file format is recommended unless:

- You need to access platform-dependent APIs such as the NativeProcess class.

- Your application uses native extensions.

In such cases, you can package an AIR application as a platform-specific native
installer file.

## SWF-based applications

1.  Write the MXML or ActionScript code.

2.  Create needed assets, such as icon bitmap files.

3.  Create the application descriptor.

4.  Compile ActionScript code.

5.  Test the application.

6.  Package and sign as an AIR file using the _air_ target.

## HTML-based applications

1.  Write the HTML and JavaScript code.

2.  Create needed assets, such as icon bitmap files.

3.  Create the application descriptor.

4.  Test the application.

5.  Package and sign as an AIR file using the _air_ target.

## Creating native installers for AIR applications

1.  Write the code (ActionScript or HTML and JavaScript).

2.  Create needed assets, such as icon bitmap files.

3.  Create the application descriptor, specifying the _extendedDesktop_ profile.

4.  Compile any ActionScript code.

5.  Test the application.

6.  Package the application on each target platform using the _native_ target.

Note: The native installer for a target platform must be created on that
platform. You cannot, for example, create a Windows installer on a Mac. You can
use a virtual machine such as VMWare to run multiple platforms on the same
computer hardware.

## Creating AIR applications with a captive runtime bundle

1.  Write the code (ActionScript or HTML and JavaScript).

2.  Create needed assets, such as icon bitmap files.

3.  Create the application descriptor, specifying the _extendedDesktop_ profile.

4.  Compile any ActionScript code.

5.  Test the application.

6.  Package the application on each target platform using the _bundle_ target.

7.  Create an install program using the bundle files. (The AIR SDK does not
    provide tools for creating such an installer, but many third-party toolkits
    are available.)

Note: The bundle for a target platform must be created on that platform. You
cannot, for example, create a Windows bundle on a Mac. You can use a virtual
machine such as VMWare to run multiple platforms on the same computer hardware.
