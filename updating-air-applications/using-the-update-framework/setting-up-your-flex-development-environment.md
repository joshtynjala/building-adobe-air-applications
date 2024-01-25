# Setting up your Flex development environment

<div>

The SWC files in the frameworks/libs/air directory of the AIR 2 SDK define
classes that you can use in Flex and Flash development.

To use the update framework when compiling with the Flex SDK, include either the
ApplicationUpdater.swc or ApplicationUpdater_UI.swc file in the call to the
amxmlc compiler. In the following, example, the compiler loads the
ApplicationUpdater.swc file in the lib subdirectory of the Flex SDK directory:

    amxmlc -library-path+=lib/ApplicationUpdater.swc  -- myApp.mxml

The following example, the compiler loads the ApplicationUpdater_UI.swc file in
the lib subdirectory of the Flex SDK directory:

    amxmlc -library-path+=lib/ApplicationUpdater_UI.swc  -- myApp.mxml

When developing using Flash Builder, add the SWC file in the Library Path tab of
the Flex Build Path settings in the Properties dialog box.

Be sure to copy the SWC files to the directory that you will reference in the
amxmlc compiler (using Flex SDK) or Flash Builder.

</div>

<div>

<div>



</div>

</div>
