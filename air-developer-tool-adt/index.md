# AIR Developer Tool (ADT)

<div>

The AIR Developer Tool (ADT) is a multi-purpose, command-line tool for
developing AIR applications. You can use ADT to perform the following tasks:

- Package an AIR application as an .air installation file

- Package an AIR application as a native installer—for example, as a .exe
  installer file on Windows, .ipa on iOS, or .apk on Android

- Package a native extension as an AIR Native Extension (ANE) file

- Sign an AIR application with a digital certificate

- Change (migrate) the digital signature used for application updates

- Determine the devices connected to a computer

- Create a self-signed digital code signing certificate

- Remotely install, launch, and uninstall an application on a mobile device

- Remotely install and uninstall the AIR runtime on a mobile device

ADT is a Java program included in the
[AIR SDK](http://www.adobe.com/go/learn_air_download_AIRSDK_en). You must have
Java 1.5 or higher to use it. The SDK includes a script file for invoking ADT.
To use this script, the location of the Java program must be included in the
path environment variable. If the AIR SDK `bin` directory is also listed in your
path environment variable, you can type `adt` on the command line, with the
appropriate arguments, to invoke ADT. (If you do not know how to set your path
environment variable, please refer to your operating system documentation. As a
further aid, procedures for setting the path on most computer systems are
described in
[Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html).)

At least 2GB of computer memory is required to use ADT. If you have less memory
than this, ADT can run out of memory, especially when packaging applications for
iOS.

Assuming both Java and the AIR SDK bin directory are both included in the path
variable, you can run ADT using the following basic syntax:

    adt -command options

<div>

Note: Most integrated development environments, including Adobe Flash Builder
and Adobe Flash Professional can package and sign AIR applications for you. You
typically do not need to use ADT for these common tasks when you already use
such a development environment. However, you might still need to use ADT as a
command-line tool for functions that are not supported by your integrated
development environment. In addition, you can use ADT as a command-line tool as
part of an automated build process.

</div>

- [ADT commands](WS901d38e593cd1bac1e63e3d128fc240122-8000.html)
- [ADT option sets](WS901d38e593cd1bac1e63e3d128fc240122-7ff3.html)
- [ADT error messages](WSBE9908A0-8E3A-4329-8ABD-12F2A19AB5E9.html)
- [ADT environment variables](WS901d38e593cd1bac1e63e3d129cf8c19f1-8000.html)

</div>

<div>

<div>



</div>

</div>
