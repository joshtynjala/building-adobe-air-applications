# Signing an AIR intermediate file with ADT

<div>

To sign an AIR intermediate file with ADT, use the `-sign` command. The sign
command only works with AIR intermediate files (extension `airi`). An AIR file
cannot be signed a second time.

To create an AIR intermediate file, use the adt `-prepare`command. (See
[ADT prepare command](WS901d38e593cd1bac1e63e3d128fc240122-7fff.html).)

<div>

#### Sign an AIRI file

<div>

![](../img/dingbat.png) Use the ADT -`sign` command with following syntax:

    adt -sign SIGNING_OPTIONS airi_file air_file

**SIGNING_OPTIONS** The signing options identify the private key and certificate
with which to sign the AIR file. These options are described in
[ADT code signing options](WS5b3ccc516d4fbf351e63e3d118666ade46-7f72.html).

**airi_file** The path to the unsigned AIR intermediate file to be signed.

**air_file** The name of the AIR file to be created.

</div>

</div>

<div>

#### ADT -sign command example

    adt -sign -storetype pkcs12 -keystore cert.p12 unsignedMyApp.airi myApp.air

For more information, see
[ADT sign command](WS901d38e593cd1bac1e63e3d128fc240122-7ffe.html).

</div>

</div>

<div>

<div>

</div>

</div>
