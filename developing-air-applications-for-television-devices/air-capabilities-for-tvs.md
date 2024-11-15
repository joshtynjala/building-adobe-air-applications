# AIR capabilities for TVs

You can create Adobe® AIR® applications for TV devices, such as televisions,
digital video recorders, and Blu-ray players, if the device contains Adobe AIR
for TV. AIR for TV is optimized for TV devices, by using, for example, a
device's hardware accelerators for high performance video and graphics.

AIR applications for TV devices are SWF-based applications, not HTML-based. Your
AIR for TV application can take advantage of hardware acceleration, as well as
other AIR capabilities that are well-suited for the "living room" environment.

## Device profiles

AIR uses profiles to define a target set of devices with similar capabilities.
Use the following profiles for AIR for TV applications:

- The `tv` profile. Use this profile in AIR applications that target an AIR for
  TV device.

- The `extendedTV` profile. Use this profile if your AIR for TV application uses
  native extensions.

The ActionScript capabilities defined for these profiles are covered in
[Device profiles](WS144092a96ffef7cc16ddeea2126bb46b82f-8000.html). Specific
ActionScript differences for AIR for TV applications are noted in the
[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html).

For details about AIR for TV profiles, see
[Supported profiles](WS62b4b4caef5f7931-1f86f0fb1328dba45c2-7fd8.html).

## Hardware acceleration

Television devices provide hardware accelerators that dramatically increase the
performance of graphics and video in your AIR application. To take advantage of
these hardware accelerators, see
[AIR for TV application design considerations](WS62b4b4caef5f7931-1f86f0fb1328dba45c2-7ff7.html).

## Content protection

AIR for TV enables the creation of rich consumer experiences around premium
video content, from Hollywood blockbusters to independent films and TV episodes.
Content providers can create interactive applications using Adobe's tools. They
can integrate Adobe server products into their content distribution
infrastructure or work with one of Adobe's ecosystem partners.

Content protection is a key requirement for the distribution of premium video.
AIR for TV supports Adobe® Flash® Access™, a content protection and monetization
solution that meets the stringent security requirements of content owners,
including the major film studios.

Flash Access supports the following:

- Video streaming and downloading.

- Various business models, including ad-supported, subscription, rental, and
  electronic sell-through.

- Different content-delivery technologies, including HTTP Dynamic Streaming,
  streaming over RTMP (Real Time Media Protocol) using Flash® Media Server, and
  progressive download with HTTP.

AIR for TV also has built-in support for RTMPE, the encrypted version of RTMP,
for existing streaming solutions with lower security requirements. RTMPE and
related SWF verification technologies are supported in Flash Media Server.

For more information, see
[Adobe Flash Access](https://web.archive.org/web/20151102110511/http://www.adobe.com/products/adobe-access.html).

## Multichannel audio

Starting with AIR 3, AIR for TV supports multichannel audio for videos that are
progressively downloaded from an HTTP server. This support includes these
codecs:

- AC-3 (Dolby Digital)

- E-AC-3 (Enhanced Dolby Digital)

- DTS Digital Surround

- DTS Express

- DTS-HD High Resolution Audio

- DTS-HD Master Audio

> **Note:** Support for multichannel audio in videos streamed from an Adobe
> Flash Media Server is not yet available.

## Game input

Starting with AIR 3, AIR for TV supports ActionScript APIs that allow
applications to communicate with attached game input devices, such as joysticks,
gamepads, and wands. Although these devices are called game input devices, any
AIR for TV application, not just games, can use the devices.

A wide range of game input devices with different capabilities are available.
Therefore, the devices are generalized in the API so that an application can
function well with different (and possibly unknown) types of game input devices.

The GameInput class is the entry point into the game input ActionScript APIs.
For more information, see
[GameInput](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/ui/GameInput.html).

## Stage 3D accelerated graphics rendering

Starting with AIR 3, AIR for TV supports Stage 3D accelerated graphics
rendering. The
[Stage3D](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/Stage3D.html)
ActionScript APIs are a set of low-level GPU-accelerated APIs enabling advanced
2D and 3D capabilities. These low-level APIs provide developers the flexibility
to leverage GPU hardware acceleration for significant performance gains. You can
also use gaming engines that support the Stage3D ActionScript APIs.

For more information, see
[Gaming engines, 3D, and Stage 3D](https://web.archive.org/web/20140302145731/http://www.adobe.com:80/devnet/games/gaming_engines.html).

## Native extensions

When your application targets the `extendedTV` profile, it can use ANE (AIR
native extension) packages.

Typically, a device manufacturer provides ANE packages to provide access to
device features not otherwise supported by AIR. For example, a native extension
could allow you to change channels on a television or pause playback on a video
player.

When you package an AIR for TV application that uses ANE packages, you package
the application into an AIRN file instead of an AIR file.

Native extensions for AIR for TV devices are always _device-bundled_ native
extensions. Device-bundled means that the extension libraries are installed on
the AIR for TV device. The ANE package you include in your application package
_never_ includes the extension's native libraries. Sometime it contains an
ActionScript-only version of the native extension. This ActionScript-only
version is a stub or simulator of the extension. The device manufacturer
installs the real extension, including the native libraries, on the device.

If you are developing native extensions, note the following:

- Always consult the device manufacturer if you are creating an AIR for TV
  native extension for their devices.

- On some AIR for TV devices, only the device manufacturer creates native
  extensions.

- On all AIR for TV devices, the device manufacturer decides which native
  extensions to install.

- Development tools for building AIR for TV native extensions vary by
  manufacturer.

For more information about using native extensions in your AIR application, see
[Using native extensions for Adobe AIR](WS597e5dadb9cc1e0253f7d2fc1311b491071-8000.html).

For information about creating native extensions, see
[Developing Native Extensions for Adobe AIR](https://web.archive.org/web/20150414032840/https://help.adobe.com/en_US/air/extensions/index.html).
