# AIR.SWF in-browser API

<div>

</div>

<div>

## Customizing the seamless install badge.swf

<div>

In addition to using the badge.swf file provided with the SDK, you can create
your own SWF file for use in a browser page. Your custom SWF file can interact
with the runtime in the following ways:

- It can install an AIR application. See
  [Installing an AIR application from the browser](WS5b3ccc516d4fbf351e63e3d118666ade46-7c97.html).

- It can check to see if a specific AIR application is installed. See
  [Checking from a web page if an AIR application is installed](WS5b3ccc516d4fbf351e63e3d118666ade46-7c85.html).

- It can check to see if the runtime is installed. See
  [Checking if the runtime is installed](WS5b3ccc516d4fbf351e63e3d118666ade46-7c98.html).

- It can launch an installed AIR application on the user’s system. See
  [Launching an installed AIR application from the browser](WS5b3ccc516d4fbf351e63e3d118666ade46-7cd2.html).

These capabilities are all provided by calling APIs in a SWF file hosted at
adobe.com: air.swf. You can customize the badge.swf file and call the air.swf
APIs from your own SWF file.

Additionally, a SWF file running in the browser can communicate with a running
AIR application by using the LocalConnection class. For more information, see
[Communicating with other Flash Player and AIR instances](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7c7e.html)
(for ActionScript developers) or
[Communicating with other Flash Player and AIR instances](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7c7e.html)
(for HTML developers).

<div>

Important: The features described in this section (and the APIs in the air.swf
file) require the end user to have Adobe® Flash® Player 9 update 3, or later,
installed in the web browser on Windows or Mac OS. On Linux, the seamless
install feature requires Flash Player 10 (version 10,0,12,36 or later). You can
write code to check the installed version of Flash Player and provide an
alternate interface to the user if the required version of Flash Player is not
installed. For example, if an older version of Flash Player is installed, you
could provide a link to the download version of the AIR file (instead of using
the badge.swf file or the air.swf API to install an application).

</div>

</div>

</div>

<div>

## Using the badge.swf file to install an AIR application

<div>

Included in the AIR SDK and the Flex SDK is a badge.swf file which lets you
easily use the seamless install feature. The badge.swf can install the runtime
and an AIR application from a link in a web page. The badge.swf file and its
source code are provided to you for distribution on your website.

<div>

#### Embed the badge.swf file in a web page

1.  Locate the following files, provided in the samples/badge directory of the
    AIR SDK or the Flex SDK, and add them to your web server.

    - badge.swf

    - default_badge.html

    - AC_RunActiveContent.js

2.  Open the default_badge.html page in a text editor.

3.  In the default_badge.html page, in the `AC_FL_RunContent()` JavaScript
    function, adjust the `FlashVars` parameter definitions for the following:

    <div>

    | Parameter      | Description                                                                                                                              |
    | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
    | `appname`      | The name of the application, displayed by the SWF file when the runtime is not installed.                                                |
    | `appurl`       | (Required). The URL of the AIR file to be downloaded. You must use an absolute, not relative, URL.                                       |
    | `airversion`   | (Required). For the 1.0 version of the runtime, set this to 1.0.                                                                         |
    | `imageurl`     | The URL of the image (optional) to display in the badge.                                                                                 |
    | `buttoncolor`  | The color of the download button (specified as a hex value, such as `FFCC00`).                                                           |
    | `messagecolor` | The color of the text message displayed below the button when the runtime is not installed (specified as a hex value, such as `FFCC00`). |

    </div>

4.  The minimum size of the badge.swf file is 217 pixels wide by 180 pixels
    high. Adjust the values of the `width` and `height` parameters of the
    `AC_FL_RunContent()` function to suit your needs.

5.  Rename the default_badge.html file and adjust its code (or include it in
    another HTML page) to suit your needs.

<div>

<div>

Note: For the HTML `embed` tag that loads the badge.swf file, do not set the
`wmode` attribute; leave it set to the default setting (`"window"`). Other
`wmode` settings will prevent installation on some systems. Also, using other
`wmode` settings produces an error: “Error \#2044: Unhandled ErrorEvent:.
text=Error \#2074: The stage is too small to fit the download ui.”

</div>

</div>

You can also edit and recompile the badge.swf file. For details, see
[Modify the badge.swf file](WS5b3ccc516d4fbf351e63e3d118666ade46-7c7d.html).

</div>

</div>

<div>

### Install the AIR application from a seamless install link in a web page

<div>

Once you have added the seamless install link to a page, the user can install
the AIR application by clicking the link in the SWF file.

