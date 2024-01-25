# Working with the AIR APIs

Adobe® AIR® includes functionality that is not available to SWF content running
in Adobe® Flash® Player.

#### ActionScript 3.0 Developers

The Adobe AIR APIs are documented in the following two books:

- [ActionScript 3.0 Developer's Guide](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/index.html)

- [ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/)

#### HTML Developers

If you're building HTML-based AIR applications, the APIs that are available to
you in JavaScript via the AIRAliases.js file (see
[Accessing AIR API classes from JavaScript](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7f0d.html))
are documented in the following two books:

- [HTML Developer's Guide for Adobe AIR](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/air/html/dev/index.html)

- [Adobe AIR API Reference for HTML Developers](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/air/reference/html/)

## AIR-specific ActionScript 3.0 classes

The following table contains runtime classes are specific to Adobe AIR. They are
not available to SWF content running in Adobe® Flash® Player in the browser.

#### HTML Developers

The classes that are available to you in JavaScript via the AIRAliases.js file
are listed in
[Adobe AIR API Reference for HTML Developers](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/air/reference/html/).

| Class                                                                                                                                                      | ActionScript 3.0 Package | Added in AIR version                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ----------------------------------- |
| [ARecord](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/dns/ARecord.html)                                                  | flash.net.dns            | 2.0                                 |
| [AAAARecord](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/dns/AAAARecord.html)                                            | flash.net.dns            | 2.0                                 |
| [ApplicationUpdater](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/update/ApplicationUpdater.html)                               | air.update               | 1.5                                 |
| [ApplicationUpdaterUI](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/update/ApplicationUpdaterUI.html)                           | air.update               | 1.5                                 |
| [AudioPlaybackMode](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/media/AudioPlaybackMode.html)                                | flash.media              | 3.0                                 |
| [AutoCapitalize](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/text/AutoCapitalize.html)                                       | flash.text               | 3.0                                 |
| [BrowserInvokeEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/BrowserInvokeEvent.html)                             | flash.events             | 1.0                                 |
| [CameraPosition](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/media/CameraPosition.html)                                      | flash.media              | 3.0                                 |
| [CameraRoll](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/media/CameraRoll.html)                                              | flash.media              | 2.0                                 |
| [CameraRollBrowseOptions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/media/CameraRollBrowseOptions.html)                    | flash.media              | 3.0                                 |
| [CameraUI](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/media/CameraUI.html)                                                  | flash.media              | 2.5                                 |
| [CertificateStatus](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/security/CertificateStatus.html)                             | flash.security           | 2.0                                 |
| [CompressionAlgorithm](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/utils/CompressionAlgorithm.html)                          | flash.utils              | 1.0                                 |
| [DatagramSocket](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/DatagramSocket.html)                                        | flash.net                | 2.0                                 |
| [DatagramSocketDataEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DatagramSocketDataEvent.html)                   | flash.events             | 2.0                                 |
| [DNSResolver](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/dns/DNSResolver.html)                                          | flash.net.dns            | 2.0                                 |
| [DNSResolverEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DNSResolverEvent.html)                                 | flash.events             | 2.0                                 |
| [DockIcon](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/DockIcon.html)                                                | flash.desktop            | 1.0                                 |
| [DownloadErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/update/events/DownloadErrorEvent.html)                        | air.update.events        | 1.5                                 |
| [DRMAuthenticateEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMAuthenticateEvent.html)                         | flash.events             | 1.0                                 |
| [DRMDeviceGroup](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMDeviceGroup.html)                                    | flash.net.drm            | 3.0                                 |
| [DRMDeviceGroupErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMDeviceGroupErrorEvent.html)                 | flash.net.drm            | 3.0                                 |
| [DRMDeviceGroupEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMDeviceGroupEvent.html)                           | flash.net.drm            | 3.0                                 |
| [DRMManagerError](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/errors/DRMManagerError.html)                                   | flash.errors             | 1.5                                 |
| [EncryptedLocalStore](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/EncryptedLocalStore.html)                             | flash.data               | 1.0                                 |
| [ExtensionContext](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/external/ExtensionContext.html)                               | flash.external           | 2.5                                 |
| [File](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/filesystem/File.html)                                                     | flash.filesystem         | 1.0                                 |
| [FileListEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/FileListEvent.html)                                       | flash.events             | 1.0                                 |
| [FileMode](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/filesystem/FileMode.html)                                             | flash.filesystem         | 1.0                                 |
| [FileStream](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/filesystem/FileStream.html)                                         | flash.filesystem         | 1.0                                 |
| [FocusDirection](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/FocusDirection.html)                                    | flash.display            | 1.0                                 |
| [GameInput](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/ui/GameInput.html)                                                   | flash.ui                 | 3.0                                 |
| [GameInputControl](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/ui/GameInputControl.html)                                     | flash.ui                 | 3.0                                 |
| [GameInputControlType](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/ui/GameInputControlType.html)                             | flash.ui                 | 3.6 and earlier; dropped, as of 3.7 |
| [GameInputDevice](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/ui/GameInputDevice.html)                                       | flash.ui                 | 3.0                                 |
| [GameInputEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/GameInputEvent.html)                                     | flash.ui                 | 3.0                                 |
| [GameInputFinger](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/ui/GameInputFinger.html)                                       | flash.ui                 | 3.6 and earlier; dropped, as of 3.7 |
| [GameInputHand](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/ui/GameInputHand.html)                                           | flash.ui                 | 3.6 and earlier; dropped, as of 3.7 |
| [Geolocation](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/sensors/Geolocation.html)                                          | flash.sensors            | 2.0                                 |
| [GeolocationEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/GeolocationEvent.html)                                 | flash.events             | 2.0                                 |
| [HTMLHistoryItem](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/html/HTMLHistoryItem.html)                                     | flash.html               | 1.0                                 |
| [HTMLHost](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/html/HTMLHost.html)                                                   | flash.html               | 1.0                                 |
| [HTMLLoader](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/html/HTMLLoader.html)                                               | flash.html               | 1.0                                 |
| [HTMLPDFCapability](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/html/HTMLPDFCapability.html)                                 | flash.html               | 1.0                                 |
| [HTMLSWFCapabiltiy](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/html/HTMLSWFCapability.html)                                 | flash.html               | 2.0                                 |
| [HTMLUncaughtScriptExceptionEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/HTMLUncaughtScriptExceptionEvent.html) | flash.events             | 1.0                                 |
| [HTMLWindowCreateOptions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/html/HTMLWindowCreateOptions.html)                     | flash.html               | 1.0                                 |
| [Icon](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/Icon.html)                                                        | flash.desktop            | 1.0                                 |
| _[IFilePromise](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/IFilePromise.html)_                                      | flash.desktop            | 2.0                                 |
| [ImageDecodingPolicy](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/system/ImageDecodingPolicy.html)                           | flash.system             | 2.6                                 |
| [InteractiveIcon](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/InteractiveIcon.html)                                  | flash.desktop            | 1.0                                 |
| [InterfaceAddress](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/InterfaceAddress.html)                                    | flash.net                | 2.0                                 |
| [InvokeEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/InvokeEvent.html)                                           | flash.events             | 1.0                                 |
| [InvokeEventReason](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/InvokeEventReason.html)                              | flash.desktop            | 1.5.1                               |
| [IPVersion](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/IPVersion.html)                                                  | flash.net                | 2.0                                 |
| _[IURIDereferencer](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/security/IURIDereferencer.html)_                             | flash.security           | 1.0                                 |
| [LocationChangeEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/LocationChangeEvent.html)                           | flash.events             | 2.5                                 |
| [MediaEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/MediaEvent.html)                                             | flash.events             | 2.5                                 |
| [MediaPromise](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/media/MediaPromise.html)                                          | flash.media              | 2.5                                 |
| [MediaType](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/media/MediaType.html)                                                | flash.media              | 2.5                                 |
| [MXRecord](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/dns/MXRecord.html)                                                | flash.net.dns            | 2.0                                 |
| [NativeApplication](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NativeApplication.html)                              | flash.desktop            | 1.0                                 |
| [NativeDragActions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NativeDragActions.html)                              | flash.desktop            | 1.0                                 |
| [NativeDragEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/NativeDragEvent.html)                                   | flash.events             | 1.0                                 |
| [NativeDragManager](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NativeDragManager.html)                              | flash.desktop            | 1.0                                 |
| [NativeDragOptions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NativeDragOptions.html)                              | flash.desktop            | 1.0                                 |
| [NativeMenu](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeMenu.html)                                            | flash.display            | 1.0                                 |
| [NativeMenuItem](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeMenuItem.html)                                    | flash.display            | 1.0                                 |
| [NativeProcess](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NativeProcess.html)                                      | flash.desktop            | 2.0                                 |
| [NativeProcessExitEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/NativeProcessExitEvent.html)                     | flash.events             | 2.0                                 |
| [NativeProcessStartupInfo](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NativeProcessStartupInfo.html)                | flash.desktop            | 2.0                                 |
| [NativeWindow](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindow.html)                                        | flash.display            | 1.0                                 |
| [NativeWindowBoundsEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/NativeWindowBoundsEvent.html)                   | flash.events             | 1.0                                 |
| [NativeWindowDisplayState](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindowDisplayState.html)                | flash.display            | 1.0                                 |
| [NativeWindowDisplayStateEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/NativeWindowDisplayStateEvent.html)       | flash.events             | 1.0                                 |
| [NativeWindowInitOptions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindowInitOptions.html)                  | flash.display            | 1.0                                 |
| [NativeWindowRenderMode](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindowRenderMode.html)                    | flash.display            | 3.0                                 |
| [NativeWindowResize](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindowResize.html)                            | flash.display            | 1.0                                 |
| [NativeWindowSystemChrome](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindowSystemChrome.html)                | flash.display            | 1.0                                 |
| [NativeWindowType](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindowType.html)                                | flash.display            | 1.0                                 |
| [NetworkInfo](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/NetworkInfo.html)                                              | flash.net                | 2.0                                 |
| [NetworkInterface](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/NetworkInterface.html)                                    | flash.net                | 2.0                                 |
| [NotificationType](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/NotificationType.html)                                | flash.desktop            | 1.0                                 |
| [OutputProgressEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/OutputProgressEvent.html)                           | flash.events             | 1.0                                 |
| [PaperSize](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/printing/PaperSize.html)                                             | flash.printing           | 2.0                                 |
| [PrintMethod](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/printing/PrintMethod.html)                                         | flash.printing           | 2.0                                 |
| [PrintUIOptions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/printing/PrintUIOptions.html)                                   | flash.printing           | 2.0                                 |
| [PTRRecord](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/dns/PTRRecord.html)                                              | flash.net.dns            | 2.0                                 |
| [ReferencesValidationSetting](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/security/ReferencesValidationSetting.html)         | flash.security           | 1.0                                 |
| [ResourceRecord](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/dns/ResourceRecord.html)                                    | flash.net.dns            | 2.0                                 |
| [RevocationCheckSettings](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/security/RevocationCheckSettings.html)                 | flash.security           | 1.0                                 |
| [Screen](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/Screen.html)                                                    | flash.display            | 1.0                                 |
| [ScreenMouseEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/ScreenMouseEvent.html)                                 | flash.events             | 1.0                                 |
| [SecureSocket](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/SecureSocket.html)                                            | flash.net                | 2.0                                 |
| [SecureSocketMonitor](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/net/SecureSocketMonitor.html)                                | air.net                  | 2.0                                 |
| [ServerSocket](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/ServerSocket.html)                                            | flash.net                | 2.0                                 |
| [ServerSocketConnectEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/ServerSocketConnectEvent.html)                 | flash.events             | 2.0                                 |
| [ServiceMonitor](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/net/ServiceMonitor.html)                                          | air.net                  | 1.0                                 |
| [SignatureStatus](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/security/SignatureStatus.html)                                 | flash.security           | 1.0                                 |
| [SignerTrustSettings](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/security/SignerTrustSettings.html)                         | flash.security           | 1.0                                 |
| [SocketMonitor](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/net/SocketMonitor.html)                                            | air.net                  | 1.0                                 |
| [SoftKeyboardType](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/text/SoftKeyboardType.html)                                   | flash.text               | 3.0                                 |
| [SQLCollationType](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLCollationType.html)                                   | flash.data               | 1.0                                 |
| [SQLColumnNameStyle](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLColumnNameStyle.html)                               | flash.data               | 1.0                                 |
| [SQLColumnSchema](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLColumnSchema.html)                                     | flash.data               | 1.0                                 |
| [SQLConnection](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLConnection.html)                                         | flash.data               | 1.0                                 |
| [SQLError](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/errors/SQLError.html)                                                 | flash.errors             | 1.0                                 |
| [SQLErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/SQLErrorEvent.html)                                       | flash.events             | 1.0                                 |
| [SQLErrorOperation](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/errors/SQLErrorOperation.html)                               | flash.errors             | 1.0                                 |
| [SQLEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/SQLEvent.html)                                                 | flash.events             | 1.0                                 |
| [SQLIndexSchema](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLIndexSchema.html)                                       | flash.data               | 1.0                                 |
| [SQLMode](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLMode.html)                                                     | flash.data               | 1.0                                 |
| [SQLResult](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLResult.html)                                                 | flash.data               | 1.0                                 |
| [SQLSchema](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLSchema.html)                                                 | flash.data               | 1.0                                 |
| [SQLSchemaResult](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLSchemaResult.html)                                     | flash.data               | 1.0                                 |
| [SQLStatement](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLStatement.html)                                           | flash.data               | 1.0                                 |
| [SQLTableSchema](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLTableSchema.html)                                       | flash.data               | 1.0                                 |
| [SQLTransactionLockType](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLTransactionLockType.html)                       | flash.data               | 1.0                                 |
| [SQLTriggerSchema](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLTriggerSchema.html)                                   | flash.data               | 1.0                                 |
| [SQLUpdateEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/SQLUpdateEvent.html)                                     | flash.events             | 1.0                                 |
| [SQLViewSchema](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/data/SQLViewSchema.html)                                         | flash.data               | 1.0                                 |
| [SRVRecord](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/dns/SRVRecord.html)                                              | flash.net.dns            | 2.0                                 |
| [StageAspectRatio](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/StageAspectRatio.html)                                | flash.display            | 2.0                                 |
| [StageOrientation](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/StageOrientation.html)                                | flash.display            | 2.0                                 |
| [StageOrientationEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/StageOrientationEvent.html)                       | flash.events             | 2.0                                 |
| [StageText](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/text/StageText.html)                                                 | flash.text               | 3.0                                 |
| [StageTextInitOptions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/text/StageTextInitOptions.html)                           | flash.text               | 3.0                                 |
| [StageWebView](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/media/StageWebView.html)                                          | flash.media              | 2.5                                 |
| [StatusFileUpdateErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/update/events/StatusFileUpdateErrorEvent.html)        | air.update.events        | 1.5                                 |
| [StatusFileUpdateEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/update/events/StatusFileUpdateEvent.html)                  | air.update.events        | 1.5                                 |
| [StatusUpdateErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/update/events/StatusUpdateErrorEvent.html)                | air.update.events        | 1.5                                 |
| [StatusUpdateEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/update/events/StatusUpdateEvent.html)                          | air.update.events        | 1.5                                 |
| [StorageVolume](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/filesystem/StorageVolume.html)                                   | flash.filesystem         | 2.0                                 |
| [StorageVolumeChangeEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/StorageVolumeChangeEvent.html)                 | flash.events             | 2.0                                 |
| [StorageVolumeInfo](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/filesystem/StorageVolumeInfo.html)                           | flash.filesystem         | 2.0                                 |
| [SystemIdleMode](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/SystemIdleMode.html)                                    | flash.desktop            | 2.0                                 |
| [SystemTrayIcon](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/SystemTrayIcon.html)                                    | flash.desktop            | 1.0                                 |
| [TouchEventIntent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/TouchEventIntent.html)                                 | flash.events             | 3.0                                 |
| [UpdateEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/update/events/UpdateEvent.html)                                      | air.update.events        | 1.5                                 |
| [Updater](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/Updater.html)                                                  | flash.desktop            | 1.0                                 |
| [URLFilePromise](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/desktop/URLFilePromise.html)                                      | air.desktop              | 2.0                                 |
| [URLMonitor](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/air/net/URLMonitor.html)                                                  | air.net                  | 1.0                                 |
| [URLRequestDefaults](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/URLRequestDefaults.html)                                | flash.net                | 1.0                                 |
| [XMLSignatureValidator](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/security/XMLSignatureValidator.html)                     | flash.security           | 1.0                                 |

## Flash Player classes with AIR-specific functionality

The following classes are available to SWF content running in the browser, but
AIR provides additional properties or methods:

| Package        | Class                                                                                                                                     | Property, method, or event          | Added in AIR version |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- | -------------------- |
| flash.desktop  | [Clipboard](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/Clipboard.html)                             | `supportsFilePromise`               | 2.0                  |
|                | [ClipboardFormats](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/desktop/ClipboardFormats.html)               | BITMAP_FORMAT                       | 1.0                  |
|                |                                                                                                                                           | FILE_LIST_FORMAT                    | 1.0                  |
|                |                                                                                                                                           | `FILE_PROMISE_LIST_FORMAT`          | 2.0                  |
|                |                                                                                                                                           | `URL_FORMAT`                        | 1.0                  |
| flash.display  | [LoaderInfo](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/LoaderInfo.html)                           | `childSandboxBridge`                | 1.0                  |
|                |                                                                                                                                           | `parentSandboxBridge`               | 1.0                  |
|                | [Stage](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/Stage.html)                                     | assignFocus()                       | 1.0                  |
|                |                                                                                                                                           | autoOrients                         | 2.0                  |
|                |                                                                                                                                           | deviceOrientation                   | 2.0                  |
|                |                                                                                                                                           | `nativeWindow`                      | 1.0                  |
|                |                                                                                                                                           | orientation                         | 2.0                  |
|                |                                                                                                                                           | orientationChange event             | 2.0                  |
|                |                                                                                                                                           | orientationChanging event           | 2.0                  |
|                |                                                                                                                                           | setAspectRatio                      | 2.0                  |
|                |                                                                                                                                           | `setOrientation`                    | 2.0                  |
|                |                                                                                                                                           | softKeyboardRect                    | 2.6                  |
|                |                                                                                                                                           | supportedOrientations               | 2.6                  |
|                |                                                                                                                                           | supportsOrientationChange           | 2.0                  |
|                | [NativeWindow](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindow.html)                       | owner                               | 2.6                  |
|                |                                                                                                                                           | listOwnedWindows                    | 2.6                  |
|                | [NativeWindowInitOptions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/NativeWindowInitOptions.html) | owner                               | 2.6                  |
| flash.events   | [Event](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/Event.html)                                      | `CLOSING`                           | 1.0                  |
|                |                                                                                                                                           | `DISPLAYING`                        | 1.0                  |
|                |                                                                                                                                           | `PREPARING`                         | 2.6                  |
|                |                                                                                                                                           | `EXITING`                           | 1.0                  |
|                |                                                                                                                                           | `HTML_BOUNDS_CHANGE`                | 1.0                  |
|                |                                                                                                                                           | `HTML_DOM_INITIALIZE`               | 1.0                  |
|                |                                                                                                                                           | `HTML_RENDER`                       | 1.0                  |
|                |                                                                                                                                           | `LOCATION_CHANGE`                   | 1.0                  |
|                |                                                                                                                                           | `NETWORK_CHANGE`                    | 1.0                  |
|                |                                                                                                                                           | `STANDARD_ERROR_CLOSE`              | 2.0                  |
|                |                                                                                                                                           | `STANDARD_INPUT_CLOSE`              | 2.0                  |
|                |                                                                                                                                           | `STANDARD_OUTPUT_CLOSE`             | 2.0                  |
|                |                                                                                                                                           | `USER_IDLE`                         | 1.0                  |
|                |                                                                                                                                           | `USER_PRESENT`                      | 1.0                  |
|                | [HTTPStatusEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/HTTPStatusEvent.html)                  | `HTTP_RESPONSE_STATUS`              | 1.0                  |
|                |                                                                                                                                           | `responseHeaders`                   | 1.0                  |
|                |                                                                                                                                           | `responseURL`                       | 1.0                  |
|                | [KeyboardEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/KeyboardEvent.html)                      | `commandKey`                        | 1.0                  |
|                |                                                                                                                                           | `controlKey`                        | 1.0                  |
| flash.net      | [FileReference](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/FileReference.html)                         | `extension`                         | 1.0                  |
|                |                                                                                                                                           | `httpResponseStatus` event          | 1.0                  |
|                |                                                                                                                                           | `uploadUnencoded()`                 | 1.0                  |
|                | [NetStream](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/NetStream.html)                                 | `drmAuthenticate` event             | 1.0                  |
|                |                                                                                                                                           | `onDRMContentData` event            | 1.5                  |
|                |                                                                                                                                           | `preloadEmbeddedData()`             | 1.5                  |
|                |                                                                                                                                           | `resetDRMVouchers()`                | 1.0                  |
|                |                                                                                                                                           | `setDRMAuthenticationCredentials()` | 1.0                  |
|                | [URLRequest](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/URLRequest.html)                               | authenticate                        | 1.0                  |
|                |                                                                                                                                           | cacheResponse                       | 1.0                  |
|                |                                                                                                                                           | followRedirects                     | 1.0                  |
|                |                                                                                                                                           | idleTimeout                         | 2.0                  |
|                |                                                                                                                                           | manageCookies                       | 1.0                  |
|                |                                                                                                                                           | useCache                            | 1.0                  |
|                |                                                                                                                                           | userAgent                           | 1.0                  |
|                | [URLStream](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/URLStream.html)                                 | `httpResponseStatus event`          | 1.0                  |
| flash.printing | [PrintJob](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/printing/PrintJob.html)                              | `active`                            | 2.0                  |
|                |                                                                                                                                           | `copies`                            | 2.0                  |
|                |                                                                                                                                           | `firstPage`                         | 2.0                  |
|                |                                                                                                                                           | `isColor`                           | 2.0                  |
|                |                                                                                                                                           | `jobName`                           | 2.0                  |
|                |                                                                                                                                           | `lastPage`                          | 2.0                  |
|                |                                                                                                                                           | `maxPixelsPerInch`                  | 2.0                  |
|                |                                                                                                                                           | `paperArea`                         | 2.0                  |
|                |                                                                                                                                           | `printableArea`                     | 2.0                  |
|                |                                                                                                                                           | `printer`                           | 2.0                  |
|                |                                                                                                                                           | `printers`                          | 2.0                  |
|                |                                                                                                                                           | `selectPaperSize()`                 | 2.0                  |
|                |                                                                                                                                           | `showPageSetupDialog()`             | 2.0                  |
|                |                                                                                                                                           | `start2()`                          | 2.0                  |
|                |                                                                                                                                           | `supportsPageSetupDialog`           | 2.0                  |
|                |                                                                                                                                           | `terminate()`                       | 2.0                  |
|                | [PrintJobOptions](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/printing/PrintJobOptions.html)                | `pixelsPerInch`                     | 2.0                  |
|                |                                                                                                                                           | `printMethod`                       | 2.0                  |
| flash.system   | [Capabilities](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/system/Capabilities.html)                        | `languages`                         | 1.1                  |
|                | [LoaderContext](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/system/LoaderContext.html)                      | `allowLoadBytesCodeExecution`       | 1.0                  |
|                | [Security](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/system/Security.html)                                | `APPLICATION`                       | 1.0                  |
| flash.ui       | [KeyLocation](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/ui/KeyLocation.html)                              | D_PAD                               | 2.5                  |

Most of these new properties and methods are available only to content in the
AIR application security sandbox. However, the new members in the URLRequest
classes are also available to content running in other sandboxes.

The `ByteArray.compress()` and `ByteArray.uncompress()` methods each include a
new `algorithm` parameter, allowing you to choose between deflate and zlib
compression. This parameter is available only to content running in AIR.

## AIR-specific Flex components

The following Adobe® Flex™ MX components are available when developing content
for Adobe AIR:

- [FileEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/events/FileEvent.html)

- [FileSystemComboBox](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/FileSystemComboBox.html)

- [FileSystemDataGrid](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/FileSystemDataGrid.html)

- [FileSystemEnumerationMode](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/FileSystemEnumerationMode.html)

- [FileSystemHistoryButton](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/FileSystemHistoryButton.html)

- [FileSystemList](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/FileSystemList.html)

- [FileSystemSizeDisplayMode](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/FileSystemSizeDisplayMode.html)

- [FileSystemTree](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/FileSystemTree.html)

- [FlexNativeMenu](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/FlexNativeMenu.html)

- [HTML](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/controls/HTML.html)

- [Window](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/core/Window.html)

- [WindowedApplication](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/core/WindowedApplication.html)

- [WindowedSystemManager](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/mx/managers/WindowedSystemManager.html)

Additionally, Flex 4 includes the following spark AIR components:

- [Window](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/spark/components/Window.html)

- [WindowedApplication](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/spark/components/WindowedApplication.html)

For more information about the AIR Flex components, see
[Using the Flex AIR components](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/Flex/4.0/UsingSDK/WSacd9bdd0c5c09f4a-690d4877120e8b878b0-8000.html).
