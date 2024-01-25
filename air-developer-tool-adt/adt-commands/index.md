# ADT commands

The first argument passed to ADT specifies one of the following commands.

- -package — packages an AIR application or AIR Native Extension (ANE).

- -prepare — packages an AIR application as an intermediate file (AIRI), but
  does not sign it. AIRI files cannot be installed.

- -sign — signs an AIRI package produced with the -prepare command. The -prepare
  and -sign commands allow packaging and signing to be performed at different
  times. You can also use the -sign command to sign or resign an ANE package.

- -migrate — applies a migration signature to a signed AIR package, which allows
  you to use a new or renewed code signing certificate.

- -certificate — creates a self-signed digital code signing certificate.

- -checkstore — verifies that a digital certificate in a keystore can be
  accessed.

- -installApp — installs an AIR application on a device or device emulator.

- -launchApp — launches an AIR application on a device or device emulator.

- -appVersion — reports the version of an AIR application currently installed on
  a device or device emulator.

- -uninstallApp — uninstalls an AIR application from a device or device
  emulator.

- -installRuntime — installs the AIR runtime on a device or device emulator.

- -runtimeVersion — reports the version of the AIR runtime currently installed
  on a device or device emulator.

- -uninstallRuntime — uninstalls the AIR runtime currently installed from a
  device or device emulator.

- -version — reports the ADT version number.

- -devices — reports device information for connected mobile devices or
  emulators.

- -help — displays the list of commands and options.

Many ADT commands share related sets of option flags and parameters. These sets
of option are described in detail separately:

- [ADT code signing options](WS5b3ccc516d4fbf351e63e3d118666ade46-7f72.html)

- [File and path options](WS901d38e593cd1bac1e63e3d128fc240122-7ff2.html)

- [Debugger connection options](WS901d38e593cd1bac1e63e3d128fc240122-7ff1.html)

- [Native extension options](WS901d38e593cd1bac1e63e3d128fc240122-7ff0.html)

- [ADT package command](WS901d38e593cd1bac1e63e3d128cdca935b-8000.html)
- [ADT prepare command](WS901d38e593cd1bac1e63e3d128fc240122-7fff.html)
- [ADT sign command](WS901d38e593cd1bac1e63e3d128fc240122-7ffe.html)
- [ADT migrate command](WS901d38e593cd1bac1e63e3d128fc240122-7ffd.html)
- [ADT checkstore command](WS901d38e593cd1bac1e63e3d12905776a90-8000.html)
- [ADT certificate command](WS901d38e593cd1bac1e63e3d128fc240122-7ffc.html)
- [ADT installApp command](WS901d38e593cd1bac1e63e3d128fc240122-7ffa.html)
- [ADT appVersion command](WS901d38e593cd1bac1e63e3d128fc240122-7ff9.html)
- [ADT launchApp command](WS901d38e593cd1bac1e63e3d128fc240122-7ff8.html)
- [ADT uninstallApp command](WS901d38e593cd1bac1e63e3d128fc240122-7ff7.html)
- [ADT installRuntime command](WS901d38e593cd1bac1e63e3d128fc240122-7ff6.html)
- [ADT runtimeVersion command](WS901d38e593cd1bac1e63e3d128fc240122-7ff5.html)
- [ADT uninstallRuntime command](WS901d38e593cd1bac1e63e3d128fc240122-7ff4.html)
- [ADT devices command](WSd6d4f896b3a8801b24e4e975138ba7d1658-8000.html)
- [ADT help command](WS901d38e593cd1bac1e63e3d129194b1eff-8000.html)