1.  Navigate to the HTML page in a web browser that has Flash Player (version 9
    update 3 or later on Windows and Mac OS, or version 10 on Linux) installed.

2.  In the web page, click the link in the badge.swf file.

    - If you have installed the runtime, skip to the next step.

    - If you have not installed the runtime, a dialog box is displayed asking
      whether you would like to install it. Install the runtime (see
      [Adobe AIR installation](WS5b3ccc516d4fbf351e63e3d118666ade46-7fdf.html)),
      and then proceed with the next step.

3.  In the Installation window, leave the default settings selected, and then
    click Continue.

    On a Windows computer, AIR automatically does the following:

    - Installs the application into c:\Program Files\\

    - Creates a desktop shortcut for application

    - Creates a Start Menu shortcut

    - Adds an entry for application in the Add/Remove Programs Control Panel

    On Mac OS, the installer adds the application to the Applications directory
    (for example, in the /Applications directory in Mac OS).

    On a Linux computer, AIR automatically does the following:

    - Installs the application into /opt.

    - Creates a desktop shortcut for application

    - Creates a Start Menu shortcut

    - Adds an entry for application in the system package manager

4.  Select the options you want, and then click the Install button.

5.  When the installation is complete, click Finish.

</div>

</div>

<div>

### Modify the badge.swf file

<div>

The Flex SDK and AIR SDK provides the source files for the badge.swf file. These
files are included in the samples/badge folder of the SDK:

<div>

| Source files | Description                                                                                                                                    |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| badge.fla    | The source Flash file used to compile the badge.swf file. The badge.fla file compiles into a SWF 9 file (which can be loaded in Flash Player). |
| AIRBadge.as  | An ActionScript 3.0 class that defines the base class used in the basdge.fla file.                                                             |

</div>

You can use Flash Professional to redesign the visual interface of the badge.fla
file.

The `AIRBadge()` constructor function, defined in the AIRBadge class, loads the
air.swf file hosted at http://airdownload.adobe.com/air/browserapi/air.swf. The
air.swf file includes code for using the seamless install feature.

The `onInit()` method (in the AIRBadge class) is invoked when the air.swf file
is loaded successfully:

    private function onInit(e:Event):void {
        _air = e.target.content;
        switch (_air.getStatus()) {
            case "installed" :
                root.statusMessage.text = "";
                break;
            case "available" :
                if (_appName && _appName.length > 0) {
                    root.statusMessage.htmlText = "<p align='center'><font color='#"
                            + _messageColor + "'>In order to run " + _appName +
                            ", this installer will also set up Adobe® AIR®.</font></p>";
                } else {
                    root.statusMessage.htmlText = "<p align='center'><font color='#"
                            + _messageColor + "'>In order to run this application, "
                            + "this installer will also set up Adobe® AIR®.</font></p>";
                }
                break;
            case "unavailable" :
                root.statusMessage.htmlText = "<p align='center'><font color='#"
                            + _messageColor
                            + "'>Adobe® AIR® is not available for your system.</font></p>";
                root.buttonBg_mc.enabled = false;
                break;
        }
    }

The code sets the global `_air` variable to the main class of the loaded air.swf
file. This class includes the following public methods, which the badge.swf file
accesses to call seamless install functionality:

<div>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Method</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><samp>getStatus()</samp></p></td>
<td><div>
Determines whether the runtime is installed (or can be installed) on the
computer. For details, see <a
href="WS5b3ccc516d4fbf351e63e3d118666ade46-7c98.html">Checking if the
runtime is installed</a>.
<ul class="incremental">
<li><p><samp>runtimeVersion</samp>—A string indicating the version of
the runtime (such as <samp>"1.0.M6"</samp>) required by the application
to be installed.</p></li>
</ul>
</div></td>
</tr>
<tr class="even">
<td><p><samp>installApplication()</samp></p></td>
<td><p>Installs the specified application on the user’s machine. For
details, see <a
href="WS5b3ccc516d4fbf351e63e3d118666ade46-7c97.html">Installing an AIR
application from the browser</a>.</p>
<div>
<ul class="incremental">
<li><p><samp>url</samp>—A string defining the URL. You must use an
absolute, not relative, URL path.</p></li>
<li><p><samp>runtimeVersion</samp>—A string indicating the version of
the runtime (such as <samp>"2.5"</samp>) required by the application to
be installed.</p></li>
<li><p><samp>arguments</samp>— Arguments to be passed to the application
if it is launched upon installation. The application is launched upon
installation if the <samp>allowBrowserInvocation</samp> element is set
to <samp>true</samp> in the application descriptor file. (For more
information on the application descriptor file, see <a
href="WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html">AIR application
descriptor files</a>.) If the application is launched as the result of a
seamless install from the browser (with the user choosing to launch upon
installation), the application’s NativeApplication object dispatches a
BrowserInvokeEvent object only if arguments are passed. Consider the
security implications of data that you pass to the application. For
details, see <a
href="WS5b3ccc516d4fbf351e63e3d118666ade46-7cd2.html">Launching an
installed AIR application from the browser</a>.</p></li>
</ul>
</div></td>
</tr>
</tbody>
</table>

