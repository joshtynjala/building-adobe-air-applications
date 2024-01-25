# Installing from an arbitrary AIR file

You can call the `installFromAIRFile()` method to install the update version to
install from an AIR file on the user's computer:

    appUpdater.installFromAIRFile();

This method causes the updater to install an update version the application from
the AIR file.

The `installFromAIRFile()` method can dispatch the following events:

- `StatusFileUpdateEvent.FILE_UPDATE_STATUS`—Dispatched after the
  ApplicationUpdater successfully validated the file sent using the
  `installFromAIRFile()` method. This event has the following properties:

  - `available`—Set to `true` if there is a different version available than one
    of the current application; `false` otherwise (the versions are the same).

  - `version` —The string representing the new available version.

  - `path`—Represents the native path of the update file.

  You can cancel this event if the available property of the
  StatusFileUpdateEvent object is set to `true`. Canceling the event cancels the
  update from proceeding. Call the `installUpdate()` method to continue the
  canceled update.

- `StatusFileUpdateErrorEvent.FILE_UPDATE_ERROR`—There was an error, and the
  updater could not install the AIR application.
