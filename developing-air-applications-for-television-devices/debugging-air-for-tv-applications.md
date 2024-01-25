# Debugging AIR for TV applications

<div>

</div>

<div>

## Device simulation using ADL

<div>

The fastest, easiest way to test and debug most application features is to run
your application on your development computer using the Adobe Debug Launcher
(ADL) utility.

ADL uses the `supportedProfiles` element in the application descriptor to choose
which profile to use. Specifically:

<div>

- If more than one profile is listed, ADL uses the first one in the list.

- You can use the `-profile` parameter of ADL to select one of the other
  profiles in the `supportedProfiles` list.

- If you do not include a `supportedProfiles` element in the application
  descriptor, then any profile can be specified for the `-profile` argument.

For example, use the following command to launch an application to simulate the
`tv` profile:

</div>

    adl -profile tv myApp-app.xml

When simulating the `tv` or `extendedTV` profile on the desktop with ADL, the
application runs in an environment that more closely matches a target device.
For example:

<div>

- ActionScript APIs that are not part of the profile in the `-profile` argument
  are not available.

- ADL allows the input of device input controls, such as remote controls,
  through menu commands.

- Specifying `tv` or `extendedTV` in the `-profile` argument allows ADL to
  simulate the StageVideo class on the desktop.

- Specifying `extendedTV` in the `-profile` argument allows the application to
  use native extension stubs or simulators packaged with the application AIRN
  file.

</div>

However, because ADL runs the application on the desktop, testing AIR for TV
applications using ADL has limitations:

<div>

- It does not reflect application performance on the device. Run performance
  tests on the target device.

- It does not simulate the limitations of the StageVideo object. Typically, you
  use the StageVideo class, not the Video class, to play a video when targeting
  AIR for TV devices. The StageVideo class takes advantage of performance
  benefits of the device’s hardware, but has display limitations. ADL plays the
  video on the desktop without these limitations. Therefore, test playing video
  on the target device.

- It cannot simulate the native code of a native extension. You can, however,
  specify the `extendedTV` profile, which supports native extensions, in the ADL
  `-profile` argument. ADL allows you to test with the ActionScript-only stub or
  simulator version of the extension included in the ANE package. However,
  typically the corresponding extension that is installed on the device also
  includes native code. To test using the extension with its native code, run
  the application on the target device.

</div>

For more information, see
[AIR Debug Launcher (ADL)](WSfffb011ac560372f-6fa6d7e0128cca93d31-8000.html).

<div>

#### Using native Extensions

If your application uses native extensions, the ADL command looks like the
following example:

    adl -profile extendedTV -extdir C:\extensionDirs myApp-app.xml

The example assumes that:

<div>

- The path to the ADL tool is on your command-line shell’s path definition. (See
  [Path environment variables](WSfffb011ac560372f-71994050128cca87097-8000.html).)

- The current directory contains the application files. These files include the
  SWF files and the application descriptor file, which is myApp-app.xml in this
  example.

- The parameter `-extdir` names a directory that contains a directory for each
  native extension that the application uses. Each of these directories contains
  the _unpackaged_ ANE file of a native extension. For example:

  <div>

      C:\extensionDirs
          extension1.ane
              META-INF
                  ANE
                      default
                          library.swf
                      extension.xml
                  signatures.xml
              catalog.xml
              library.swf
              mimetype
          extension2.ane
              META-INF
                  ANE
                      default
                          library.swf
                      extension.xml
                  signatures.xml
              catalog.xml
              library.swf
              mimetype


  </div>

  These unpackaged ANE files contain an ActionScript-only stub or simulator
  version of the extension. The version of the extension that contains the
  native code is installed on the AIR for TV device.

</div>

