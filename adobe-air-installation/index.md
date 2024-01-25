# Adobe AIR installation

The Adobe® AIR® runtime allows you to run AIR applications. You can install the
runtime in the following ways:

- By installing the runtime separately (without also installing an AIR
  application)

- By installing an AIR application for the first time through a web page
  installation "badge" (you are prompted to also install the runtime)

- By creating a custom installer that installs both your application and the
  runtime. You must get approval from Adobe to distribute the AIR runtime in
  this fashion. You can request approval on the
  [Adobe runtime licensing](http://www.adobe.com/licensing/) page. Note that
  Adobe does not provide tools for building such an installer. Many third-party
  installer toolkits are available, however.

- By installing an AIR application that bundles AIR as a captive runtime. A
  captive runtime is used only by the bundling application. It is not used to
  run other AIR applications. Bundling the runtime is an option on Mac and
  Windows. On iOS, all applications include a bundled runtime. As of AIR 3.7,
  all Android applications include a bundled runtime by default (although you
  have the option of using a separate runtime).

- By setting up an AIR development environment such as the AIR SDK, Adobe®
  Flash® Builder™ , or the Adobe Flex® SDK (which includes the AIR command line
  development tools). The runtime included in the SDK is only used when
  debugging applications — it is not used to run installed AIR applications.

The system requirements for installing AIR and running AIR applications are
detailed here:
[Adobe AIR: System requirements](https://web.archive.org/web/20200408200256/https://www.adobe.com/products/air/tech-specs.html).

Both the runtime installer and the AIR application installer create log files
when they install, update, or remove AIR applications or the AIR runtime itself.
You can consult these logs to help determine the cause of any installation
problems. See
[Installation logs](https://web.archive.org/web/20150520002006/http://kb2.adobe.com/cps/839/cpsid_83989.html).

- [Installing Adobe AIR](./installing-adobe-air.md)
- [Removing Adobe AIR](./removing-adobe-air.md)
- [Installing and running the AIR sample applications](./installing-and-running-the-air-sample-applications.md)
- [Adobe AIR updates](./adobe-air-updates.md)
