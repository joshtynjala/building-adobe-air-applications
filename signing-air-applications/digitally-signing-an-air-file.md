# Digitally signing an AIR file

Digitally signing your AIR installation files with a certificate issued by a
recognized certification authority (CA) provides significant assurance to your
users that the application they are installing has not been accidentally or
maliciously altered and identifies you as the signer (publisher). AIR displays
the publisher name during installation when the AIR application has been signed
with a certificate that is trusted, or which _chains_ to a certificate that is
trusted on the installation computer:

![](../img/CaSigned.png)

Installation confirmation dialog for application signed by a trusted certificate

If you sign an application with a self-signed certificate (or a certificate that
does not chain to a trusted certificate), the user must accept a greater
security risk by installing your application. The installation dialogs reflect
this additional risk:

![](../img/SelfSigned.png)

Installation confirmation dialog for application signed by a self-signed
certificate

Important: A malicious entity could forge an AIR file with your identity if it
somehow obtains your signing keystore file or discovers your private key.

## Code-signing certificates

The security assurances, limitations, and legal obligations involving the use of
code-signing certificates are outlined in the Certificate Practice Statements
(CPS) and subscriber agreements published by the issuing certification
authority. For more information about the agreements for the certification
authorities that currently issue AIR code signing certificates, refer to:

