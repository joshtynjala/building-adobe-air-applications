# The update process

<div>

The AIR update framework completes the update process in the following steps:

1.  The updater initialization checks to see if an update check has been
    performed within the defined delay interval (see
    [Configuring the update settings](WS83C043EC-9D2C-4db9-AA1F-352EE2E30892.html)).
    If an update check is due, the update process continues.

2.  The updater downloads and interprets the update descriptor file.

3.  The updater downloads the update AIR file.

4.  The updater installs the updated version of the application.

The updater object dispatches events at the completion of each of these steps.
In the ApplicationUpdater version, you can cancel the events that indicate
successful completion of a step in the process. If you cancel one of these
events, the next step in the process is canceled. In the ApplicationUpdaterUI
version, the updater presents a dialog box allowing the user to cancel or
proceed at each step in the process.

If you cancel the event, you can call methods of the updater object to resume
the process.

As the ApplicationUpdater version of the updater progresses through the update
process, it records its current state, in a `currentState` property. This
property is set to a string with the following possible values:

- `"UNINITIALIZED"`—The updater has not been initialized.

- `"INITIALIZING"`—The updater is initializing.

- `"READY"`—The updater has been initialized

- `"BEFORE_CHECKING"`—The updater has not yet checked for the update descriptor
  file.

- `"CHECKING"`—The updater is checking for an update descriptor file.

- `"AVAILABLE"`—The updater descriptor file is available.

- `"DOWNLOADING"`—The updater is downloading the AIR file.

- `"DOWNLOADED"`—The updater has downloaded the AIR file.

- `"INSTALLING"`—The updater is installing the AIR file.

- `"PENDING_INSTALLING"`—The updater has initialized and there are pending
  updates.

Some methods of the updater object only execute if the updater is in a certain
state.

</div>

<div>

<div>



</div>

</div>
