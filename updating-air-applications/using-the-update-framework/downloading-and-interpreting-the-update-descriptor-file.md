# Downloading and interpreting the update descriptor file

The ApplicationUpdater object dispatches the `checkForUpdate` event before the
update process begins, just before the updater tries to download the update
descriptor file. If you cancel the default behavior of the `checkForUpdate`
event, the updater does not download the update descriptor file. You can call
the `checkForUpdate()` method resume the update process:

    appUpdater.checkForUpdate();

Calling the `checkForUpdate()` method causes the updater to asynchronously
download and interpret the update descriptor file. As a result of calling the
`checkForUpdate()` method, the updater object can dispatch the following events:

- `StatusUpdateEvent.UPDATE_STATUS`—The updater has downloaded and interpreted
  the update descriptor file successfully. This event has these properties:

  - `available`—A Boolean value. Set to `true` if there is a different version
    available than the current application; `false` otherwise (the version is
    the same).

  - `version`—A String. The version from the application descriptor file of the
    update file

  - `details`—An Array. If there are no localized versions of the description,
    this array returns an empty string (`""`) as the first element and the
    description as the second element.

    If there are multiple versions of the description (in the update descriptor
    file), the array contains multiple sub-arrays. Each array has two elements:
    the first is a language code (such as `"en"`), and the second is the
    corresponding description (a String) for that language. See
    [Defining the update descriptor files and adding the AIR file to your web server](WS3A1F0087-BF77-45ed-B442-E654E5C7E8F1.html).

- `StatusUpdateErrorEvent.UPDATE_ERROR`—There was an error, and the updater
  could not download or interpret the update descriptor file.
