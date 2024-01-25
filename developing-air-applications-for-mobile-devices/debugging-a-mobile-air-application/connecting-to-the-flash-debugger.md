# Connecting to the Flash debugger

To debug an application running on a mobile device, you can run the Flash
debugger on your development computer and connect to it over the network. To
enable remote debugging, you must do the following:

- On Android, specify the android:permission.INTERNET permission in the
  application descriptor.

- Compile the application SWFs with debugging enabled.

- Package the application with the `-target apk-debug, for Android,`or
  `-target ipa-debug`, for iOS, and either the `-connect` (wifi debugging) or
  `-listen` (USB debugging) flag.

For remote debugging over wifi, the device must be able to access TCP port 7935
of the computer running the Flash debugger by IP address or fully qualified
domain name. For remote debugging over USB, the device must be able to access
TCP port 7936 or the port specified in the `-listen` flag.

For iOS, you can also specify `-target ipa-debug-interpreter` or
`-target ipa-debug-interpreter-simulator`.

More Help topics

[Remote debugging with Flash Professional](WSd106d9f573d8da23-dcd13bd12a7d944d0b-8000.html)

[Remote debugging with FDB over a network connection](WSd106d9f573d8da23-dcd13bd12a7d944d0b-7ffe.html)

[Remote debugging with FDB over USB](WS901d38e593cd1bac7b2281cc12cd6bced97-8000.html)
