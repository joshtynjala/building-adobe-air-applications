# Instantiating an updater object

<div>

After loading the AIR update framework in your code (see
[Setting up your Flex development environment](WS01EC1957-C9FB-484d-9AA4-D7293468133D.html)
and
[Including framework files in an HTML-based AIR application](WSF03EE194-4501-482d-BB53-99E6F51C6D44.html)),
you need to instantiate an updater object, as in the following.

ActionScript example:

    var appUpdater:ApplicationUpdater = new ApplicationUpdater();

JavaScript example:

    var appUpdater = new runtime.air.update.ApplicationUpdater();

The previous code uses the ApplicationUpdater class (which provides no user
interface). If you want to use the ApplicationUpdaterUI class (which provides a
user interface), use the following.

ActionScript example:

`var appUpdater:ApplicationUpdaterUI = new ApplicationUpdaterUI();`

JavaScript example:

`var appUpdater = new runtime.air.update.ApplicationUpdaterUI();`

The remaining code samples in this document assume that you have instantiated an
updater object named `appUpdater`.

</div>

<div>

<div>

</div>

</div>
