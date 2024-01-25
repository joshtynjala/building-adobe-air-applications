# Workflow for developing an AIR for TV application

<div>

You can develop AIR for TV applications with the following Adobe Flash Platform
development tools:

<div>

- Adobe Flash Professional

  Adobe Flash Professional CS5.5 supports AIR 2.5 for TV, the first version of
  AIR to support AIR for TV applications.

- Adobe Flash® Builder®

  Flash Builder 4.5 supports AIR 2.5 for TV.

- The AIR SDK

  Starting with AIR 2.5, you can develop your applications using the
  command-line tools provided with the AIR SDK. To download the AIR SDK, see
  <http://www.adobe.com/products/air/sdk/>.

</div>

</div>

<div>

## Using Flash Professional

<div>

Using Flash Professional to develop, test, and publish AIR for TV applications
is similar to using the tool for AIR desktop applications.

However, when writing your ActionScript 3.0 code, use only classes and methods
that the `tv` and `extendedTV` AIR profiles support. For details, see
[Device profiles](WS144092a96ffef7cc16ddeea2126bb46b82f-8000.html).

</div>

<div>

### Project settings

<div>

Do the following to set up your project for an AIR for TV application:

<div>

- In the Flash tab of the Publish Settings dialog box, set the Player value to
  at least AIR 2.5.

- In the General tab of the Adobe AIR Settings dialog box (Application and
  Installer Settings), set the profile to `TV` or `extended` TV.

</div>

</div>

</div>

<div>

### Debugging

<div>

You can run your application using the AIR Debug Launcher within Flash
Professional. Do the following:

<div>

- To run the application in debugging mode, select:

  Debug \> Debug Movie \> In AIR Debug Launcher (Desktop)

  Once you have made this selection, for subsequent debugging runs, you can
  select:

  Debug \> Debug Movie \> Debug

- To run the application without debugging mode capabilities, select:

  Control \> Test Movie \> In AIR Debug Launcher (Desktop)

  Once you have made this selection, you can select Control \> Test Movie \>
  Test for subsequent runs.

</div>

Because you set the AIR profile to TV or extended TV, the AIR Debug Launcher
provides a menu called Remote Control Buttons. You can use this menu to simulate
pressing keys on a remote control device.

For more information, see
[Remote debugging with Flash Professional](WS62b4b4caef5f7931-1f86f0fb1328dba45c2-7fce.html).

</div>

</div>

<div>

### Using native extensions

<div>

If your application uses a native extension, follow the instructions at
[Task list for using a native extension](WS08cc5e527b0868243ea2ffcd1314dff873a-7fff.html).

However, when an application uses native extensions:

- You cannot publish the application using Flash Professional. To publish the
  application, use ADT. See
  [Packaging with ADT](WS62b4b4caef5f7931-1f86f0fb1328dba45c2-7fd3.html).

- You cannot run or debug the application using Flash Professional. To debug the
  application on the development machine, use ADL. See
  [Device simulation using ADL](WS62b4b4caef5f7931-1f86f0fb1328dba45c2-7fd0.html).

</div>

</div>

</div>

<div>

## Using Flash Builder

<div>

Starting with Flash Builder 4.5, Flash Builder supports AIR for TV development.
Using Flash Builder to develop, test, and publish AIR for TV applications is
similar to using the tool for AIR desktop applications.

</div>

<div>

### Setting up the application

<div>

Make sure that your application:

<div>

- Uses the `Application` element as the container class in the MXML file, if you
  are using an MXML file:

      <s:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
          xmlns:s="library://ns.adobe.com/flex/spark"
          xmlns:mx="library://ns.adobe.com/flex/mx">

          <!-- Place elements here. -->

      </s:Application>.

  <div>

  Important: AIR for TV applications do not support the `WindowedApplication`
  element.

  </div>

  <div>

  Note: You do not have to use an MXML file at all. You can instead create an
  ActionScript 3.0 project.

  </div>

- Uses only ActionScript 3.0 classes and methods that the `tv` and `extendedTV`
  AIR profiles support. For details, see
  [Device profiles](WS144092a96ffef7cc16ddeea2126bb46b82f-8000.html).

</div>

Furthermore, in your application’s XML file, make sure that:

<div>

- The `application` element’s `xmlns` attribute is set to AIR 2.5:

      <application xmlns="http://ns.adobe.com/air/application/2.5">

- The `supportedProfiles` element includes `tv` or `extendedTV`:

      <supportedProfiles>tv</supportedProfiles>

</div>

</div>

</div>

<div>

### Debugging the application

<div>

You can run your application using the AIR Debug Launcher within Flash Builder.
Do the following:

1.  Select Run \> Debug Configurations.

2.  Make sure that the Profile field is set to Desktop.

3.  Select Run \> Debug to run in debugging mode or select Run \> Run to run
    without debugging mode capabilities.

Because you set the `supportedProfiles` element to TV or extended TV, the AIR
Debug Launcher provides a menu called Remote Control Buttons. You can use this
menu to simulate pressing keys on a remote control device.

For more information, see
[Remote debugging with Flash Builder](WS62b4b4caef5f7931-1f86f0fb1328dba45c2-7fcd.html).

</div>

</div>

<div>

### Using native extensions

<div>

If your application uses a native extension, follow the instructions at
[Task list for using a native extension](WS08cc5e527b0868243ea2ffcd1314dff873a-7fff.html).

However, when an application uses native extensions:

- You cannot publish the application using Flash Builder. To publish the
  application, use ADT. See
  [Packaging with ADT](WS62b4b4caef5f7931-1f86f0fb1328dba45c2-7fd3.html).

- You cannot run or debug the application using Flash Builder. To debug the
  application on the development machine, use ADL. See
  [Device simulation using ADL](WS62b4b4caef5f7931-1f86f0fb1328dba45c2-7fd0.html).

</div>

</div>

</div>

<div>

<div>



</div>

</div>