[ChosenSecurity](http://www.chosensecurity.com/products/tc_publisher_id_adobe_air.htm)
(http://www.chosensecurity.com/products/tc_publisher_id_adobe_air.htm)

[ChosenSecurity CPS](http://www.chosensecurity.com/resource_center/repository.htm)
(http://www.chosensecurity.com/resource_center/repository.htm)

[GlobalSign](http://www.globalsign.com/code-signing/index.html)
(http://www.globalsign.com/code-signing/index.html)

[GlobalSign CPS](http://www.globalsign.com/repository/index.htm)
(http://www.globalsign.com/repository/index.htm)

[Thawte CPS](http://www.thawte.com/cps/index.html)
(http://www.thawte.com/cps/index.html)

[VeriSign CPS](http://www.verisign.com/repository/CPS/)
(http://www.verisign.com/repository/CPS/)

[VeriSign Subscriber's Agreement](https://www.verisign.com/repository/subscriber/SUBAGR.html)
(https://www.verisign.com/repository/subscriber/SUBAGR.html)

## About AIR code signing

When an AIR file is signed, a digital signature is included in the installation
file. The signature includes a digest of the package, which is used to verify
that the AIR file has not been altered since it was signed, and it includes
information about the signing certificate, which is used to verify the publisher
identity.

AIR uses the public key infrastructure (PKI) supported through the operating
system's certificate store to establish whether a certificate can be trusted.
The computer on which an AIR application is installed must either directly trust
the certificate used to sign the AIR application, or it must trust a chain of
certificates linking the certificate to a trusted certification authority in
order for the publisher information to be verified.

If an AIR file is signed with a certificate that does not chain to one of the
trusted root certificates (and normally this includes all self-signed
certificates), then the publisher information cannot be verified. While AIR can
determine that the AIR package has not been altered since it was signed, there
is no way to know who actually created and signed the file.

Note: A user can choose to trust a self-signed certificate and then any AIR
applications signed with the certificate displays the value of the common name
field in the certificate as the publisher name. AIR does not provide any means
for a user to designate a certificate as trusted. The certificate (not including
the private key) must be provided to the user separately and the user must use
one of the mechanisms provided by the operating system or an appropriate tool to
import the certificate into the proper location in system certificate store.

## About AIR publisher identifiers

Important: As of AIR 1.5.3 the publisher ID is deprecated and no longer computed
based on the code signing certificate. New applications do not need and should
not use a publisher ID. When updating existing applications, you must specify
the original publisher ID in the application descriptor file.

Prior to AIR 1.5.3, the AIR application installer generated a publisher ID
during the installation of an AIR file. This was an identifier that is unique to
the certificate used to sign the AIR file. If you reused the same certificate
for multiple AIR applications, they received the same publisher ID. Signing an
application update with a different certificate and sometimes even a renewed
instance of the original certificate changed the publisher ID.

In AIR 1.5.3 and later, a publisher ID is not assigned by AIR. An application
published with AIR 1.5.3 can specify a publisher ID string in the application
descriptor. You should only specify a publisher ID when publishing updates for
applications originally published for versions of AIR prior to 1.5.3. If you do
not specifying the original ID in the application descriptor then the new AIR
package is not treated as an update of the existing application.

To determine the original publisher ID, find the `publisherid` file in the
META-INF/AIR subdirectory where the original application is installed. The
string within this file is the publisher ID. Your application descriptor must
specify the AIR 1.5.3 runtime (or later) in the namespace declaration of the
application descriptor file in order to specify the publisher ID manually.

The publisher ID, when present, is used for the following purposes:

- As part of the encryption key for the encrypted local store

- As part of the path for the application storage directory

- As part of the connection string for local connections

- As part of the identity string used to invoke an application with the AIR
  in-browser API

- As part of the OSID (used when creating custom install/uninstall programs)

When a publisher ID changes, the behavior of any AIR features relying on the ID
also changes. For example, data in the existing encrypted local store can no
longer be accessed and any Flash or AIR instances that create a local connection
to the application must use the new ID in the connection string. The publisher
ID for an installed application cannot change in AIR 1.5.3 or later. If you use
a different publisher ID when publishing an AIR package, the installer treats
the new package as a different application rather than as an update.

## About Certificate formats

The AIR signing tools accept any keystores accessible through the Java
Cryptography Architecture (JCA). This includes file-based keystores such as
PKCS12-format files (which typically use a .pfx or .p12 file extension), Java
.keystore files, PKCS11 hardware keystores, and the system keystores. The
keystore formats that ADT can access depend on the version and configuration of
the Java runtime used to run ADT. Accessing some types of keystore, such as
PKCS11 hardware tokens, may require the installation and configuration of
additional software drivers and JCA plug-ins.

To sign AIR files, you can use most existing code signing certificates or you
can obtain a new one issued expressly for signing AIR applications. For example,
any of the following types of certificate from VeriSign, Thawte, GlobalSign, or
ChosenSecurity can be used:

- [ChosenSecurity](http://www.chosensecurity.com/products/tc_publisher_id_adobe_air.htm)

  - TC Publisher ID for Adobe AIR

- [GlobalSign](http://www.globalsign.com/code-signing/index.html)

  - ObjectSign Code Signing Certificate

- [Thawte](http://www.thawte.com/code-signing/):

  - AIR Developer Certificate

  - Apple Developer Certificate

  - JavaSoft Developer Certificate

  - Microsoft Authenticode Certificate

- [VeriSign](http://www.verisign.com/products-services/security-services/code-signing/digital-ids-code-signing/):

  - Adobe AIR Digital ID

  - Microsoft Authenticode Digital ID

  - Sun Java Signing Digital ID

Note: The certificate must be created for code signing. You cannot use an SSL or
other type of certificate to sign AIR files.

## Time stamps

When you sign an AIR file, the packaging tool queries the server of a timestamp
authority to obtain an independently verifiable date and time of signing. The
time stamp obtained is embedded in the AIR file. As long as the signing
certificate is valid at the time of signing, the AIR file can be installed, even
after the certificate has expired. On the other hand, if no time stamp is
obtained, the AIR file ceases to be installable when the certificate expires or
is revoked.

By default, the AIR packaging tools obtain a time stamp. However, to allow
applications to be packaged when the time-stamp service is unavailable, you can
turn time stamping off. Adobe recommends that all publicly distributed AIR files
include a time stamp.

The default time-stamp authority used by the AIR packaging tools is Geotrust.

## Obtaining a certificate

To obtain a certificate, you would normally visit the certification authority
web site and complete the company's procurement process. The tools used to
produce the keystore file needed by the AIR tools depend on the type of
certificate purchased, how the certificate is stored on the receiving computer,
and, in some cases, the browser used to obtain the certificate. For example, to
obtain and export an Adobe Developer certificate certificate from Thawte you
must use Mozilla Firefox. The certificate can then be exported as a .p12 or .pfx
file directly from the Firefox user interface.

Note: Java versions 1.5 and above do not accept high-ASCII characters in
passwords used to protect PKCS12 certificate files. Java is used by the AIR
development tools to create the signed AIR packages. When you export the
certificate as a .p12 or .pfx file, use only regular ASCII characters in the
password.

You can generate a self-signed certificate using the Air Development Tool (ADT)
used to package AIR installation files. Some third-party tools can also be used.

For instructions on how to generate a self-signed certificate, as well as
instructions on signing an AIR file, see
[AIR Developer Tool (ADT)](WS5b3ccc516d4fbf351e63e3d118666ade46-7fd9.html). You
can also export and sign AIR files using Flash Builder, Dreamweaver, and the AIR
update for Flash.

The following example describes how to obtain an AIR Developer Certificate from
the Thawte Certification Authority and prepare it for use with ADT.

### Example: Getting an AIR Developer Certificate from Thawte

Note: This example illustrates only one of the many ways to obtain and prepare a
code signing certificate for use. Each certification authority has its own
policies and procedures.

To purchase an AIR Developer Certificate, the Thawte web site requires you to
use the Mozilla Firefox browser. The private key for the certificate is stored
within the browser's keystore. Ensure that the Firefox keystore is secured with
a master password and that the computer itself is physically secure. (You can
export and remove the certificate and private key from the browser keystore once
the procurement process is complete.)

As part of the certificate enrollment process a private/public key pair is
generated. The private key is automatically stored within the Firefox keystore.
You must use the same computer and browser to both request and retrieve the
certificate from Thawte's web site.

1.  Visit the Thawte web site and navigate to the
    [Product page for Code Signing Certificates](https://www.thawte.com/process/retail/new_devel?language=en&productInfo.productType=devel2).

2.  From the list of Code Signing Certificates, select the Adobe AIR Developer
    Certificate.

3.  Complete the three step enrollment process. You need to provide
    organizational and contact information. Thawte then performs its identity
    verification process and may request additional information. After
    verification is complete, Thawte will send you e-mail with instructions on
    how to retrieve the certificate.

    Note: Additional information about the type of documentation required can be
    found here:
    <https://www.thawte.com/ssl-digital-certificates/free-guides-whitepapers/pdf/enroll_codesign_eng.pdf>_._

4.  Retrieve the issued certificate from the Thawte site. The certificate is
    automatically saved to the Firefox keystore.

5.  Export a keystore file containing the private key and certificate from the
    Firefox keystore using the following steps:

    Note: When exporting the private key/cert from Firefox, it is exported in a
    .p12 (pfx) format which ADT, Flex, Flash, and Dreamweaver can use.

    1.  Open the Firefox _Certificate Manager_ dialog:

    2.  On Windows: open Tools -\> Options -\> Advanced -\> Encryption -\> View
        Certificates

    3.  On Mac OS: open Firefox -\> Preferences -\> Advanced -\> Encryption -\>
        View Certificates

    4.  On Linux: open Edit -\> Preferences -\> Advanced -\> Encryption -\> View
        Certificates

    5.  Select the Adobe AIR Code Signing Certificate from the list of
        certificates and click the **Backup** button.

    6.  Enter a file name and the location to which to export the keystore file
        and click **Save**.

    7.  If you are using the Firefox master password, you are prompted to enter
        your password for the software security device in order to export the
        file. (This password is used only by Firefox.)

    8.  On the _Choose a Certificate Backup Password_ dialog box, create a
        password for the keystore file.

        Important: This password protects the keystore file and is required when
        the file is used for signing AIR applications.A secure password should
        be chosen.

    9.  Click OK. You should receive a successful backup password message. The
        keystore file containing the private key and certificate is saved with a
        .p12 file extension (in PKCS12 format)

6.  Use the exported keystore file with ADT, Flash Builder, Flash Professional,
    or Dreamweaver. The password created for the file is required whenever an
    AIR application is signed.

Important: The private key and certificate are still stored within the Firefox
keystore. While this permits you to export an additional copy of the certificate
file, it also provides another point of access that must be protected to
maintain the security of your certificate and private key.

## Changing certificates

In some circumstances, you must change the certificate you use to sign updates
for your AIR application. Such circumstances include:

- Renewing the original signing certificate.

- Upgrading from a self-signed certificate to a certificate issued by a
  certification authority

- Changing from a self-signed certificate that is about to expire to another

- Changing from one commercial certificate to another, for example, when your
  corporate identity changes

For AIR to recognize an AIR file as an update, you must either sign both the
original and update AIR files with the same certificate or apply a certificate
migration signature to the update. A migration signature is a second signature
applied to the update AIR package using the original certificate. The migration
signature uses the original certificate to establish that the signer is the
original publisher of the application.

After an AIR file with a migration signature is installed, the new certificate
becomes the primary certificate. Subsequent updates do not require a migration
signature. However, you should apply migration signatures for as long as
possible to accommodate users who skip updates.

Important: You must change the certificate and apply a migration signature to
the update with the original certificate before it expires. Otherwise, users
must uninstall their existing version of your application before installing a
new version. For AIR 1.5.3 or later, you can apply a migration signature using
an expired certificate within a grace period of 365 days after it expires.
However, you cannot use the expired certificate to apply the main application
signature.

To change certificates:

1.  Create an update to your application

2.  Package and sign the update AIR file with the **new** certificate

3.  Sign the AIR file again with the **original** certificate (using the ADT
    `-migrate` command)

An AIR file with a migration signature is, in other respects, a normal AIR file.
If the application is installed on a system without the original version, AIR
installs the new version in the usual manner.

Note: Prior to AIR 1.5.3, signing an AIR application with a renewed certificate
did not always require a migration signature. Starting with AIR 1.5.3, a
migration signature is always required for renewed certificates.

To apply a migration signature use the
[ADT migrate command](WS901d38e593cd1bac1e63e3d128fc240122-7ffd.html), as
described in
[Signing an updated version of an AIR application](WS13ACB483-1711-43c0-9049-0A7251630A7D.html).

Note: The ADT migrate command cannot be used with AIR desktop applications that
include native extensions, because those applications are packaged as native
installers, not as .air files. To change certificates for an AIR desktop
application that includes a native extension, package the application using the
[ADT package command](WS901d38e593cd1bac1e63e3d128cdca935b-8000.html) with the
-migrate flag.

#### Application identity changes

Prior to AIR 1.5.3, the identity of an AIR application changed when an update
signed with a migration signature was installed. Changing the identity of an
application has the several repercussions, including:

- The new application version cannot access data in the existing encrypted local
  store.

- The location of the application storage directory changes. Data in the old
  location is not copied to the new directory. (But the new application can
  locate the original directory based on the old publisher ID).

- The application can no longer open local connections using the old publisher
  ID.

- The identity string used to access an application from a web page changes.

- The OSID of the application changes. (The OSID is used when writing custom
  install/uninstall programs.)

When publishing an update with AIR 1.5.3 or later, the application identity
cannot change. The original application and publisher IDs must be specified in
the application descriptor of the update AIR file. Otherwise, the new package is
not recognized as an update.

Note: When publishing a new AIR application with AIR 1.5.3 or later, you should
not specify a publisher ID.

## Terminology

This section provides a glossary of some of the key terminology you should
understand when making decisions about how to sign your application for public
distribution.

| Term                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Certification Authority (CA)         | An entity in a public-key infrastructure network that serves as a trusted third party and ultimately certifies the identity of the owner of a public key. A CA normally issues digital certificates, signed by its own private key, to attest that it has verified the identity of the certificate holder.                                                                                                                                                                                                                                             |
| Certificate Practice Statement (CPS) | Sets forth the practices and policies of the certification authority in issuing and verifying certificates. The CPS is part of the contract between the CA and its subscribers and relying parties. It also outlines the policies for identity verification and the level of assurances offered by the certificates they provide.                                                                                                                                                                                                                      |
| Certificate Revocation List (CRL)    | A list of issued certificates that have been revoked and should no longer be relied upon. AIR checks the CRL at the time an AIR application is signed, and, if no timestamp is present, again when the application is installed.                                                                                                                                                                                                                                                                                                                       |
| Certificate chain                    | A certificate chain is a sequence of certificates in which each certificate in the chain has been signed by the next certificate.                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Digital Certificate                  | A digital document that contains information about the identity of the owner, the owner's public key, and the identity of the certificate itself. A certificate issued by a certification authority is itself signed by a certificate belonging to the issuing CA.                                                                                                                                                                                                                                                                                     |
| Digital Signature                    | An encrypted message or digest that can only be decrypted with the public key half of a public-private key pair. In a PKI, a digital signature contains one or more digital certificates that are ultimately traceable to the certification authority. A digital signature can be used to validate that a message (or computer file) has not been altered since it was signed (within the limits of assurance provided by the cryptographic algorithm used), and, assuming one trusts the issuing certification authority, the identity of the signer. |
| Keystore                             | A database containing digital certificates and, in some cases, the related private keys.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Java Cryptography Architecture (JCA) | An extensible architecture for managing and accessing keystores. See the [Java Cryptography Architecture Reference Guide](http://java.sun.com/javase/6/docs/technotes/guides/security/crypto/CryptoSpec.html) for more information.                                                                                                                                                                                                                                                                                                                    |
| PKCS \#11                            | The Cryptographic Token Interface Standard by RSA Laboratories. A hardware token based keystore.                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| PKCS \#12                            | The Personal Information Exchange Syntax Standard by RSA Laboratories. A file-based keystore typically containing a private key and its associated digital certificate.                                                                                                                                                                                                                                                                                                                                                                                |
| Private Key                          | The private half of a two-part, public-private key asymmetric cryptography system. The private key must be kept secret and should never be transmitted over a network. Digitally signed messages are encrypted with the private key by the signer.                                                                                                                                                                                                                                                                                                     |
| Public Key                           | The public half of a two-part, public-private key asymmetric cryptography system. The public key is openly available and is used to decrypt messages encrypted with the private key.                                                                                                                                                                                                                                                                                                                                                                   |
| Public Key Infrastructure (PKI)      | A system of trust in which certification authorities attest to the identity of the owners of public keys. Clients of the network rely on the digital certificates issued by a trusted CA to verify the identity of the signer of a digital message (or file).                                                                                                                                                                                                                                                                                          |
| Time stamp                           | A digitally signed datum containing the date and time an event occurred. ADT can include a time stamp from an [RFC 3161](http://tools.ietf.org/html/rfc3161) compliant time server in an AIR package. When present, AIR uses the time stamp to establish the validity of a certificate at the time of signing. This allows an AIR application to be installed after its signing certificate has expired.                                                                                                                                               |
| Time stamp authority                 | An authority that issues time stamps. To be recognized by AIR, the time stamp must conform to RFC 3161 and the time stamp signature must chain to a trusted root certificate on the installation machine.                                                                                                                                                                                                                                                                                                                                              |

## iOS Certificates

The code signing certificates issued by Apple are used for signing iOS
applications, including those developed with Adobe AIR. Applying a signature
using a Apple development certificate is required to install an application on
test devices. Applying a signature using a distribution certificate is required
to distribute the finished application.

To sign an application, ADT requires access to both the code signing certificate
and the associated private key. The certificate file, itself, does not include
the private key. You must create a keystore in the form of a Personal
Information Exchange file (.p12 or .pfx) that contains both the certificate and
the private key. See
[Converting a developer certificate into a P12 keystore file](WSfffb011ac560372f46768d8712cd1d13954-7ffc.html).

### Generating a certificate signing request

To obtain a developer certificate, you generate a certificate signing request,
which you submit at the Apple iOS Provisioning Portal.

The certificate signing request process generates a public-private key pair. The
private key remains on your computer. You send the signing request containing
the public key and your identifying information to Apple, who is acting in the
role of a Certificate Authority. Apple signs your certificate with their own
World Wide Developer Relations certificate.

#### Generate a certificate signing request on Mac OS

On Mac OS, you can use the Keychain Access application to generate a code
signing request. The Keychain Access application is in the Utilities
subdirectory of the Applications directory. Instructions for generating the
certificate signing request are available at the Apple iOS Provisioning Portal.

#### Generate a certificate signing request on Windows

For Windows developers, it may be easiest to obtain the iPhone developer
certificate on a Mac computer. However, it is possible to obtain a certificate
on a Windows computer. First, you create a certificate signing request (a CSR
file) using OpenSSL:

1.  Install OpenSSL on your Windows computer. (Go to
    <http://www.openssl.org/related/binaries.html>.)

    You may also need to install the Visual C++ 2008 Redistributable files,
    listed on the Open SSL download page. (You do _not_ need Visual C++
    installed on your computer.)

2.  Open a Windows command session, and CD to the OpenSSL bin directory (such as
    c:\OpenSSL\bin\\.

3.  Create the private key by entering the following in the command line:

        openssl genrsa -out mykey.key 2048

    Save this private key file. You will use it later.

    When using OpenSSL, do not ignore error messages. If OpenSSL generates an
    error message, it may still output files. However, those files may not be
    usable. If you see errors, check your syntax and run the command again.

4.  Create the CSR file by entering the following in the command line:

        openssl req -new -key mykey.key -out CertificateSigningRequest.certSigningRequest  -subj "/emailAddress=yourAddress@example.com, CN=John Doe, C=US"

    Replace the e-mail address, CN (certificate name), and C (country) values
    with your own.

5.  Upload the CSR file to Apple at the
    [iPhone developer site](http://developer.apple.com/iphone/). (See "Apply for
    an iPhone developer certificate and create a provisioning profile".)

### Converting a developer certificate into a P12 keystore file

To create a P12 keystore, you must combine your Apple developer certificate and
the associated private key in a single file. The process for creating the
keystore file depends on the method that you used to generate the original
certificate signing request and where the private key is stored.

#### Convert the iPhone developer certificate to a P12 file on Mac OS

Once you have downloaded the Apple iPhone certificate from Apple, export it to
the P12 keystore format. To do this on Mac® OS:

1.  Open the Keychain Access application (in the Applications/Utilities folder).

2.  If you have not already added the certificate to Keychain, select File \>
    Import. Then navigate to the certificate file (the .cer file) you obtained
    from Apple.

3.  Select the Keys category in Keychain Access.

4.  Select the private key associated with your iPhone Development Certificate.

    The private key is identified by the iPhone Developer: \<First Name\> \<Last
    Name\> public certificate that is paired with it.

5.  Command-click the iPhone Developer certificate and select, _Export "iPhone
    Developer: Name..."_.

6.  Save your keystore in the Personal Information Exchange (.p12) file format.

7.  You will be prompted to create a password that is used when you use the
    keystore to sign applications or transfer the key and certificate in this
    keystore to another keystore.

#### Convert an Apple developer certificate to a P12 file on Windows

To develop AIR for iOS applications, you must use a P12 certificate file. You
generate this certificate based on the Apple iPhone developer certificate file
you receive from Apple.

1.  Convert the developer certificate file you receive from Apple into a PEM
    certificate file. Run the following command-line statement from the OpenSSL
    bin directory:

        openssl x509 -in developer_identity.cer -inform DER -out developer_identity.pem -outform PEM

2.  If you are using the private key from the keychain on a Mac computer,
    convert it into a PEM key:

        openssl pkcs12 -nocerts -in mykey.p12 -out mykey.pem

3.  You can now generate a valid P12 file, based on the key and the PEM version
    of the iPhone developer certificate:

        openssl pkcs12 -export -inkey mykey.key -in developer_identity.pem -out iphone_dev.p12

    If you are using a key from the Mac OS keychain, use the PEM version you
    generated in the previous step. Otherwise, use the OpenSSL key you generated
    earlier (on Windows).
