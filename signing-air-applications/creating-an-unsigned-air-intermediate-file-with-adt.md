# Creating an unsigned AIR intermediate file with ADT

Use the `-prepare` command to create an unsigned AIR intermediate file. An AIR
intermediate file must be signed with the ADT `-sign` command to produce a valid
AIR installation file.

The `-prepare` command takes the same flags and parameters as the `-package`
command (except for the signing options). The only difference is that the output
file is not signed. The intermediate file is generated with the filename
extension: `airi`.

To sign an AIR intermediate file, use the ADT `-sign` command. (See
[ADT prepare command](WS901d38e593cd1bac1e63e3d128fc240122-7fff.html).)

#### ADT -prepare command example

    adt -prepare unsignedMyApp.airi myApp.xml myApp.swf components.swc
