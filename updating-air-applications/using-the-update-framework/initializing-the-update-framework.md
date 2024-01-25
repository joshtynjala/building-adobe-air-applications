# Initializing the update framework

After setting the configuration properties (see
[Basic example: Using the ApplicationUpdaterUI version](WS96E10DFB-39A5-4488-A666-15B9B46C5EE8.html)),
call the `initialize()` method to initialize the update:

    appUpdater.initialize();

This method does the following:

- It initializes the update framework, silently installing synchronously any
  pending updates. It is required to call this method during application startup
  because it may restart the application when it is called.

- It checks if there is a postponed update and installs it.

- If there is an error during the update process, it clears the update file and
  version information from the application storage area.

- If the delay has expired, it starts the update process. Otherwise it restarts
  the timer.

Calling this method can result in the updater object dispatching the following
events:

- `UpdateEvent.INITIALIZED`—Dispatched when the initialization is complete.

- `ErrorEvent.ERROR`—Dispatched when there is an error during initialization.

Upon dispatching the `UpdateEvent.INITIALIZED` event, the update process is
completed.

When you call the `initialize()` method, the updater starts the update process,
and completes all steps, based on the timer delay setting. However, you can also
start the update process at any time by calling the `checkNow()` method of the
updater object:

    appUpdater.checkNow();

This method does nothing if the update process is already running. Otherwise, it
starts the update process.

The updater object can dispatch the following event as a result of the calling
the `checkNow()` method:

- `UpdateEvent.CHECK_FOR_UPDATE` event just before it attempts to download the
  update descriptor file.

If you cancel the `checkForUpdate` event, you can call the `checkForUpdate()`
method of the updater object. (See the next section.) If you do not cancel the
event, the update process proceeds to check for the update descriptor file.