</div>

The settings for `url` and `runtimeVersion` are passed into the SWF file via the
FlashVars settings in the container HTML page.

If the application starts automatically upon installation, you can use
LocalConnection communication to have the installed application contact the
badge.swf file upon invocation. For more information, see
[Communicating with other Flash Player and AIR instances](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7c7e.html)
(for ActionScript developers) or
[Communicating with other Flash Player and AIR instances](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7c7e.html)
(for HTML developers).

You may also call the `getApplicationVersion()` method of the air.swf file to
check if an application is installed. You can call this method either before the
application installation process or after the installation is started. For
details, see
[Checking from a web page if an AIR application is installed](WS5b3ccc516d4fbf351e63e3d118666ade46-7c85.html).

</div>

</div>

</div>

<div>

## Loading the air.swf file

<div>

You can create your own SWF file that uses the APIs in the air.swf file to
interact with the runtime and AIR applications from a web page in a browser. The
air.swf file is hosted at http://airdownload.adobe.com/air/browserapi/air.swf.
To reference the air.swf APIs from your SWF file, load the air.swf file into the
same application domain as your SWF file. The following code shows an example of
loading the air.swf file into the application domain of the loading SWF file:

    var airSWF:Object; // This is the reference to the main class of air.swf
    var airSWFLoader:Loader = new Loader(); // Used to load the SWF
    var loaderContext:LoaderContext = new LoaderContext();
                                    // Used to set the application domain

    loaderContext.applicationDomain = ApplicationDomain.currentDomain;

    airSWFLoader.contentLoaderInfo.addEventListener(Event.INIT, onInit);
    airSWFLoader.load(new URLRequest("http://airdownload.adobe.com/air/browserapi/air.swf"),
                        loaderContext);

    function onInit(e:Event):void
    {
        airSWF = e.target.content;
    }

Once the air.swf file is loaded (when the Loader object’s `contentLoaderInfo`
object dispatches the `init` event), you can call any of the air.swf APIs,
described in the sections that follow.

<div>

Note: The badge.swf file, provided with the AIR SDK and the Flex SDK,
automatically loads the air.swf file. See
[Using the badge.swf file to install an AIR application](WS5b3ccc516d4fbf351e63e3d118666ade46-7c88.html).
The instructions in this section apply to creating your own SWF file that loads
the air.swf file.

</div>

</div>

</div>

<div>

## Checking if the runtime is installed

<div>

A SWF file can check if the runtime is installed by calling the `getStatus(`)
method in the air.swf file loaded from
http://airdownload.adobe.com/air/browserapi/air.swf. For details, see
[Loading the air.swf file](WS5b3ccc516d4fbf351e63e3d118666ade46-7c87.html).

Once the air.swf file is loaded, the SWF file can call the air.swf file’s
`getStatus(`) method as in the following:

    var status:String = airSWF.getStatus();

The `getStatus()` method returns one of the following string values, based on
the status of the runtime on the computer:

<div>

| String value    | Description                                                                      |
| --------------- | -------------------------------------------------------------------------------- |
| `"available"`   | The runtime can be installed on this computer but currently it is not installed. |
| `"unavailable"` | The runtime cannot be installed on this computer.                                |
| `"installed"`   | The runtime is installed on this computer.                                       |

</div>

The `getStatus()` method throws an error if the required version of Flash Player
(version 9 update 3 or later on Windows and Mac OS, or version 10 on Linux) is
not installed in the browser.

</div>

</div>

<div>

## Checking from a web page if an AIR application is installed

<div>

A SWF file can check if an AIR application (with a matching application ID and
publisher ID) is installed by calling the `getApplicationVersion(`) method in
the air.swf file loaded from
http://airdownload.adobe.com/air/browserapi/air.swf. For details, see
[Loading the air.swf file](WS5b3ccc516d4fbf351e63e3d118666ade46-7c87.html).

