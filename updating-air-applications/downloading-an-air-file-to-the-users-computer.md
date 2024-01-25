# Downloading an AIR file to the user's computer

To use the Updater class, the user or the application must first save an AIR
file locally to the user's computer.

Note: AIR 1.5 includes an update framework, which assists developers in
providing good update capabilities in AIR applications. Using this framework may
be much easier than using the `update()` method of the Update class directly.
For details, see
[Using the update framework](WS9CD40F06-4DD7-4230-B56A-88AA27541A1E.html).

The following code reads an AIR file from a URL
(`http://example.com/air/updates/Sample_App_v2.air`) and saves the AIR file to
the application storage directory.

ActionScript example:

    var urlString:String = "http://example.com/air/updates/Sample_App_v2.air";
    var urlReq:URLRequest = new URLRequest(urlString);
    var urlStream:URLStream = new URLStream();
    var fileData:ByteArray = new ByteArray();
    urlStream.addEventListener(Event.COMPLETE, loaded);
    urlStream.load(urlReq);

    function loaded(event:Event):void {
        urlStream.readBytes(fileData, 0, urlStream.bytesAvailable);
        writeAirFile();
    }

    function writeAirFile():void {
        var file:File = File.applicationStorageDirectory.resolvePath("My App v2.air");
        var fileStream:FileStream = new FileStream();
        fileStream.open(file, FileMode.WRITE);
        fileStream.writeBytes(fileData, 0, fileData.length);
        fileStream.close();
        trace("The AIR file is written.");
    }

JavaScript example:

    var urlString = "http://example.com/air/updates/Sample_App_v2.air";
    var urlReq = new air.URLRequest(urlString);
    var urlStream = new air.URLStream();
    var fileData = new air.ByteArray();
    urlStream.addEventListener(air.Event.COMPLETE, loaded);
    urlStream.load(urlReq);

    function loaded(event) {
        urlStream.readBytes(fileData, 0, urlStream.bytesAvailable);
        writeAirFile();
    }

    function writeAirFile() {
        var file = air.File.desktopDirectory.resolvePath("My App v2.air");
        var fileStream = new air.FileStream();
        fileStream.open(file, air.FileMode.WRITE);
        fileStream.writeBytes(fileData, 0, fileData.length);
        fileStream.close();
        trace("The AIR file is written.");
    }

For more information, see:

- [Workflow for reading and writing files](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7dc8.html)
  (for ActionScript developers)

- [Workflow for reading and writing files](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7dc8.html)
  (for HTML developers)
