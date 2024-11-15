# Creating your first desktop Flex AIR application in Flash Builder

For a quick, hands-on illustration of how Adobe® AIR® works, use these
instructions to create and package a simple SWF file-based AIR "Hello World"
application using Adobe® Flash® Builder.

If you haven't already done so, download and install Flash Builder. Also,
download and install the most recent version of the Adobe AIR SDK, which is
located here: [airsdk.harman.com](https://airsdk.harman.com/).

## Create an AIR project

Flash Builder includes tools to develop and package AIR applications.

You begin to create AIR applications in Flash Builder or Flex Builder in the
same way that you create other Flex-based application projects: by defining a
new project.

1.  Open Flash Builder.

2.  Select File \> New \> Flex Project.

3.  Enter the project name as AIRHelloWorld.

4.  In Flex, AIR applications are considered an application type. You have two
    type options:

    - a web application that runs in Adobe® Flash® Player

    - a desktop application that runs in Adobe AIR

    Select Desktop as the application type.

5.  Click Finish to create the project.

AIR projects initially consist of two files: the main MXML file and an
application XML file (known as the application descriptor file). The latter file
specifies application properties.

For more information, see
[Developing AIR applications with Flash Builder](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/Flex/4.0/UsingFlashBuilder/WS6b84a753ecd210fd-7fb8a08d12114b6a4cf-8000.html).

## Write the AIR application code

To write the "Hello World" application code, you edit the application MXML file
(AIRHelloWorld.mxml), which is open in the editor. (If the file isn't open, use
the Project Navigator to open the file.)

Flex AIR applications on the desktop are contained within the MXML
WindowedApplication tag. The MXML WindowedApplication tag creates a simple
window that includes basic window controls such as a title bar and close button.

1.  Add a `title` attribute to the WindowedApplication component, and assign it
    the value `"Hello World"`:

        <?xml version="1.0" encoding="utf-8"?>
        <s:WindowedApplication xmlns:fx="http://ns.adobe.com/mxml/2009"
                               xmlns:s="library://ns.adobe.com/flex/spark"
                               xmlns:mx="library://ns.adobe.com/flex/mx"
                               title="Hello World">
        </s:WindowedApplication>

2.  Add a Label component to the application (place it inside the
    WindowedApplication tag). Set the `text` property of the Label component to
    `"Hello AIR"`, and set the layout constraints to keep it centered, as shown
    here:

        <?xml version="1.0" encoding="utf-8"?>
        <s:WindowedApplication xmlns:fx="http://ns.adobe.com/mxml/2009"
                               xmlns:s="library://ns.adobe.com/flex/spark"
                               xmlns:mx="library://ns.adobe.com/flex/mx"
                               title="Hello World">

            <s:Label text="Hello AIR" horizontalCenter="0" verticalCenter="0"/>
        </s:WindowedApplication>

3.  Add the following style block immediately after the opening
    WindowedApplication tag and before the label component tag you just entered:

        <fx:Style>
            @namespace s "library://ns.adobe.com/flex/spark";
            s|WindowedApplication
            {

        skinClass:ClassReference("spark.skins.spark.SparkChromeWindowedApplicationSkin");
                background-color:#999999;
                background-alpha:"0.7";
            }
        </fx:Style>

These style settings apply to the entire application and render the window
background a slightly transparent gray.

The application code now looks like the following:

    <?xml version="1.0" encoding="utf-8"?>
    <s:WindowedApplication xmlns:fx="http://ns.adobe.com/mxml/2009"
                           xmlns:s="library://ns.adobe.com/flex/spark"
                           xmlns:mx="library://ns.adobe.com/flex/mx"
                           title="Hello World">

        <fx:Style>
            @namespace s "library://ns.adobe.com/flex/spark";
            s|WindowedApplication
            {

    skinClass:ClassReference("spark.skins.spark.SparkChromeWindowedApplicationSkin");
                background-color:#999999;
                background-alpha:"0.7";
            }
        </fx:Style>

        <s:Label text="Hello AIR" horizontalCenter="0" verticalCenter="0"/>
    </s:WindowedApplication>

Next, you will change some settings in the application descriptor to allow the
application to be transparent:

1.  In the Flex Navigator pane, locate the application descriptor file in the
    source directory of the project. If you named your project AIRHelloWorld,
    this file is named AIRHelloWorld-app.xml.

2.  Double-click the application descriptor file to edit it in Flash Builder.

3.  In the XML code, locate the commented lines for the `systemChrome` and
    `transparent` properties (of the `initialWindow` property). Remove the
    comments. (Remove the `"<!--"` and `"-->"` comment delimiters.)

4.  Set the text value of the `systemChrome` property to `none`, as in the
    following:

        <systemChrome>none</systemChrome>

5.  Set the text value of the `transparent` property to `true`, as in the
    following:

        <transparent>true</transparent>

6.  Save the file.

## Test the AIR application

To test the application code that you've written, run it in debug mode.

1.  Click the Debug button ![](../img/FlexBuilderDebugIcon1.png) in the main
    toolbar.

    You can also select the Run \> Debug \> AIRHelloWorld command.

    The resulting AIR application should look like the following example:

    ![](../img/HelloWorldApolloScreenshot.png)

2.  Using the `horizontalCenter` and `verticalCenter` properties of the Label
    control, the text is placed in the center of the window. Move or resize the
    window as you would any other desktop application.

> **Note:** If the application does not compile, fix any syntax or spelling
> errors that you inadvertently entered into the code. Errors and warnings are
> displayed in the Problems view in Flash Builder.

## Package, sign, and run your AIR application

You are now ready to package the "Hello World" application into an AIR file for
distribution. An AIR file is an archive file that contains the application
files, which are all of the files contained in the project's bin folder. In this
simple example, those files are the SWF and application XML files. You
distribute the AIR package to users who then use it to install the application.
A required step in this process is to digitally sign it.

1.  Ensure that the application has no compilation errors and runs as expected.

2.  Select Project \> Export Release Build.

3.  Check that the AIRHelloWorld project and AIRHelloWorld.mxml application are
    listed for project and application.

4.  Select Export as signed AIR package option. Then click Next.

5.  If you have an existing digital certificate, click Browse to locate and
    select it.

6.  If you must create a new self-signed digital certificate, select Create.

7.  Enter the required information and click OK.

8.  Click Finish to generate the AIR package, which is named AIRHelloWorld.air.

You can now install and run the application from the Project Navigator in Flash
Builder or from the file system by double-clicking the AIR file.
