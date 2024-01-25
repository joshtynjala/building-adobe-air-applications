# Updating the application

<div>

The ApplicationUpdater object dispatches the `downloadComplete` event when the
download of the update file is complete. If you cancel the default behavior, you
can call the `installUpdate()` method to resume the update process:

    appUpdater.installUpdate(file);

Calling this method causes the updater install an update version of the AIR
file. The method includes one parameter, `file`, which is a File object
referencing the AIR file to use as the update.

The ApplicationUpdater object can dispatch the `beforeInstall` event as a result
of calling the `installUpdate()` method:

- `UpdateEvent.BEFORE_INSTALL`—Dispatched just before installing the update.
  Sometimes, it is useful to prevent the installation of the update at this
  time, so that the user can complete current work before the update proceeds.
  Calling the `preventDefault()` method of the Event object postpones the
  installation until the next restart and no additional update process can be
  started. (These include updates that would result by calling the `checkNow()`
  method or because of the periodical check.)

</div>

<div>

<div>



</div>

</div>
