# AIR application descriptor files

Every AIR application requires an application descriptor file. The application
descriptor file is an XML document that defines the basic properties of the
application.

Many development environments supporting AIR automatically generate an
application descriptor when you create a project. Otherwise, you must create
your own descriptor file. A sample descriptor file, `descriptor-sample.xml`, can
be found in the `samples` directory of both the AIR and Flex SDKs.

Any filename can be used for the application descriptor file. When you package
the application, the application descriptor file is renamed `application.xml`
and placed within a special directory inside the AIR package.

#### Example application descriptor

The following application descriptor document sets the basic properties used by
most AIR applications:

    <?xml version="1.0" encoding="utf-8" ?>
    <application xmlns="http://ns.adobe.com/air/application/3.0">
        <id>example.HelloWorld</id>
        <versionNumber>1.0.1</versionNumber>
        <filename>Hello World</filename>
        <name>Example Co. AIR Hello World</name>
         <description>
            <text xml:lang="en">This is an example.</text>
            <text xml:lang="fr">C'est un exemple.</text>
            <text xml:lang="es">Esto es un ejemplo.</text>
        </description>
        <copyright>Copyright (c) 2010 Example Co.</copyright>
        <initialWindow>
            <title>Hello World</title>
            <content>
                HelloWorld.swf
            </content>
        </initialWindow>
        <icon>
            <image16x16>icons/smallIcon.png</image16x16>
            <image32x32>icons/mediumIcon.png</image32x32>
            <image48x48>icons/bigIcon.png</image48x48>
            <image128x128>icons/biggerIcon.png</image128x128>
        </icon>
    </application>

If the application uses an HTML file as its root content instead of a SWF file,
only the `<content>` element is different:

    <content>
        HelloWorld.html
    </content>

- [Application descriptor changes](WSfffb011ac560372f-1f98376f1293df83869-8000.html)
- [The application descriptor file structure](WS5b3ccc516d4fbf351e63e3d118666ade46-7f84.html)
- [AIR application descriptor elements](WSfffb011ac560372f2fea1812938a6e463-8000.html)
