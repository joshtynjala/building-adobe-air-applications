# Downloading the update AIR file

The ApplicationUpdater object dispatches the `updateStatus` event after the
updater successfully downloads and interprets the update descriptor file. The
default behavior is to start downloading the update file if it is available. If
you cancel the default behavior, you can call the `downloadUpdate()` method to
resume the update process:

    appUpdater.downloadUpdate();

Calling this method causes the updater to asynchronously download the update
version of the AIR file.

The `downloadUpdate()` method can dispatch the following events:

- `UpdateEvent.DOWNLOAD_START`—The connection to the server was established.
  When using ApplicationUpdaterUI library, this event displays a dialog box with
  a progress bar to track the download progress.

- `ProgressEvent.PROGRESS`—Dispatched periodically as file download progresses.

- `DownloadErrorEvent.DOWNLOAD_ERROR`—Dispatched if there is an error while
  connecting or downloading the update file. It is also dispatched for invalid
  HTTP statuses (such as "404 - File not found"). This event has an `errorID`
  property, an integer defining additional error information. An additional
  `subErrorID` property may contain more error information.

- `UpdateEvent.DOWNLOAD_COMPLETE`—The updater has downloaded and interpreted the
  update descriptor file successfully. If you do not cancel this event, the
  ApplicationUpdater version proceeds to install the update version. In the
  ApplicationUpdaterUI version, the user is presented with a dialog box that
  gives them the option to proceed.
