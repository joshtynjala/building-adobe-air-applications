# Mobile application design considerations

The operating context and physical characteristics of mobile devices demand
careful coding and design. For example, streamlining code so that it executes as
fast as possible is crucial. Code optimization can only go so far, of course;
intelligent design that works within the device limitations can also help
prevent your visual presentation from overtaxing the rendering system.

**Code**

While making your code run faster is always beneficial, the slower processor
speed of most mobile devices increases the rewards of the time spent writing
lean code. In addition, mobile devices are almost always run on battery power.
Achieving the same result with less work uses less battery power.

**Design**

Factors like the small screen size, the touch-screen interaction mode, and even
the constantly changing environment of a mobile user must be considered when
designing the user experience of your application.

**Code and design together**

If your application uses animation, then rendering optimization is very
important. However, code optimization alone is often not enough. You must design
the visual aspects of the application such that the code can render them
efficiently.

Important optimization techniques are discussed in the
[Optimizing Content for the Flash Platform](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/mobile/index.html)
guide. The techniques covered in the guide apply to all Flash and AIR content,
but are essential to developing applications that run well on mobile devices.

- [Paul Trani: Tips and Tricks for Mobile Flash Development](https://www.slideshare.net/paultrani/tips-and-tricks-for-mobile-flash-development)

- [roguish: GPU Test App AIR for Mobile](https://web.archive.org/web/20150628042611/http://www.roguish.com/blog/?p=214)

- [Jonathan Campos: Optimization Techniques for AIR for Android apps](https://web.archive.org/web/20120513072615/http://www.unitedmindset.com/jonbcampos/2010/09/08/optimization-techniques-for-air-for-android-apps/)

- [Charles Schulze: AIR 2.6 Game Development: iOS included](https://web.archive.org/web/20150217173740/http://www.flash-3d.net/2011/03/air-2-6-game-development/)

## Application life cycle

When your application loses focus to another app, AIR drops the framerate to 4
frames-per-second and stops rendering graphics. Below this framerate, streaming
network and socket connections tend to break. If your app doesn't use such
connections, you can throttle the framerate even lower.

When appropriate, you should stop audio playback and remove listeners to the
geolocation and accelerometer sensors. The AIR NativeApplication object
dispatches activate and deactivate events. Use these events to manage the
transition between the active and the background state.

Most mobile operating systems terminate background applications without warning.
By saving application state frequently, your application should be able to
restore itself to a reasonable state whether it is returning to active status
from the background or by being launched anew.

## Information density

The physical size of the screen of mobile devices is smaller than on the
desktop, although their pixel density (pixels per inch) is higher. The same font
size will produce letters that are physically smaller on a mobile device screen
than on a desktop computer. You must often use a larger font to ensure
legibility. In general, 14 point is the smallest font size that can be easily
read.

Mobile devices are often used on the move and under poor lighting conditions.
Consider how much information you can realistically display on screen legibly.
It might be less than you would display on a screen of the same pixel dimensions
on a desktop.

Also consider that when a user is touching the screen, their finger and hand
block part of the display from view. Place interactive elements at the sides and
bottom of the screen when the user has to interact with them for longer than a
momentary touch.

## Text input

Many devices use a virtual keyboard for text entry. Virtual keyboards obscure
part of the screen and are often cumbersome to use. Avoid relying on keyboard
events (except for soft keys).

Consider implementing alternatives to using input text fields. For example, to
have the user enter a numerical value, you do not need a text field. You can
provide two buttons to increase or decrease the value.

## Soft keys

Mobile devices include a varying number of soft keys. Soft keys are buttons that
are programmable to have different functions. Follow the platform conventions
for these keys in your application.

## Screen orientation changes

Mobile content can be viewed in portrait or landscape orientation. Consider how
your application will deal with screen orientation changes. For more
information, see
[Stage orientation](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/WS901d38e593cd1bac3bf97f12ca4e5c567-8000.html).

## Screen dimming

AIR does not automatically prevent the screen from dimming while video is
playing. You can use the `systemIdleMode` property of the AIR NativeApplication
object to control whether the device will enter a power-saving mode. (On some
platforms, you must request the appropriate permissions for this feature to
work.)

## Incoming phone calls

The AIR runtime automatically mutes audio when the user makes or receives a
phone call. On Android, you should set the Android READ_PHONE_STATE permission
in the application descriptor if your application plays audio while it is in the
background. Otherwise, Android prevents the runtime from detecting phone calls
and muting the audio automatically. See
[Android permissions](WS901d38e593cd1bac1e63e3d129d39606f2-8000.html).

## Hit targets

Consider the size of hit targets when designing buttons and other user interface
elements that the user taps. Make these elements large enough that they can be
comfortably activated with a finger on a touch screen. Also, make sure that you
have enough space between targets. The hit target area should be about 44 pixels
to 57 pixels on each side for a typical high-dpi phone screen.

## Application package install size

Mobile devices typically have far less storage space for installing applications
and data than desktop computers. Minimize the package size by removing unused
assets and libraries.

On Android, the application package is not extracted into separate files when an
app is installed. Instead, assets are decompressed into temporary storage when
they are accessed. To minimize this decompressed asset storage footprint, close
file and URL streams when assets are completely loaded.

## File system access

Different mobile operating systems impose different file system restrictions and
those restrictions tend to be different than those imposed by desktop operating
systems. The appropriate place to save files and data can, therefore, vary from
platform to platform.

One consequence of the variation in file systems is that the shortcuts to common
directories provided by the AIR File class are not always available. The
following table shows which shortcuts can be used on Android and iOS:

|                                  | Android                                 | iOS           |
| -------------------------------- | --------------------------------------- | ------------- |
| File.applicationDirectory        | Read-only through URL (not native path) | Read-only     |
| File.applicationStorageDirectory | Available                               | Available     |
| File.cacheDirectory              | Available                               | Available     |
| File.desktopDirectory            | Root of sdcard                          | Not available |
| File.documentsDirectory          | Root of sdcard                          | Available     |
| File.userDirectory               | Root of sdcard                          | Not available |
| File.createTempDirectory()       | Available                               | Available     |
| File.createTempFile()            | Available                               | Available     |

Apple's guidelines for iOS applications provide specific rules on which storage
locations should be used for files in various situations. For example, one
guideline is that only files that contain user-entered data or data that
otherwise can't be regenerated or re-downloaded should be stored in a directory
that's designated for remote backup. For information on how to comply with
Apple's guidelines for file backup and caching, see
[Controlling file backup and caching](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/WS2f73111e7a180bd0-2c8d6a0213c56230816-8000.html).

## UI components

Adobe has developed a mobile-optimized version of the Flex framework. For more
information, see
[Developing Mobile Applications with Flex and Flash Builder](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/flex/mobileapps/index.html).

Community component projects suitable for mobile applications are also
available. These include:

- Josh Tynjala's
  [Feathers UI controls for Starling](https://feathersui.com/learn/as3-starling/)

- Derrick Grigg's
  [skinnable version of Minimal Comps](https://github.com/dgrigg/SkinnableMinimalComponents)

- Todd Anderson's
  [as3flobile components](https://github.com/bustardcelly/as3flobile)

## Stage 3D accelerated graphics rendering

Starting with AIR 3.2, AIR for mobile supports Stage 3D accelerated graphics
rendering. The
[Stage3D](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/Stage3D.html)
ActionScript APIs are a set of low-level GPU-accelerated APIs enabling advanced
2D and 3D capabilities. These low-level APIs provide developers the flexibility
to leverage GPU hardware acceleration for significant performance gains. You can
also use gaming engines that support the Stage3D ActionScript APIs.

For more information, see
[Gaming engines, 3D, and Stage 3D](https://web.archive.org/web/20140302145731/http://www.adobe.com:80/devnet/games/gaming_engines.html).

## Video smoothing

In order to enhance performance, video smoothing is disabled on AIR.

## Native features

Many mobile platforms provide features that are not yet accessible through the
standard AIR API. As of AIR 3, you can extend AIR with your own native code
libraries. These native extension libraries can access features available from
the operating system or even specific to a given device. Native extensions can
be written in C on iOS, and Java or C on Android. For information on developing
native extensions, see
[Introducing native extensions for Adobe AIR](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/air/extensions/WSb464b1207c184b14-70ccb6bd12937b4f2d6-8000.html).

More Help topics

![](../img/as3LinkIndicator.png) 
[Working with File objects in AIR](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7fe4.html)
