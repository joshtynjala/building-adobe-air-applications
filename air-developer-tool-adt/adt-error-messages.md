# ADT error messages

The following tables list the possible errors that can be reported by the ADT
program and the probable causes:

**Application descriptor validation errors**

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Error code</p></th>
<th><p>Description</p></th>
<th><p>Notes</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>100</p></td>
<td><p>Application descriptor cannot be parsed</p></td>
<td><p>Check the application descriptor file for XML syntax errors such
as unclosed tags.</p></td>
</tr>
<tr class="even">
<td><p>101</p></td>
<td><p>Namespace is missing</p></td>
<td><p>Add the missing namespace.</p></td>
</tr>
<tr class="odd">
<td><p>102</p></td>
<td><p>Invalid namespace</p></td>
<td><p>Check the namespace spelling.</p></td>
</tr>
<tr class="even">
<td><p>103</p></td>
<td><p>Unexpected element or attribute</p></td>
<td><p>Remove offending elements and attributes. Custom values are not
allowed in the descriptor file.</p>
<p>Check the spelling of element and attribute names.</p>
<p>Make sure that elements are placed within the correct parent element
and that attributes are used with the correct elements.</p></td>
</tr>
<tr class="odd">
<td><p>104</p></td>
<td><p>Missing element or attribute</p></td>
<td><p>Add the required element or attribute.</p></td>
</tr>
<tr class="even">
<td><p>105</p></td>
<td><p>Element or attribute contains an invalid value</p></td>
<td><p>Correct the offending value.</p></td>
</tr>
<tr class="odd">
<td><p>106</p></td>
<td><p>Illegal window attribute combination</p></td>
<td><p>Some window settings, such as <samp>transparency = true</samp>and
<samp>systemChrome = standard</samp> cannot be used together. Change one
of the incompatible settings.</p></td>
</tr>
<tr class="even">
<td><p>107</p></td>
<td><p>Window minimum size is larger than the window maximum
size</p></td>
<td><p>Change either the minimum or the maximum size setting.</p></td>
</tr>
<tr class="odd">
<td><p>108</p></td>
<td><p>Attribute already used in prior element</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>109</p></td>
<td><p>Duplicate element.</p></td>
<td><p>Remove the duplicate element.</p></td>
</tr>
<tr class="odd">
<td><p>110</p></td>
<td><p>At least one element of the specified type is required.</p></td>
<td><p>Add the missing element.</p></td>
</tr>
<tr class="even">
<td><p>111</p></td>
<td><p>None of the profiles listed in the application descriptor support
native extensions.</p></td>
<td><p>Add a profile to the supportedProfies list that supports native
extensions.</p></td>
</tr>
<tr class="odd">
<td><p>112</p></td>
<td><p>The AIR target doesn't support native extensions.</p></td>
<td><p>Choose a target that supports native extensions.</p></td>
</tr>
<tr class="even">
<td><p>113</p></td>
<td><p>&lt;nativeLibrary&gt; and &lt;initializer&gt; must be provided
together.</p></td>
<td><p>An initializer function must be specified for every native
library in the native extension.</p></td>
</tr>
<tr class="odd">
<td><p>114</p></td>
<td><p>Found &lt;finalizer&gt; without &lt;nativeLibrary&gt;.</p></td>
<td><p>Do not specify a finalizer unless the platform uses a native
library.</p></td>
</tr>
<tr class="even">
<td><p>115</p></td>
<td><p>The default platform must not contain a native
implementation.</p></td>
<td><p>Do not specify a native library in the default platform
element.</p></td>
</tr>
<tr class="odd">
<td><p>116</p></td>
<td><p>Browser invocation is not supported for this target.</p></td>
<td><p>The <samp>&lt;allowBrowserInvocation&gt;</samp> element cannot be
<samp>true</samp> for the specified packaging target.</p></td>
</tr>
<tr class="even">
<td><p>117</p></td>
<td><p>This target requires at least namespace n to package native
extensions.</p></td>
<td><p>Change the AIR namespace in the application descriptor to a
supported value.</p></td>
</tr>
</tbody>
</table>

See
[AIR application descriptor files](WS5b3ccc516d4fbf351e63e3d118666ade46-7ff1.html)
for information about the namespaces, elements, attributes, and their valid
values.

**Application icon errors**

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Error code</p></th>
<th><p>Description</p></th>
<th><p>Notes</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>200</p></td>
<td><p>Icon file cannot be opened</p></td>
<td><p>Check that the file exists at the specified path.</p>
<p>Use another application to ensure that the file can be
opened.</p></td>
</tr>
<tr class="even">
<td><p>201</p></td>
<td><p>Icon is the wrong size</p></td>
<td><p>Icon size (in pixels) must match the XML tag. For example, given
the application descriptor element:</p>
<p><samp>&lt;image32x32&gt;icon.png&lt;/image32x32&gt;</samp></p>
<p>The image in <samp>icon.png</samp> must be exactly 32x32
pixels.</p></td>
</tr>
<tr class="odd">
<td><p>202</p></td>
<td><p>Icon file contains an unsupported image format</p></td>
<td><p>Only the PNG format is supported. Convert images in other formats
before packaging your application.</p></td>
</tr>
</tbody>
</table>

**Application file errors**

