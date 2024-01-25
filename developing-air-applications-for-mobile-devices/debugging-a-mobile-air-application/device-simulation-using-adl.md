# Device simulation using ADL

The fastest, easiest way to test and debug most mobile application features is
to run your application on your development computer using the Adobe Debug
Launcher (ADL) utility. ADL uses the `supportedProfiles` element in the
application descriptor to determine which profile to use. If more than one
profile is listed, ADL uses the first one in the list. You can also use the
`-profile` parameter of ADL to select one of the other profiles in the
`supportedProfiles` list. (If you do not include a `supportedProfiles` element
in the application descriptor, then any profile can be specified for the
`-profile` argument.) For example, use the following command to launch an
application to simulate the mobile device profile:

    adl -profile mobileDevice myApp-app.xml

When simulating the mobile profile on the desktop like this, the application
runs in an environment that more closely matches a target mobile device.
ActionScript APIs that are not part of the mobile profile are not available.
However, ADL does not distinguish between the capabilities of different mobile
devices. For example, you can send simulated soft-key presses to your app, even
though your actual target device does not utilize soft keys.

ADL support simulations of device orientation changes and soft key input through
menu commands. When you run ADL in the mobile device profile, the ADL displays a
menu (in either the application window or the desktop menu bar) that allows you
to enter device rotation or soft key input.

#### Soft key input

ADL simulates the soft key buttons for Back, Menu, and Search buttons on a
mobile device. You can send these keys to the simulated device using the menu
displayed when ADL is launched using the mobile profile.

#### Device rotation

ADL lets you simulate device rotation through the menu displayed when ADL is
launched using the mobile profile. You can rotate the simulated device to the
right or the left.

The rotation simulation only affects an application that enables
auto-orientation. You can enable this feature by setting the `autoOrients`
element to `true` in the application descriptor.

#### Screen size

You can test your application on different size screens by setting the ADL
`‑screensize` parameter. You can pass in the code for one of the predefined
screen types or a string containing the four values representing the pixel
dimensions of the normal and maximized screens.

Always specify the pixel dimensions for portrait layout, meaning specify the
width as a value smaller than the value for height. For example, the following
command would open ADL to simulate the screen used on the Motorola Droid:

    adl -screensize 480x816:480x854 myApp-app.xml

For a list of the predefined screen types, see
[ADL usage](WS5b3ccc516d4fbf351e63e3d118666ade46-7f65.html).

#### Limitations

Some APIs that are not supported on the desktop profile cannot be simulated by
ADL. The APIs that are not simulated include:

- Accelerometer

- cacheAsBitmapMatrix

- CameraRoll

- CameraUI

- Geolocation

- Multitouch and gestures on desktop operating systems that do not support these
  features

- SystemIdleMode

If your application uses these classes, you should test the features on an
actual device or emulator.

Similarly, there are APIs that work when running under ADL on the desktop, but
which do not work on all types of mobile devices. These include:

- Speex and AAC audio codec

- Accessibility and screen reader support

- RTMPE

- Loading SWF files containing ActionScript bytecode

- PixelBender shaders

Be sure to test applications that use these features on the target devices since
ADL does not entirely replicate the execution environment.
