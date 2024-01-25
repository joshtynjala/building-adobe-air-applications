# Packaging a mobile AIR application

Use the ADT -package command to create the application package for an AIR
application intended for a mobile device. The -target parameter specifies the
mobile platform for which the package is created.

#### Android packages

AIR applications on Android use the Android application package format (APK),
rather than the AIR package format.

Packages produced by ADT using the _APK_ target type are in a format that can be
submitted to the Android Market. The Android Market does have requirements that
submitted apps must meet to be accepted. You should review the latest
requirements before creating your final package. See
[Android Developers: Publishing on the Market](http://developer.android.com/guide/publishing/publishing.html).

Unlike iOS applications, you can use a normal AIR code signing certificate to
sign your Android application; however, to submit an app to the Android Market,
the certificate must conform to the Market rules, which require the certificate
to be valid until at least 2033. You can create such a certificate using the ADT
-certificate command.

To submit an app to an alternate market that does not allow your app to require
an AIR download from the Google market, you can specify an alternate download
URL using the `-airDownloadURL` parameter of ADT. When a user who does not have
the required version of the AIR runtime launches your app, they are directed to
the specified URL. See
[ADT package command](WS901d38e593cd1bac1e63e3d128cdca935b-8000.html) for more
information.

By default, ADT packages Android application with shared runtime. So to run the
application, user should install separate AIR runtime on the device.

Note: To force ADT to create an APK that uses captive runtime, use
`target apk-captive-runtime`.

#### iOS packages

AIR applications on iOS use the iOS package format (IPA), rather than the native
AIR format.

Packages produced by ADT using the _ipa-app-store_ target type and the correct
code signing certificate and provisioning profile are in the format that can be
submitted to the Apple App Store. Use the _ipa-ad-hoc_ target type to package an
application for ad hoc distribution.

You must use the correct Apple-issued developer certificate to sign your
application. Different certificates are used for creating test builds than are
used for the final packaging prior to application submission.

For an example of how to package an iOS application using Ant, see
[Piotr Walczyszyn: Packaging AIR application for iOS devices with ADT command and ANT script](http://www.riaspace.com/2011/03/packaging-air-application-for-ios-devices-with-adt-command-and-ant-script/)

- [Packaging with ADT](WS901d38e593cd1bac1e63e3d12994b39ff0-8000.html)
