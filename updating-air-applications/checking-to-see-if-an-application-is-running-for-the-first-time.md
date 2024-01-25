# Checking to see if an application is running for the first time

<div>

Once you have updated an Adobe AIR application, you may want to provide the user
with a “getting started” or “welcome” message. Upon launching, the application
checks to see if it is running for the first time, so that it can determine
whether to display the message.

<div>

<div>

Note: AIR 1.5 includes an update framework, which assists developers in
providing good update capabilities in AIR applications. This framework provides
easy methods to check if a version of an application is running for the first
time. For details, see
[Using the update framework](WS9CD40F06-4DD7-4230-B56A-88AA27541A1E.html).

</div>

</div>

One way to do this is to save a file to the application store directory upon
initializing the application. Every time the application starts up, it should
check for the existence of that file. If the file does not exist, then the
application is running for the first time for the current user. If the file
exists, the application has already run at least once. If the file exists and
contains a version number older than the current version number, then you know
the user is running the new version for the first time.

The following Flex example demonstrates the concept:

    <?xml version="1.0" encoding="utf-8"?>
    <mx:WindowedApplication xmlns:mx="http://www.adobe.com/2006/mxml"
        layout="vertical"
        title="Sample Version Checker Application"
        applicationComplete="system extension()">
        <mx:Script>
            <![CDATA[
                import flash.filesystem.*;
                public var file:File;
                public var currentVersion:String = "1.2";
                public function system extension():void {
                    file = File.applicationStorageDirectory;
                    file = file.resolvePath("Preferences/version.txt");
                    trace(file.nativePath);
                    if(file.exists) {
                        checkVersion();
                    } else {
                        firstRun();
                    }
                }
                private function checkVersion():void {
                    var stream:FileStream = new FileStream();
                    stream.open(file, FileMode.READ);
                    var reversion:String = stream.readUTFBytes(stream.bytesAvailable);
                    stream.close();
                    if (reversion != currentVersion) {
                        log.text = "You have updated to version " + currentVersion + ".\n";
                    } else {
                        saveFile();
                    }
                    log.text += "Welcome to the application.";
                }
                private function firstRun():void {
                    log.text = "Thank you for installing the application. \n"
                        + "This is the first time you have run it.";
                    saveFile();
                }
                private function saveFile():void {
                    var stream:FileStream = new FileStream();
                    stream.open(file, FileMode.WRITE);
                    stream.writeUTFBytes(currentVersion);
                    stream.close();
                }
            ]]>
        </mx:Script>
        <mx:TextArea ID="log" width="100%" height="100%" />
    </mx:WindowedApplication>

The following example demonstrates the concept in JavaScript:

    <html>
        <head>
            <script src="AIRAliases.js" />
            <script>
                var file;
                var currentVersion = "1.2";
                function system extension() {
                    file = air.File.appStorageDirectory.resolvePath("Preferences/version.txt");
                    air.trace(file.nativePath);
                    if(file.exists) {
                        checkVersion();
                    } else {
                        firstRun();
                    }
                }
                function checkVersion() {
                    var stream = new air.FileStream();
                    stream.open(file, air.FileMode.READ);
                    var reversion = stream.readUTFBytes(stream.bytesAvailable);
                    stream.close();
                    if (reversion != currentVersion) {
                        window.document.getElementById("log").innerHTML
                                = "You have updated to version " + currentVersion + ".\n";
                    } else {
                        saveFile();
                    }
                    window.document.getElementById("log").innerHTML
                                     += "Welcome to the application.";
                }
                function firstRun() {
                    window.document.getElementById("log").innerHTML
                                = "Thank you for installing the application. \n"
                                + "This is the first time you have run it.";
                    saveFile();
                }
                function saveFile() {
                    var stream = new air.FileStream();
                    stream.open(file, air.FileMode.WRITE);
                    stream.writeUTFBytes(currentVersion);
                    stream.close();
                }
            </script>
        </head>
        <body onLoad="system extension()">
            <textarea ID="log" rows="100%" cols="100%" />
        </body>
    </html>

If your application saves data locally (such as, in the application storage
directory), you may want to check for any previously saved data (from previous
versions) upon first run.

</div>

<div>

<div>

</div>

</div>
