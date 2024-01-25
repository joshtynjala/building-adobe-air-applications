# Defining update settings in an XML configuration file

<div>

The update configuration file is an XML file. It can contain the following
elements:

- `updateURL`— A String. Represents the location of the update descriptor on the
  remote server. Any valid URLRequest location is allowed. You must define the
  `updateURL` property, either via the configuration file or via script (see
  [Defining the update descriptor files and adding the AIR file to your web server](WS3A1F0087-BF77-45ed-B442-E654E5C7E8F1.html)).
  You must define this property before using the updater (before calling the
  `initialize()` method of the updater object, described in
  [Initializing the update framework](WS6C09B923-6464-472e-8EDA-0BAA0A2FFCA1.html)).

- `delay`—A Number. Represents an interval of time given in days (values like
  `0.25` are allowed) for checking for updates. A value of 0 (which is the
  default value) specifies that the updater does not perform an automatic
  periodical check.

The configuration file for the ApplicationUpdaterUI can contain the following
element in addition to the `updateURL` and `delay` elements:

- `defaultUI`: A list of `dialog` elements. Each `dialog` element has a `name`
  attribute that corresponds to dialog box in the user interface. Each `dialog`
  element has a `visible` attribute that defines whether the dialog box is
  visible. The default value is `true`. Possible values for the `name` attribute
  are the following:

  - `"checkForUpdate"`—Corresponding to the Check for Update, No Update, and
    Update Error dialog boxes

  - `"downloadUpdate"`—Corresponding to the Download Update dialog box

  - `"downloadProgress"`—Corresponding to Download Progress and Download Error
    dialog boxes

  - `"installUpdate"`—Corresponding to Install Update dialog box

  - `"fileUpdate"`—Corresponding to File Update, File No Update, and File Error
    dialog boxes

- `"unexpectedError"`—Corresponding to Unexpected Error dialog box

  When set to `false`, the corresponding dialog box does not appear as part of
  the update procedure.

Here is an example of the configuration file for the ApplicationUpdater
framework:

    <?xml version="1.0" encoding="utf-8"?>
    <configuration xmlns="http://ns.adobe.com/air/framework/update/configuration/1.0">
          <url>http://example.com/updates/update.xml</url>
          <delay>1</delay>
    </configuration>

Here is an example of the configuration file for the ApplicationUpdaterUI
framework, which includes a definition for the `defaultUI` element:

    <?xml version="1.0" encoding="utf-8"?>
    <configuration xmlns="http://ns.adobe.com/air/framework/update/configuration/1.0">
          <url>http://example.com/updates/update.xml</url>
          <delay>1</delay>
          <defaultUI>
             <dialog name="checkForUpdate" visible="false" />
             <dialog name="downloadUpdate" visible="false" />
             <dialog name="downloadProgress" visible="false" />
          </defaultUI>
    </configuration>

Point the `configurationFile` property to the location of that file:

ActionScript example:

<div>

    appUpdater.configurationFile = new File("app:/cfg/updateConfig.xml");

JavaScript example:

    appUpdater.configurationFile = new air.File("app:/cfg/updateConfig.xml");

</div>

The templates directory of the update framework includes a sample configuration
file, config-template.xml.

</div>

<div>

<div>



</div>

</div>
