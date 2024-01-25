# ActionScript compilers

<div>

Before ActionScript and MXML code can be included in an AIR application, it must
be compiled. If you use an Integrated Development Environment (IDE), such as
Adobe Flash Builder or Adobe Flash Professional, the IDE handles compilation
behind the scenes. However, you can also invoke the ActionScript compilers from
the command line to create your SWF files when not using an IDE or when using a
build script.

</div>

<div>

## About the AIR command-line tools in the Flex SDK

<div>

Each of the command-line tools you use to create an Adobe AIR application calls
the corresponding tool used to build applications:

- amxmlc calls mxmlc to compile application classes

- acompc calls compc to compile library and component classes

- aasdoc calls asdoc to generate documentation files from source code comments

The only difference between the Flex and the AIR versions of the utilities is
that the AIR versions load the configuration options from the air-config.xml
file instead of the flex-config.xml file.

The Flex SDK tools and their command-line options are fully described in the
[Flex documentation](http://help.adobe.com/en_US/flex/using/WS2db454920e96a9e51e63e3d11c0bf69084-7ffd.html).
The Flex SDK tools are described here at a basic level to help you get started
and to point out the differences between building Flex applications and building
AIR applications.

</div>

</div>

<div>

## Compiler setup

<div>

You typically specify compilation options both on the command line and with one
or more configuration files. The global Flex SDK configuration file contains
default values that are used whenever the compilers are run. You can edit this
file to suit your own development environment. There are two global Flex
configuration files located in the frameworks directory of your Flex SDK
installation. The air-config.xml file is used when you run the amxmlc compiler.
This file configures the compiler for AIR by including the AIR libraries. The
flex-config.xml file is used when you run mxmlc.

The default configuration values are suitable for discovering how Flex and AIR
work, but when you embark on a full-scale project examine the available options
more closely. You can supply project-specific values for the compiler options in
a local configuration file that takes precedence over the global values for a
given project.

<div>

Note: No compilation options are used specifically for AIR applications, but you
must reference the AIR libraries when compiling an AIR application. Typically,
these libraries are referenced in a project-level configuration file, in a file
for a build tool such as Ant, or directly on the command line.

</div>

</div>

</div>

<div>

## Compiling MXML and ActionScript source files for AIR

<div>

You can compile the Adobe® ActionScript® 3.0 and MXML assets of your AIR
application with the command-line MXML compiler (amxmlc). (You do not need to
compile HTML-based applications. To compile a SWF in Flash Professional, simply
publish the movie to a SWF file.)

The basic command-line pattern for using amxmlc is:

    amxmlc [compiler options] -- MyAIRApp.mxml

where _\[compiler options\]_ specifies the command-line options used to compile
your AIR application.

The amxmlc command invokes the standard Flex mxmlc compiler with an additional
parameter, `+configname=air`. This parameter instructs the compiler to use the
air-config.xml file instead of the flex-config.xml file. Using amxmlc is
otherwise identical to using mxmlc.

The compiler loads the air-config.xml configuration file specifying the AIR and
Flex libraries typically required to compile an AIR application. You can also
use a local, project-level configuration file to override or add additional
options to the global configuration. Typically, the easiest way to create a
local configuration file is to edit a copy of the global version. You can load
the local file with the `-load-config` option:

**-load-config=project-config.xml** Overrides global options.

**-load-config+=project-config.xml** Adds additional values to those global
options that take more than value, such as the `-library-path` option. Global
options that only take a single value are overridden.

If you use a special naming convention for the local configuration file, the
amxmlc compiler loads the local file automatically. For example, if the main
MXML file is `RunningMan.mxml`, then name the local configuration file:
`RunningMan-config.xml`. Now, to compile the application, you only have to type:

    amxmlc RunningMan.mxml

`RunningMan-config.xml` is loaded automatically since its filename matches that
of the compiled MXML file.

<div>

#### amxmlc examples

The following examples demonstrate use of the amxmlc compiler. (Only the
ActionScript and MXML assets of your application must be compiled.)

Compile an AIR MXML file:

    amxmlc myApp.mxml

Compile and set the output name:

    amxmlc –output anApp.swf -- myApp.mxml

Compile an AIR ActionScript file:

    amxmlc myApp.as

Specify a compiler configuration file:

    amxmlc –load-config config.xml -- myApp.mxml

Add additional options from another configuration file:

    amxmlc –load-config+=moreConfig.xml -- myApp.mxml

Add libraries on the command line (in addition to the libraries already in the
configuration file):

    amxmlc –library-path+=/libs/libOne.swc,/libs/libTwo.swc  -- myApp.mxml

Compile an AIR MXML file without using a configuration file (Win):

    mxmlc -library-path [AIR SDK]/frameworks/libs/air/airframework.swc, ^
    [AIR SDK]/frameworks/libs/air/airframework.swc, ^
    -library-path [Flex SDK]/frameworks/libs/framework.swc ^
    -- myApp.mxml

Compile an AIR MXML file without using a configuration file (Mac OS X or Linux):

    mxmlc -library-path [AIR SDK]/frameworks/libs/air/airframework.swc, \
    [AIR SDK]/frameworks/libs/air/airframework.swc, \
    -library-path [Flex 3 SDK]/frameworks/libs/framework.swc \
    -- myApp.mxml

Compile an AIR MXML file to use a runtime-shared library:

    amxmlc -external-library-path+=../lib/myLib.swc -runtime-shared-libraries=myrsl.swf -- myApp.mxml

Compile an AIR MXML file to use an ANE (be sure to use `‑external‑library‑path`
for the ANE):

    amxmlc -external-library-path+=../lib/myANE.ane -output=myAneApp.swf -- myAneApp.mxml

Compiling from Java (with the class path set to include `mxmlc.jar`):

    java flex2.tools.Compiler +flexlib [Flex SDK 3]/frameworks +configname=air [additional compiler options] -- myApp.mxml

The flexlib option identifies the location of your Flex SDK frameworks
directory, enabling the compiler to locate the flex_config.xml file.

Compiling from Java (without the class path set):

    java -jar [Flex SDK 2]/lib/mxmlc.jar +flexlib [Flex SDK 3]/frameworks +configname=air [additional compiler options] -- myApp.mxml

To invoke the compiler using Apache Ant (the example uses a Java task to run
mxmlc.jar):

    <property name="SDK_HOME" value="C:/Flex46SDK"/>
    <property name="MAIN_SOURCE_FILE" value="src/myApp.mxml"/>
    <property name="DEBUG" value="true"/>
    <target name="compile">
        <java jar="${MXMLC.JAR}" fork="true" failonerror="true">
            <arg value="-debug=${DEBUG}"/>
            <arg value="+flexlib=${SDK_HOME}/frameworks"/>
            <arg value="+configname=air"/>
            <arg value="-file-specs=${MAIN_SOURCE_FILE}"/>
        </java>
    </target>

</div>

</div>

</div>

<div>

## Compiling an AIR component or code library (Flex)

<div>

Use the component compiler, acompc, to compile AIR libraries and independent
components. The acompc component compiler behaves like the amxmlc compiler, with
the following exceptions:

- You must specify which classes within the code base to include in the library
  or component.

- acompc does not look for a local configuration file automatically. To use a
  project configuration file, you must use the –load-config option.

The acompc command invokes the standard Flex compc component compiler, but loads
its configuration options from the `air-config.xml` file instead of the
`flex-config.xml` file.

</div>

<div>

### Component compiler configuration file

<div>

Use a local configuration file to avoid typing (and perhaps incorrectly typing)
the source path and class names on the command line. Add the -load-config option
to the acompc command line to load the local configuration file.

The following example illustrates a configuration for building a library with
two classes, ParticleManager and Particle, both in the package:
`com.adobe.samples.particles`. The class files are located in the
`source/com/adobe/samples/particles` folder.

    <flex-config>
        <compiler>
            <source-path>
                <path-element>source</path-element>
            </source-path>
        </compiler>
        <include-classes>
            <class>com.adobe.samples.particles.ParticleManager</class>
            <class>com.adobe.samples.particles.Particle</class>
        </include-classes>
    </flex-config>

To compile the library using the configuration file, named
`ParticleLib-config.xml`, type:

    acompc -load-config ParticleLib-config.xml -output ParticleLib.swc

To run the same command entirely on the command line, type:

    acompc -source-path source -include-classes com.adobe.samples.particles.Particle
    com.adobe.samples.particles.ParticleManager -output ParticleLib.swc

(Type the entire command on one line, or use the line continuation character for
your command shell.)

</div>

</div>

<div>

### acompc examples

<div>

These examples assume that you are using a configuration file named
`myLib-config.xml`.

Compile an AIR component or library:

    acompc -load-config myLib-config.xml -output lib/myLib.swc

Compile a runtime-shared library:

    acompc -load-config myLib-config.xml -directory -output lib

(Note, the folder lib must exist and be empty before running the command.)

</div>

</div>

</div>

<div>

<div>

More Help topics

</div>

<div>

[Creating your first desktop AIR application with the Flex SDK](WS144092a96ffef7cc4c0afd1212601c9a36f-8000.html)

</div>

![](./img/flexLinkIndicator.png) 
[Flex compilers](http://help.adobe.com/en_US/Flex/4.5/UsingSDK/WS2db454920e96a9e51e63e3d11c0bf69084-7ffd.html "http://help.adobe.com/en_US/Flex/4.5/UsingSDK/WS2db454920e96a9e51e63e3d11c0bf69084-7ffd.html")

<div>

</div>

</div>
