# Application descriptor changes

The AIR application descriptor has changed in the following AIR releases.

## AIR 1.1 descriptor changes

Allowed application `name` and `description` elements to be localized using the
[`text`](WSfffb011ac560372f-1f98376f1293df83869-7ffa.html) element.

## AIR 1.5 descriptor changes

[`contentType`](WSfffb011ac560372f2fea1812938a6e463-7fd8.html) became a required
child of `fileType`.

## AIR 1.5.3 descriptor changes

Added the [`publisherID`](WS901d38e593cd1bac1e63e3d12939cc14ab-8000.html)
element to allow applications to specify a publisher ID value.

## AIR 2.0 descriptor changes

Added:

- [`aspectRatio`](WSfffb011ac560372f2fea1812938a6e463-7fe6.html)

- [`autoOrients`](WSfffb011ac560372f2fea1812938a6e463-7fe5.html)

- [`fullScreen`](WSfffb011ac560372f2fea1812938a6e463-7fe4.html)

- `image29x29` (see
  [imageNxN](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html))

- `image57x57`

- `image72x72`

- `image512x512`

- [`iPhone`](WSfffb011ac560372f2fea1812938a6e463-7fd6.html)

- [`renderMode`](WSfffb011ac560372f2fea1812938a6e463-7fe3.html)

- [`supportedProfiles`](WSfffb011ac560372f2fea1812938a6e463-7fe2.html)

## AIR 2.5 descriptor changes

Removed: `version`

Added:

- [`android`](WSfffb011ac560372f-6fd06f0f1293d3b33ea-8000.html)

- [`extensionID`](WSfffb011ac560372f2fea1812938a6e463-7fda.html)

- [`extensions`](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffd.html)

- `image36x36` (see
  [imageNxN](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html))

- [`manifestAdditions`](WSfffb011ac560372f33105f2a1293d3d21e0-7ffd.html)

- [`versionLabel`](WSfffb011ac560372f2fea1812938a6e463-7ffa.html)

- [`versionNumber`](WSfffb011ac560372f2fea1812938a6e463-7ffb.html)

## AIR 2.6 descriptor changes

Added:

- `image114x114 (see `[`imageNxN`](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html))

- [`requestedDisplayResolution`](WSfffb011ac560372f-4cb7055d12d779150e8-8000.html)

- [`softKeyboardBehavior`](WSfffb011ac560372f1a6f6f1912d7748050e-7fff.html)

## AIR 3.0 descriptor changes

Added:

- [`colorDepth`](WS54ddc2cc39d08a6245f46ba4132b124f13e-8000.html)

- _direct_ as a valid value for `renderMode`

- [renderMode](WSfffb011ac560372f2fea1812938a6e463-7fe3.html) is no longer
  ignored for desktop platforms

- The Android `<uses-sdk>` element can be specified. (It was previously not
  allowed.)

## AIR 3.1 descriptor changes

Added:

- [Entitlements](WSd6d4f896b3a8801b-3c9d92f81393051c54c-8000.html)

## AIR 3.2 descriptor changes

Added:

- [`depthAndStencil`](WS99d2e2affb7f39bd-2d75e77d134e7ea3560-8000.html)

- [`supportedLanguages`](WS06ac295d95cf5a5c-4601cdc2134337a7308-8000.html)

## AIR 3.3 descriptor changes

Added:

- [`aspectRatio`](WSfffb011ac560372f2fea1812938a6e463-7fe6.html) now includes
  the `ANY` option.

## AIR 3.4 descriptor changes

Added:

- `image50x50 (see `[`imageNxN`](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html)`)`

- `image58x58 (see `[`imageNxN`](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html)`)`

- `image100x100 (see `[`imageNxN`](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html)`)`

- `image1024x1024 (see `[`imageNxN`](WSfffb011ac560372f-6fd06f0f1293d3b33ea-7ffc.html)`)`

## AIR 3.6 descriptor changes

Added:

- [requestedDisplayResolution](WSfffb011ac560372f-4cb7055d12d779150e8-8000.html)
  in [iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html) element now
  includes an `excludeDevices` attribute, allowing you to specify which iOS
  targets use high or standard resolution

- new
  [requestedDisplayResolution](WSfffb011ac560372f-4cb7055d12d779150e8-8000.html)
  element in [initialWindow](WSfffb011ac560372f2fea1812938a6e463-7ff5.html)
  specifies whether to use high or standard resolution on desktop platforms such
  as Macs with high-resolution displays

## AIR 3.7 descriptor changes

Added:

- The [iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html) element now
  provides an [externalSwfs](WS180fc5cb46642d105c891f2413da22fbc8f-8000.html)
  element, which lets you specify a list of SWFs to be loaded at runtime.

- The [iPhone](WSfffb011ac560372f2fea1812938a6e463-7fd6.html) element now
  provides a
  [forceCPURenderModeForDevices](WS180fc5cb46642d10-3a65697f13da2342af2-8000.html)
  element, which lets you force CPU render mode for a specified set of devices.