| Error code | Description                                                  | Notes                                                                                                                                                                                                                                                                                                                      |
| ---------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 300        | Missing file, or file cannot be opened                       | A file specified on the command line cannot be found, or cannot be opened.                                                                                                                                                                                                                                                 |
| 301        | Application descriptor file missing or cannot be opened      | The application descriptor file cannot be found at the specified path or cannot be opened.                                                                                                                                                                                                                                 |
| 302        | Root content file missing from package                       | The SWF or HTML file referenced in the `<content>` element of the application descriptor must be added to the package by including it in the files listed on the ADT command line.                                                                                                                                         |
| 303        | Icon file missing from package                               | The icon files specified in the application descriptor must be added to the package by including them among the files listed on the ADT command line. Icon files are not added automatically.                                                                                                                              |
| 304        | Initial window content is invalid                            | The file referenced in the `<content>` element of the application descriptor is not recognized as a valid HTML or SWF file.                                                                                                                                                                                                |
| 305        | Initial window content SWF version exceeds namespace version | The SWF version of the file referenced in the `<content>` element of the application descriptor is not supported by the version of AIR specified in the descriptor namespace. For example, attempting to package a SWF10 (Flash Player 10) file as the initial content of an AIR 1.1 application will generate this error. |
| 306        | Profile not supported.                                       | The profile you are specifying in the application descriptor file is not supported. See [supportedProfiles](WSfffb011ac560372f2fea1812938a6e463-7fe2.html).                                                                                                                                                                |
| 307        | Namespace must be at least _nnn_.                            | Use the appropriate namespace for the features used in the application (such as the 2.0 namespace).                                                                                                                                                                                                                        |

**Exit codes for other errors**

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Exit code</p></th>
<th><p>Description</p></th>
<th><p>Notes</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>Usage error</p></td>
<td><p>Check the command-line arguments for errors</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>Unknown error</p></td>
<td><p>This error indicates a situation that cannot be explained by
common error conditions. Possible root causes include incompatibility
between ADT and the Java Runtime Environment, corrupt ADT or JRE
installations, and programming errors within ADT.</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>Could not write to output directory</p></td>
<td><p>Make sure that the specified (or implied) output directory is
accessible and that the containing drive is has sufficient disk
space.</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>Could not access certificate</p></td>
<td><p>Make sure that the path to the keystore is specified
correctly.</p>
<p>Check that the certificate within the keystore can be accessed. The
Java 1.6 Keytool utility can be used to help troubleshoot certificate
access issues.</p></td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>Invalid certificate</p></td>
<td><p>The certificate file is malformed, modified, expired, or
revoked.</p></td>
</tr>
<tr class="even">
<td><p>9</p></td>
<td><p>Could not sign AIR file</p></td>
<td><p>Verify the signing options passed to ADT.</p></td>
</tr>
<tr class="odd">
<td><p>10</p></td>
<td><p>Could not create time stamp</p></td>
<td><p>ADT could not establish a connection to the timestamp server. If
you connect to the internet through a proxy server, you may need to
configure the JRE proxy settings.</p></td>
</tr>
<tr class="even">
<td><p>11</p></td>
<td><p>Certificate creation error</p></td>
<td><p>Verify the command-line arguments used for creating
signatures.</p></td>
</tr>
<tr class="odd">
<td><p>12</p></td>
<td><p>Invalid input</p></td>
<td><p>Verify file paths and other arguments passed to ADT on the
command line.</p></td>
</tr>
<tr class="even">
<td><p>13</p></td>
<td><p>Missing device SDK</p></td>
<td><p>Verify the device SDK configuration. ADT cannot locate the device
SDK required to execute the specified command.</p></td>
</tr>
<tr class="odd">
<td><p>14</p></td>
<td><p>Device error</p></td>
<td><p>ADT cannot execute the command because of a device restriction or
problem. For example, this exit code is emitted when attempting to
uninstall an app that is not actually installed.</p></td>
</tr>
<tr class="even">
<td><p>15</p></td>
<td><p>No devices</p></td>
<td><p>Verify that a device is attached and turned on or that an
emulator is running.</p></td>
</tr>
<tr class="odd">
<td><p>16</p></td>
<td><p>Missing GPL components</p></td>
<td><p>The current AIR SDK does not include all the components required
to perform the request operation.</p></td>
</tr>
<tr class="even">
<td><p>17</p></td>
<td><p>Device packaging tool failed.</p></td>
<td><p>The package could not be created because expected operating
system components are missing.</p></td>
</tr>
</tbody>
</table>

**Android errors**

| Exit code | Description                                                       | Notes                                                                                                                                                                                                                            |
| --------- | ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 400       | Current Android sdk version doesn't support attribute.            | Check that the attribute name is spelled correctly and is a valid attribute for the element in which it appears. You may need to set the -platformsdk flag in the ADT command if the attribute was introduced after Android 2.2. |
| 401       | Current Android sdk version doesn't support attribute value       | Check that the attribute value is spelled correctly and is a valid value for the attribute. You may need to set the -platformsdk flag in the ADT command if the attribute value was introduced after Android 2.2.                |
| 402       | Current Android sdk version doesn't support XML tag               | Check that the XML tag name is spelled correctly and is a valid Android manifest document element. You may need to set the -platformsdk flag in the ADT command if the element was introduced after Android 2.2.                 |
| 403       | Android tag is not allowed to be overridden                       | The application is attempting to override an Android manifest element that is reserved for use by AIR. See [Android settings](WSfffb011ac560372f-5d0f4f25128cc9cd0cb-7ffc.html).                                                 |
| 404       | Android attribute is not allowed to be overridden                 | The application is attempting to override an Android manifest attribute that is reserved for use by AIR. See [Android settings](WSfffb011ac560372f-5d0f4f25128cc9cd0cb-7ffc.html).                                               |
| 405       | Android tag %1 must be the first element in manifestAdditions tag | Move the specified tag to the required location.                                                                                                                                                                                 |
| 406       | The attribute %1 of the android tag %2 has invalid value %3.      | Supply a valid value for the attribute.                                                                                                                                                                                          |
