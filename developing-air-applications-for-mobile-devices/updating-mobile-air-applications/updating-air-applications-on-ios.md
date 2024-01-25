# Updating AIR applications on iOS

For AIR apps distributed through the iTunes app store, you can update an app by
submitting the update to the store as long as the following are all true (these
policies are enforced by the Apple app store, not by AIR):

- The code signing certificate and provisioning profiles are issued to the same
  Apple ID

- The IPA package uses the same Apple Bundle ID

- The update does not decrease the pool of supported devices (in other words, if
  your original application supports devices running iOS 3, then you cannot
  create an update that drops support for iOS 3).

Important: Because the AIR SDK versions 2.6 and later do not support iOS 3, and
AIR 2 does, you cannot update published iOS applications that were developed
using AIR 2 with an update developed using AIR 2.6+.
