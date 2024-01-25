# Defining update settings ActionScript or JavaScript code

These configuration parameters can also be set using code in the application, as
in the following:

    appUpdater.updateURL = " http://example.com/updates/update.xml";
    appUpdater.delay = 1;

The properties of the updater object are `updateURL` and `delay`. These
properties define the same settings as the `updateURL` and `delay` elements in
the configuration file: the URL of the update descriptor file and the interval
for checking for updates. If you specify a configuration file _and_ settings in
code, any properties set using code take precedence over corresponding settings
in the configuration file.

You must define the `updateURL` property, either via the configuration file or
via script (see
[Defining the update descriptor files and adding the AIR file to your web server](WS3A1F0087-BF77-45ed-B442-E654E5C7E8F1.html))
before using the updater (before calling the `initialize()` method of the
updater object, described in
[Initializing the update framework](WS6C09B923-6464-472e-8EDA-0BAA0A2FFCA1.html)).

The ApplicationUpdaterUI framework defines these additional properties of the
updater object:

- `isCheckForUpdateVisible`—Corresponding to the Check for Update, No Update,
  and Update Error dialog boxes

- `isDownloadUpdateVisible`—Corresponding to the Download Update dialog box

- `isDownloadProgressVisible`—Corresponding to Download Progress and Download
  Error dialog boxes

- `isInstallUpdateVisible`—Corresponding to Install Update dialog box

- `isFileUpdateVisible`—Corresponding to File Update, File No Update, and File
  Error dialog boxes

- `isUnexpectedErrorVisible`—Corresponding to Unexpected Error dialog box

Each property corresponds to one or more dialog box in the ApplicationUpdaterUI
user interface. Each property is a Boolean value, with a default value of
`true`. When set to `false` the corresponding dialog boxes do not appear as part
of the update procedure.

These dialog box properties override settings in the update configuration file.