For more information, see
[Developing Native Extensions for Adobe AIR](http://www.adobe.com/go/learn_air_as_extensions_en).

</div>

<div>

#### Control input

ADL simulates the remote control buttons on a TV device. You can send these
button inputs to the simulated device using the menu displayed when ADL is
launched using one of the TV profiles.

</div>

<div>

#### Screen size

You can test your application on different size screens by setting the ADL
`-screensize` parameter. You can specify a string containing the four values
representing the widths and heights of the normal and maximized screens.

Always specify the pixel dimensions for portrait layout, meaning specify the
width as a value smaller than the value for height. For example:

    adl -screensize 728x1024:768x1024 myApp-app.xml

</div>

</div>

</div>

<div>

## Trace statements

<div>

When you run your TV application on the desktop, trace output is printed to
either the debugger or the terminal window used to launch ADL.

</div>

</div>

<div>

## Remote debugging with Flash Professional

<div>

You can use Flash Professional to remotely debug your AIR for TV application
while it runs on the target device. However, the steps to set up remote
debugging depend on the device. For example, the Adobe® AIR® for TV MAX 2010
Hardware Development Kit contains documentation for detailed steps for that
device.

Regardless of the target device, however, do the following steps to prepare for
remote debugging:

1.  In the Publish Settings dialog box, in the Flash tab, select Permit
    Debugging.

    This option causes Flash Professional to include debugging information in
    all the SWF files it creates from your FLA file.

2.  In the Signature tab of the Adobe AIR Settings dialog box (Application and
    Installer Settings), select the option to prepare an AIR Intermediate (AIRI)
    file.

    When you are still developing your application, using an AIRI file, which
    requires no digital signature, is sufficient.

3.  Publish your application, creating the AIRI file.

The last steps are installing and running the application on the target device.
However, these steps are dependent on the device.

</div>

</div>

<div>

## Remote debugging with Flash Builder

<div>

You can also use Flash Builder to remotely debug your AIR for TV application
while it runs on the target device. However, the steps to do remote debugging
depend on the device.

Regardless of the target device, however, do the following steps to prepare for
remote debugging:

1.  Select Project \> Export Release Build. Select the option to prepare an AIR
    Intermediate (AIRI) file.

    When you are still developing your application, using an AIRI file, which
    requires no digital signature, is sufficient.

2.  Publish your application, creating the AIRI file.

3.  Change the application’s AIRI package to contain SWF files that contain
    debug information.

    The SWF files that contain debug information are located in the Flash
    Builder project directory for the application in a directory called
    bin-debug. Replace the SWF files in the AIRI package with the SWF files in
    the bin-debug directory.

On a Windows development machine, you can make this replacement by doing the
following:

<div>

1.  Rename the AIRI package file to have the filename extension .zip instead of
    .airi.

2.  Extract the ZIP file contents.

3.  Replace the SWF files in the extracted directory structure with the ones
    from bin-debug.

4.  Re-zip the files in the extracted directory.

5.  Change the zipped file to once again have the .airi filename extension.

</div>

If you are using a Mac development machine, the steps for this replacement are
device-dependent. However, they generally involve the following:

<div>

1.  Install the AIRI package on the target device.

2.  Replace the SWF files in the application’s installation directory on the
    target device with the SWF files from the bin-debug directory.

    For example, consider the device included with the Adobe AIR for TV MAX 2010
    Hardware Development Kit. Install the AIRI package as described in the kit
    documentation. Then, use telnet on the command line of your Mac development
    machine to access your target device. Replace the SWF files in the
    application installation directory at
    /opt/adobe/stagecraft/apps/_\<application name\>_/ with the SWF files from
    the bin-debug directory.

</div>

The following steps are for remote debugging with Flash Builder and the device
included with the Adobe AIR for TV MAX 2010 Hardware Development Kit.

<div>

1.  On the computer running Flash Builder, your development computer, run the
    AIR for TV Device Connector that comes with the MAX 2010 Hardware
    Development Kit. It shows the IP address of your development computer.

2.  On the hardware kit device, launch the DevMaster application, which also
    comes with the development kit.

3.  In the DevMaster application, enter the IP address of your development
    computer as shown in the AIR for TV Device Connector.

4.  In the DevMaster application, make sure that Enable Remote Debugging is
    selected.

5.  Exit the DevMaster application.

6.  On the development computer, select Start in the AIR for TV Connector.

7.  On the hardware kit device, start another application. Verify that trace
    information displays in the AIR for TV Device Connector.

    If trace information does not display, the development computer and the
    hardware kit device are not connected. Make sure the port on the development
    computer that is used for trace information is available. You can choose a
    different port in the AIR for TV Device Connector. Also, make sure that your
    firewall allows access to the chosen port.

</div>

Next, start the debugger in Flash Builder. Do the following:

<div>

1.  In Flash Builder, select Run \> Debug Configurations.

2.  From the existing debug configuration, which is for local debugging, copy
    the name of the project.

3.  In the Debug Configurations dialog box, select Web Application. Then select
    the New Launch Configuration icon.

4.  Paste the project name into the Project field.

5.  In the URL Or Path To Launch section, remove the check from Use Default.
    Also, enter <span class="kbd">`about:blank`</span> in the text field.

6.  Select Apply to save your changes.

7.  Select Debug to start the Flash Builder debugger.

8.  Start your application on the hardware kit device.

</div>

You can now use the Flash Builder debugger to, for example, set breakpoints and
examine variables.

</div>

</div>

<div>

<div>



</div>

</div>
