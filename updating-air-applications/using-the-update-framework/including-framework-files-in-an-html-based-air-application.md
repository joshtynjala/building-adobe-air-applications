# Including framework files in an HTML-based AIR application

<div>

The frameworks/html directory of the update framework includes these SWF files:

- applicationupdater.swf—Defines the basic functionality of the update library,
  without any user interface

- applicationupdater_ui.swf—Defines the basic functionality of the update
  library, including a user interface that your application can use to display
  update options

JavaScript code in AIR applications can use classes defined in SWF files.

To use the update framework, include either the applicationupdater.swf or
applicationupdater_ui.swf file in your application directory (or a
subdirectory). Then, in the HTML file that will use the framework (in JavaScript
code), include a `script` tag that loads the file:

    <script src="applicationUpdater.swf" type="application/x-shockwave-flash"/>

Or use this `script` tag to load the applicationupdater_ui.swf file:

    <script src="applicationupdater_ui.swf" type="application/x-shockwave-flash"/>

The API defined in these two files is described in the remainder of this
document.

</div>

<div>

<div>



</div>

</div>