Once the air.swf file is loaded, the SWF file can call the air.swf file’s
`getApplicationVersion(`) method as in the following:

    var appID:String = "com.example.air.myTestApplication";
    var pubID:String = "02D88EEED35F84C264A183921344EEA353A629FD.1";
    airSWF.getApplicationVersion(appID, pubID, versionDetectCallback);

    function versionDetectCallback(version:String):void
    {
        if (version == null)
        {
            trace("Not installed.");
            // Take appropriate actions. For instance, present the user with
            // an option to install the application.
        }
        else
        {
            trace("Version", version, "installed.");
            // Take appropriate actions. For instance, enable the
            // user interface to launch the application.
        }
    }

The `getApplicationVersion()` method has the following parameters:

<div>

| Parameters | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `appID`    | The application ID for the application. For details, see [id](WSfffb011ac560372f2fea1812938a6e463-7ffe.html).                                                                                                                                                                                                                                                                                                                                                                                 |
| `pubID`    | The publisher ID for the application. For details, see [publisherID](WS901d38e593cd1bac1e63e3d12939cc14ab-8000.html). If the application in question does not have a publisher ID, set the `pubID` parameter to an empty string (“”).                                                                                                                                                                                                                                                         |
| `callback` | A callback function to serve as the handler function. The getApplicationVersion() method operates asynchronously, and upon detecting the installed version (or lack of an installed version), this callback method is invoked. The callback method definition must include one parameter, a string, which is set to the version string of the installed application. If the application is not installed, a null value is passed to the function, as illustrated in the previous code sample. |

</div>

The `getApplicationVersion()` method throws an error if the required version of
Flash Player (version 9 update 3 or later on Windows and Mac OS, or version 10
on Linux) is not installed in the browser.

<div>

Note: As of AIR 1.5.3, the publisher ID is deprecated. Publisher IDs are no
longer assigned to an application automatically. For backward compatibility,
applications can continue to specify a publisher ID.

</div>

</div>

</div>

<div>

## Installing an AIR application from the browser

<div>

A SWF file can install an AIR application by calling the `installApplication(`)
method in the air.swf file loaded from
`http://airdownload.adobe.com/air/browserapi/air.swf`. For details, see
[Loading the air.swf file](WS5b3ccc516d4fbf351e63e3d118666ade46-7c87.html).

Once the air.swf file is loaded, the SWF file can call the air.swf file’s
`installApplication(`) method, as in the following code:

    var url:String = "http://www.example.com/myApplication.air";
    var runtimeVersion:String = "1.0";
    var arguments:Array = ["launchFromBrowser"]; // Optional
    airSWF.installApplication(url, runtimeVersion, arguments);

The `installApplication()` method installs the specified application on the
user’s machine. This method has the following parameters:

<div>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><samp>url</samp></p></td>
<td><p>A string defining the URL of the AIR file to install. You must
use an absolute, not relative, URL path.</p></td>
</tr>
<tr class="even">
<td><p><samp>runtimeVersion</samp></p></td>
<td><p>A string indicating the version of the runtime (such as "1.0")
required by the application to be installed.</p></td>
</tr>
<tr class="odd">
<td><p><samp>arguments</samp></p></td>
<td><p>An array of arguments to be passed to the application if it is
launched upon installation. Only alphanumerical characters are
recognized in the arguments. If you need to pass other values, consider
using an encoding scheme.</p>
<p>The application is launched upon installation if the
<samp>allowBrowserInvocation</samp> element is set to <samp>true</samp>
in the application descriptor file. (For more information on the
application descriptor file, see <a
href="WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html">AIR application
descriptor files</a>.) If the application is launched as the result of a
seamless install from the browser (with the user choosing to launch upon
installation), the application’s NativeApplication object dispatches a
BrowserInvokeEvent object only if arguments have been passed. For
details, see <a
href="WS5b3ccc516d4fbf351e63e3d118666ade46-7cd2.html">Launching an
installed AIR application from the browser</a>.</p></td>
</tr>
</tbody>
</table>

</div>

The `installApplication()` method can only operate when called in the event
handler for a user event, such as a mouse click.

The `installApplication()` method throws an error if the required version of
Flash Player (version 9 update 3 or later on Windows and Mac OS, or version 10
on Linux) is not installed in the browser.

On Mac OS, to install an updated version of an application, the user must have
adequate system privileges to install to the application directory (and
administrative privileges if the application updates the runtime). On Windows, a
user must have administrative privileges.

