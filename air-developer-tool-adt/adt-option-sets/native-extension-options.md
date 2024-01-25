# Native extension options

The native extension options specify the options and files for packaging an ANE
file for a native extension. Use these options with an ADT package command in
which the `-target` option is `ane`.

    extension-descriptor -swc swcPath
       -platform platformName
      -platformoptions path/platform.xml
       FILE_OPTIONS

**extension-descriptor** The descriptor file for the native extension.

**-swc** The SWC file containing the ActionScript code and resources for the
native extension.

**-platform** The name of the platform that this ANE file supports. You can
include multiple `-platform` options, each with its own `FILE_OPTIONS`.

**-platformoptions** The path to a platform options (platform.xml) file. Use
this file to specify non-default linker options, shared libraries, and
third-party static libraries used by the extension. For more information and
examples, see
[iOS native libraries](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/air/extensions/WSdb11516da818ea8d49ce0fe713341ed67cf-7fff.html).

**FILE_OPTIONS** Identifies the native platform files to include in the package,
such as static libraries to include in the native extension package. The file
options are fully described in
[File and path options](WS901d38e593cd1bac1e63e3d128fc240122-7ff2.html). (Note
that the -e option cannot be used when packaging an ANE file.)

More Help topics

[Packaging a native extension](https://web.archive.org/web/20150530014906/http://help.adobe.com/en_US/air/extensions/WSf00ab63af761f170-168f6f2a129378b935d-8000.html)
