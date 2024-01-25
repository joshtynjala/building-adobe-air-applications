# Defining the update descriptor files and adding the AIR file to your web server

<div>

When you use the AIR update framework, you define basic information about the
available update in update descriptor files, stored on your web server. An
update descriptor file is a simple XML file. The update framework included in
the application checks this file to see if a new version has been uploaded.

The format of the update descriptor file changed for AIR 2.5. The new format
uses a different namespace. The original namespace is
“http://ns.adobe.com/air/framework/update/description/1.0”. The AIR 2.5 name
space is “http://ns.adobe.com/air/framework/update/description/2.5”.

AIR applications created prior to AIR 2.5 can only read the version 1.0 update
descriptor. AIR applications created using the updater framework included in AIR
2.5 or later can only read the version 2.5 update descriptor. Because of this
version incompatibility, you often need to create two update descriptor files.
The update logic in the AIR 2.5 versions of your application must download an
update descriptor that uses the new format. Earlier versions of your AIR
application must continue to use the original format. Both files must be
modified for every update that you release (until you stop supporting versions
created before AIR 2.5).

The update descriptor file contains the following data:

- `versionNumber`—The new version of the AIR application. Use the
  `versionNumber` element in update descriptors used to update AIR 2.5
  applications. The value must be the same string that is used in the
  `versionNumber` element of the new AIR application descriptor file. If the
  version number in the update descriptor file does not match the update AIR
  file’s version number, the update framework will throw an exception.

- `version`—The new version of the AIR application. Use the `version` element in
  update descriptors used to update applications created prior to AIR 2.5. The
  value must be the same string that is used in the `version` element of the new
  AIR application descriptor file. If the version in the update descriptor file
  does not match the update AIR file’s version, the update framework will throw
  an exception.

- `versionLabel`—The human readable version string intended to be shown to
  users. The `versionLabel` is optional, but can only be specified in version
  2.5 update descriptor files. Use it if you use a `versionLabel` in the
  application descriptor and set it to the same value.

- `url`—The location of the update AIR file. This is the file that contains the
  update version of the AIR application.

- `description`—Details regarding the new version. This information can be
  displayed to the user during the update process.

The `version` and `url` elements are mandatory. The `description` element is
optional.

Here is a sample version 2.5 update descriptor file:

    <?xml version="1.0" encoding="utf-8"?>
         <update xmlns="http://ns.adobe.com/air/framework/update/description/2.5">
           <versionNumber>1.1.1</versionNumber>
           <url>http://example.com/updates/sample_1.1.1.air</url>
           <description>This is the latest version of the Sample application.</description>
        </update>

And, here is a sample version 1.0 update descriptor file:

    <?xml version="1.0" encoding="utf-8"?>
         <update xmlns="http://ns.adobe.com/air/framework/update/description/1.0">
           <version>1.1.1</version>
           <url>http://example.com/updates/sample_1.1.1.air</url>
           <description>This is the latest version of the Sample application.</description>
        </update>

If you want to define the `description` tag using multiple languages, use
multiple `text` elements that define a `lang` attribute:

    <?xml version="1.0" encoding="utf-8"?>
         <update xmlns="http://ns.adobe.com/air/framework/update/description/2.5">
           <versionNumber>1.1.1</versionNumber>
           <url>http://example.com/updates/sample_1.1.1.air</url>
           <description>
               <text xml:lang="en">English description</text>
               <text xml:lang="fr">French description</text>
               <text xml:lang="ro">Romanian description</text>
           </description>
        </update>

Place the update descriptor file, along with the update AIR file, on your web
server.

The templates directory included with the update descriptor includes sample
update descriptor files. These include both single-language and multi-language
versions.

</div>

<div>

<div>



</div>

</div>