You may also call the `getApplicationVersion()` method of the air.swf file to
check if an application is already installed. You can call this method either
before the application installation process begins or after the installation is
started. For details, see
[Checking from a web page if an AIR application is installed](WS5b3ccc516d4fbf351e63e3d118666ade46-7c85.html).
Once the application is running, it can communicate with the SWF content in the
browser by using the LocalConnection class. For more information, see
[Communicating with other Flash Player and AIR instances](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7c7e.html)
(for ActionScript developers) or
[Communicating with other Flash Player and AIR instances](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7c7e.html)
(for HTML developers).

</div>

</div>

<div>

## Launching an installed AIR application from the browser

<div>

To use the browser invocation feature (allowing it to be launched from the
browser), the application descriptor file of the target application must include
the following setting:

    <allowBrowserInvocation>true</allowBrowserInvocation>

For more information on the application descriptor file, see
[AIR application descriptor files](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html).

A SWF file in the browser can launch an AIR application by calling the
`launchApplication(`) method in the air.swf file loaded from
http://airdownload.adobe.com/air/browserapi/air.swf. For details, see
[Loading the air.swf file](WS5b3ccc516d4fbf351e63e3d118666ade46-7c87.html).

Once the air.swf file is loaded, the SWF file can call the air.swf file’s
`launchApplication(`) method, as in the following code:

    var appID:String = "com.example.air.myTestApplication";
    var pubID:String = "02D88EEED35F84C264A183921344EEA353A629FD.1";
    var arguments:Array = ["launchFromBrowser"]; // Optional
    airSWF.launchApplication(appID, pubID, arguments);

The `launchApplication()` method is defined at the top level of the air.swf file
(which is loaded in the application domain of the user interface SWF file).
Calling this method causes AIR to launch the specified application (if it is
installed and browser invocation is allowed, via the `allowBrowserInvocation`
setting in the application descriptor file). The method has the following
parameters:

<div>

| Parameter   | Description                                                                                                                                                                                                                                                                                                                    |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `appID`     | The application ID for the application to launch. For details, see [id](WSfffb011ac560372f2fea1812938a6e463-7ffe.html).                                                                                                                                                                                                        |
| `pubID`     | The publisher ID for the application to launch. For details, see [publisherID](WS901d38e593cd1bac1e63e3d12939cc14ab-8000.html). If the application in question does not have a publisher ID, set the `pubID` parameter to an empty string (“”)                                                                                 |
| `arguments` | An array of arguments to pass to the application. The NativeApplication object of the application dispatches a BrowserInvokeEvent event that has an arguments property set to this array. Only alphanumerical characters are recognized in the arguments. If you need to pass other values, consider using an encoding scheme. |

</div>

The `launchApplication()` method can only operate when called in the event
handler for a user event, such as a mouse click.

The `launchApplication()` method throws an error if the required version of
Flash Player (version 9 update 3 or later on Windows and Mac OS, or version 10
on Linux) is not installed in the browser.

If the `allowBrowserInvocation` element is set to `false` in the application
descriptor file, calling the `launchApplication()` method has no effect.

Before presenting the user interface to launch the application, you may want to
call the `getApplicationVersion(`) method in the air.swf file. For details, see
[Checking from a web page if an AIR application is installed](WS5b3ccc516d4fbf351e63e3d118666ade46-7c85.html).

When the application is invoked via the browser invocation feature, the
application’s NativeApplication object dispatches a BrowserInvokeEvent object.
For details, see
[Invoking an AIR application from the browser](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118676a5d46-8000.html#WS5b3ccc516d4fbf351e63e3d118666ade46-7e19)
(for ActionScript developers) or
[Invoking an AIR application from the browser](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118676a5d46-8000.html#WS5b3ccc516d4fbf351e63e3d118666ade46-7e19)
(for HTML developers).

If you use the browser invocation feature, be sure to consider security
implications. These implications are described in
[Invoking an AIR application from the browser](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118676a5d46-8000.html#WS5b3ccc516d4fbf351e63e3d118666ade46-7e19)
(for ActionScript developers) and
[Invoking an AIR application from the browser](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118676a5d46-8000.html#WS5b3ccc516d4fbf351e63e3d118666ade46-7e19)
(for HTML developers).

Once the application is running, it can communicate with the SWF content in the
browser by using the LocalConnection class. For more information, see
[Communicating with other Flash Player and AIR instances](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7c7e.html)
(for ActionScript developers) or
[Communicating with other Flash Player and AIR instances](http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7c7e.html)
(for HTML developers).

<div>

Note: As of AIR 1.5.3, the publisher ID is deprecated. Publisher IDs are no
longer assigned to an application automatically. For backward compatibility,
applications can continue to specify a publisher ID.

</div>

</div>

</div>

<div>

<div>



</div>

</div>
