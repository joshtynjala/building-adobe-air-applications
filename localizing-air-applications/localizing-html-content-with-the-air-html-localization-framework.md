# Localizing HTML content with the AIR HTML localization framework

The AIR 1.1 SDK includes an HTML localization framework. The AIRLocalizer.js
JavaScript file defines the framework. The frameworks directory of the AIR SDK
contains the AIRLocalizer.js file. This file includes an air.Localizer class,
which provides functionality to assist in creating applications that support
multiple localized versions.

## Loading the AIR HTML localization framework code

To use the localization framework, copy the AIRLocalizer.js file to your
project. Then include it in the main HTML file of the application, using a
script tag:

    <script src="AIRLocalizer.js" type="text/javascript" charset="utf-8"></script>

Subsequent JavaScript can call the `air.Localizer.localizer` object:

    <script>
        var localizer = air.Localizer.localizer;
    </script>

The `air.Localizer.localizer` object is a singleton object that defines methods
and properties for using and managing localized resources. The Localizer class
includes the following methods:

| Method                        | Description                                                                                                                                                                                                                                                                                                                                                       |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `getFile()`                   | Gets the text of a specified resource bundle for a specified locale. See [Getting resources for a specific locale](WSD2923A44-4704-4021-9714-FF5725CA2C13.html).                                                                                                                                                                                                  |
| `getLocaleChain()`            | Returns the languages in the locale chain. See [Defining the locale chain](WS337B5ACC-0D17-42b1-80BF-B8F9F3A6D412.html).                                                                                                                                                                                                                                          |
| `getResourceBundle()`         | Returns the bundle keys and corresponding values as an object. See [Getting resources for a specific locale](WSD2923A44-4704-4021-9714-FF5725CA2C13.html).                                                                                                                                                                                                        |
| `getString()`                 | Gets the string defined for a resource. See [Getting resources for a specific locale](WSD2923A44-4704-4021-9714-FF5725CA2C13.html).                                                                                                                                                                                                                               |
| `setBundlesDirectory()`       | Sets the bundles directory location. See [Customizing AIR HTML Localizer settings](WS9BB0CDF1-14C0-4c04-AD46-B0471154ED88.html).                                                                                                                                                                                                                                  |
| `setLocalAttributePrefix()`   | Sets the prefix used by localizer attributes used in HTML DOM elements. See [Customizing AIR HTML Localizer settings](WS9BB0CDF1-14C0-4c04-AD46-B0471154ED88.html)                                                                                                                                                                                                |
| `setLocaleChain()`            | Sets the order of languages in the locale chain. See [Defining the locale chain](WS337B5ACC-0D17-42b1-80BF-B8F9F3A6D412.html).                                                                                                                                                                                                                                    |
| `sortLanguagesByPreference()` | Sorts the locales in the locale chain based on the order of locales in the operating system settings. See [Defining the locale chain](WS337B5ACC-0D17-42b1-80BF-B8F9F3A6D412.html).                                                                                                                                                                               |
| `update()`                    | Updates the HTML DOM (or a DOM element) with localized strings from the current locale chain. For a discussion of locale chains, see [Managing locale chains](WS583B572D-CE0A-42b6-AAB2-24608D7B0786.html). For more information about the `update()` method, see [Updating DOM elements to use the current locale](WSBA4E3544-35C5-48d5-825C-494B86E0C7DA.html). |

The Localizer class includes the following static properties:

| Property                 | Description                                                                                                                                     |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `localizer`              | Returns a reference to the singleton Localizer object for the application.                                                                      |
| `ultimateFallbackLocale` | The locale used when the application supports no user preference. See [Defining the locale chain](WS337B5ACC-0D17-42b1-80BF-B8F9F3A6D412.html). |

## Specifying the supported languages

Use the `<supportedLanguages>` element in the application descriptor file to
identify the languages supported by the application. This element is only used
by iOS, Mac captive runtime, and Android applications, and is ignored by all
other application types.

If you do not specify the `<supportedLanguages>` element, then by default the
packager performs the following actions based on the application type:

- iOS — All languages supported by the AIR runtime are listed in the iOS app
  store as supported languages of the application.

- Mac captive runtime — Application packaged with captive bundle has no
  localization information.

- Android — Application bundle has resources for all languages supported by the
  AIR runtime.

For more information, see
[supportedLanguages](WS06ac295d95cf5a5c-4601cdc2134337a7308-8000.html).

## Defining resource bundles

The HTML localization framework reads localized versions of strings from
_localization_ files. A localization file is a collection of key-based values,
serialized in a text file. A localization file is sometimes referred to as a
_bundle_.

Create a subdirectory of your application project directory, named locale. (You
can also use a different name, see
[Customizing AIR HTML Localizer settings](WS9BB0CDF1-14C0-4c04-AD46-B0471154ED88.html).)
This directory will include the localization files. This directory is known as
the _bundles directory_.

For each locale that your application supports, create a subdirectory of the
bundles directory. Name each subdirectory to match the locale code. For example,
name the French directory "fr" and name the English directory "en." You can use
an underscore (\_) character to define a locale that has a language and country
code. For example, name the U.S. English directory "en_us." (Alternately, you
can use a hyphen instead of an underscore, as in "en-us." The HTML localization
framework supports both.)

You can add any number of resource files to a locale subdirectory. Generally,
you create a localization file for each language (and place the file in the
directory for that language). The HTML localization framework includes a
`getFile()` method that allows you to read the contents of a file (see
[Getting resources for a specific locale](WSD2923A44-4704-4021-9714-FF5725CA2C13.html).

Files that have the .properties file extension are known as localization
properties files. You can use them to define key-value pairs for a locale. A
properties file defines one string value on each line. For example, the
following defines a string value `"Hello in English."` for a key named
`greeting`:

    greeting=Hello in English.

A properties file containing the following text defines six key-value pairs:

    title=Sample Application
    greeting=Hello in English.
    exitMessage=Thank you for using the application.
    color1=Red
    color2=Green
    color3=Blue

This example shows an English version of the properties file, to be stored in
the en directory.

A French version of this properties file is placed in the fr directory:

    title=Application Example
    greeting=Bonjour en français.
    exitMessage=Merci d'avoir utilisé cette application.
    color1=Rouge
    color2=Vert
    color3=Bleu

You can define multiple resource files for different kinds of information. For
example, a legal.properties file may contain boilerplate legal text (such as
copyright information). You can reuse that resource in multiple applications.
Similarly, you can define separate files that define localized content for
different parts of the user interface.

Use UTF-8 encoding for these files, to support multiple languages.

## Managing locale chains

When your application loads the AIRLocalizer.js file, it examines the locales
defined in your application. These locales correspond to the subdirectories of
the bundles directory (see
[Defining resource bundles](WS44BB0546-4BBD-4e9d-83C9-4B24748FD946.html)). This
list of available locales is known as the _locale chain_. The AIRLocalizer.js
file automatically sorts the locale chain based on the preferred order defined
by the operating system settings. (The `Capabilities.languages` property lists
the operating system user interface languages, in preferred order.)

So, if an application defines resources for "en", "en_US" and "en_UK" locales,
the AIR HTML Localizer framework sorts the locale chain appropriately. When an
application starts on a system that reports "en" as the primary locale, the
locale chain is sorted as `["en", "en_US", "en_UK"]`. In this case, the
application looks for resources in the "en" bundle first, then in the "en_US"
bundle.

However, if the system reports "en-US" as the primary locale, then the sorting
uses `["en_US", "en", en_UK"]`. In this case, the application looks for
resources in the "en_US" bundle first, then in the "en" bundle.

By default, the application defines the first locale in the locale chain as the
default locale to use. You may ask the user to select a locale upon first
running the application. You may then choose to store the selection in a
preferences file and use that locale in subsequent start-up of the application.

Your application can use resource strings in any locale in the locale chain. If
a specific locale does not define a resource string, the application uses the
next matching resource string for other locales defined in the locale chain.

You can customize the locale chain by calling the `setLocaleChain()` method of
the Localizer object. See
[Defining the locale chain](WS337B5ACC-0D17-42b1-80BF-B8F9F3A6D412.html).

## Updating the DOM elements with localized content

An element in the application can reference a key value in a localization
properties file. For example, the `title` element in the following example
specifies a `local_innerHTML` attribute. The localization framework uses this
attribute to look up a localized value. By default, the framework looks for
attribute names that start with `"local_"`. The framework updates the attributes
that have names that match the text following `"local_"`. In this case, the
framework sets the `innerHTML` attribute of the `title` element. The `innerHTML`
attribute uses the value defined for the `mainWindowTitle` key in the default
properties file (default.properties):

    <title local_innerHTML="default.mainWindowTitle"/>

If the current locale defines no matching value, then the localizer framework
searches the rest of the locale chain. It uses the next locale in the locale
chain for which a value is defined.

In the following example, the text (`innerHTML` attribute) of the `p` element
uses the value of the `greeting` key defined in the default properties file:

    <p local_innerHTML="default.greeting" />

In the following example, the value attribute (and displayed text) of the
`input` element uses the value of the `btnBlue` key defined in the default
properties file:

    <input type="button" local_value="default.btnBlue" />

To update the HTML DOM to use the strings defined in the current locale chain,
call the `update()` method of the Localizer object. Calling the `update()`
method causes the Localizer object to parse the DOM and apply manipulations
where it finds localization (`"local_..."`) attributes:

    air.Localizer.localizer.update();

You can define values for both an attribute (such as "innerHTML") and its
corresponding localization attribute (such as "local_innerHTML"). In this case,
the localization framework only overwrites the attribute value if it finds a
matching value in the localization chain. For example, the following element
defines both `value` and `local_value` attributes:

    <input type="text" value="Blue" local_value="default.btnBlue"/>

You can also update a specific DOM element only. See the next section,
[Updating DOM elements to use the current locale](WSBA4E3544-35C5-48d5-825C-494B86E0C7DA.html).

By default, the AIR HTML Localizer uses `"local_"` as the prefix for attributes
defining localization settings for an element. For example, by default a
`local_innerHTML` attribute defines the bundle and resource name used for the
`innerHTML` value of an element. Also, by default a `local_value` attribute
defines the bundle and resource name used for the `value` attribute of an
element. You can configure the Localizer to use an attribute prefix other than
`"local_"`. See
[Customizing AIR HTML Localizer settings](WS9BB0CDF1-14C0-4c04-AD46-B0471154ED88.html).

## Updating DOM elements to use the current locale

When the Localizer object updates the HTML DOM, it causes marked elements to use
attribute values based on strings defined in the current locale chain. To have
the HTML localizer update the HTML DOM, call the `update()` method of the
`Localizer` object:

    air.Localizer.localizer.update();

To update only a specified DOM element, pass it as a parameter to the `update()`
method. The `update()` method has only one parameter, `parentNode`, which is
optional. When specified, the `parentNode` parameter defines the DOM element to
localize. Calling the `update()` method and specifying a `parentNode` parameter
sets localized values for all child elements that specify localization
attributes.

For example, consider the following `div` element:

    <div id="colorsDiv">
        <h1 local_innerHTML="default.lblColors" ></h1>
        <p><input type="button" local_value="default.btnBlue" /></p>
        <p><input type="button" local_value="default.btnRed" /></p>
        <p><input type="button" local_value="default.btnGreen" /></p>
    </div>

To update this element to use localized strings defined in the current locale
chain, use the following JavaScript code:

    var divElement = window.document.getElementById("colorsDiv");
    air.Localizer.localizer.update(divElement);

If a key value is not found in the locale chain, the localization framework sets
the attribute value to the value of the `"local_"` attribute. For example, in
the previous example, suppose the localization framework cannot find a value for
the `lblColors` key (in any of the default.properties files in the locale
chain). In this case, it uses `"default.lblColors"` as the `innerHTML` value.
Using this value indicates (to the developer) missing resources.

The `update()` method dispatches a `resourceNotFound` event when it cannot find
a resource in the locale chain. The `air.Localizer.RESOURCE_NOT_FOUND` constant
defines the string `"resourceNotFound"`. The event has three properties:
`bundleName`, `resourceName`, and `locale`. The `bundleName` property is the
name of the bundle in which the resource is not found. The `resourceName`
property is the name of the bundle in which the resource is not found. The
`locale` property is the name of the locale in which the resource is not found.

The `update()` method dispatches a `bundleNotFound` event when it cannot find
the specified bundle. The `air.Localizer.BUNDLE_NOT_FOUND` constant defines the
string `"bundleNotFound"`. The event has two properties: `bundleName` and
`locale`. The `bundleName` property is the name of the bundle in which the
resource is not found. The `locale` property is the name of the locale in which
the resource is not found.

The `update()` method operates asynchronously (and dispatches `resourceNotFound`
and `bundleNotFound` events asynchronously). The following code sets event
listeners for the `resourceNotFound` and `bundleNotFound` events:

    air.Localizer.localizer.addEventListener(air.Localizer.RESOURCE_NOT_FOUND, rnfHandler);
    air.Localizer.localizer.addEventListener(air.Localizer.BUNDLE_NOT_FOUND, rnfHandler);
    air.Localizer.localizer.update();
    function rnfHandler(event)
    {
        alert(event.bundleName + ": " + event.resourceName + ":." + event.locale);
    }
    function bnfHandler(event)
    {
        alert(event.bundleName + ":." + event.locale);
    }

## Customizing AIR HTML Localizer settings

The `setBundlesDirectory()` method of the Localizer object lets you customize
the bundles directory path. The `setLocalAttributePrefix()` method of the
Localizer object lets you customize the bundles directory path and customize the
attribute value used by the Localizer.

The default bundles directory is defined as the locale subdirectory of the
application directory. You can specify another directory by calling the
`setBundlesDirectory()` method of the Localizer object. This method takes one
parameter, `path`, which is the path to the desired bundles directory, as a
string. The value of the `path` parameter can be any of the following:

- A String defining a path relative to the application directory, such as
  `"locales"`

- A String defining a valid URL that uses the `app`, `app-storage`, or `file`
  URL schemes, such as `"app://languages"` (do _not_ use the `http` URL scheme)

- A File object

For information on URLs and directory paths, see:

- [Paths of File objects](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7fe4.html#WS5b3ccc516d4fbf351e63e3d118666ade46-7d9e)
  (for ActionScript developers)

- [Paths of File objects](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/air/html/dev/WS5b3ccc516d4fbf351e63e3d118666ade46-7fe4.html#WS5b3ccc516d4fbf351e63e3d118666ade46-7d9e)
  (for HTML developers)

For example, the following code sets the bundles directory to a languages
subdirectory of the application storage directory (not the application
directory):

    air.Localizer.localizer.setBundlesDirectory("languages");

Pass a valid path as the `path` parameter. Otherwise, the method throws a
BundlePathNotFoundError exception. This error has `"BundlePathNotFoundError"` as
its `name` property, and its `message` property specifies the invalid path.

By default, the AIR HTML Localizer uses `"local_"` as the prefix for attributes
defining localization settings for an element. For example, the
`local_innerHTML` attribute defines the bundle and resource name used for the
`innerHTML` value of the following `input` element:

    <p local_innerHTML="default.greeting" />

The `setLocalAttributePrefix()` method of the Localizer object lets you use an
attribute prefix other than `"local_"`. This static method takes one parameter,
which is the string you want to use as the attribute prefix. For example, the
following code sets the localization framework to use "loc\_" as the attribute
prefix:

    air.Localizer.localizer.setLocalAttributePrefix("loc_");

You can customize the attribute prefix the localization framework uses. You may
want to customize the prefix if the default value (`"local_"`) conflicts with
the name of another attribute used by your code. Be sure to use valid characters
for HTML attributes when calling this method. (For example, the value cannot
contain a blank space character.)

For more information on using localization attributes in HTML elements, see
[Updating the DOM elements with localized content](WS6F4C3F0F-6C68-433f-8DA4-6A233E366C8C.html).

The bundles directory and attribute prefix settings do not persist between
different application sessions. If you use a custom bundles directory or
attribute prefix setting, be sure to set it each time the application initiates.

## Defining the locale chain

By default, when you load the AIRLocalizer.js code, it sets the default locale
chain. The locales available in the bundles directory and the operating system
language settings define this locale chain. (For details, see
[Managing locale chains](WS583B572D-CE0A-42b6-AAB2-24608D7B0786.html).)

You can modify the locale chain by calling the static `setLocaleChain(`) method
of the Localizer object. For example, you may want to call this method if the
user indicates a preference for a specific language. The `setLocaleChain(`)
method takes one parameter, `chain`, which is an array of locales, such as
`["fr_FR","fr","fr_CA"]`. The order of the locales in the array sets the order
in which the framework looks for resources (in subsequent operations). If a
resource is not found for the first locale in the chain, it continues looking in
the other locale's resources. If the `chain` argument is missing, is not an
array, or is an empty array, the function fails and throws an
IllegalArgumentsError exception.

The static `getLocaleChain()` method of the Localizer object returns an Array
listing the locales in the current locale chain.

The following code reads the current locale chain and adds two French locales to
the head of the chain:

    var currentChain = air.Localizer.localizer.getLocaleChain();
    newLocales = ["fr_FR", "fr"];
    air.Localizer.localizer.setLocaleChain(newLocales.concat(currentChain));

The `setLocaleChain()` method dispatches a `"change"` event when it updates the
locale chain. The `air.Localizer.LOCALE_CHANGE` constant defines the string
`"change"`. The event has one property, `localeChain`, an array of locale codes
in the new locale chain. The following code sets an event listener for this
event:

    var currentChain = air.Localizer.localizer.getLocaleChain();
    newLocales = ["fr_FR", "fr"];
    localizer.addEventListener(air.Localizer.LOCALE_CHANGE, changeHandler);
    air.Localizer.localizer.setLocaleChain(newLocales.concat(currentChain));
    function changeHandler(event)
    {
        alert(event.localeChain);
    }

The static `air.Localizer.ultimateFallbackLocale` property represents the locale
used when the application supports no user preference. The default value is
`"en"`. You can set it to another locale, as shown in the following code:

    air.Localizer.ultimateFallbackLocale = "fr";

## Getting resources for a specific locale

The `getString()` method of the Localizer object returns the string defined for
a resource in a specific locale. You do not need to specify a `locale` value
when calling the method. In this case the method looks at the entire locale
chain and returns the string in the first locale that provides the given
resource name. The method has the following parameters:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><div>
<pre><code>bundleName</code></pre>
</div></td>
<td><p>The bundle that contains the resource. This is the filename of
the properties file without the .properties extension. (For example, if
this parameter is set as <samp>"alerts"</samp>, the Localizer code looks
in localization files named alerts.properties.</p></td>
</tr>
<tr class="even">
<td><div>
<pre><code>resourceName</code></pre>
</div></td>
<td><p>The resource name.</p></td>
</tr>
<tr class="odd">
<td><div>
<pre><code>templateArgs</code></pre>
</div></td>
<td><p>Optional. An array of strings to replace numbered tags in the
replacement string. For example, consider a call to the function where
the <samp>templateArgs</samp> parameter is <samp>["Raúl", "4"]</samp>
and the matching resource string is <samp>"Hello, {0}. You have {1} new
messages."</samp>. In this case, the function returns <samp>"Hello,
Raúl. You have 4 new messages."</samp>. To ignore this setting, pass a
<samp>null</samp> value.</p></td>
</tr>
<tr class="even">
<td><div>
<pre><code>locale</code></pre>
</div></td>
<td><p>Optional. The locale code (such as <samp>"en"</samp>,
<samp>"en_us"</samp>, or <samp>"fr"</samp>) to use. If a locale is
provided and no matching value is found, the method does not continue
searching for values in other locales in the locale chain. If no locale
code is specified, the function returns the string in the first locale
in the locale chain that provides a value for the given resource
name.</p></td>
</tr>
</tbody>
</table>

The localization framework can update marked HTML DOM attributes. However, you
can use localized strings in other ways. For example, you can use a string in
some dynamically generated HTML or as a parameter value in a function call. For
example, the following code calls the `alert()` function with the string defined
in the `error114` resource in the default properties file of the fr_FR locale:

    alert(air.Localizer.localizer.getString("default", "error114", null, "fr_FR"));

The `getString()` method dispatches a `resourceNotFound` event when it it cannot
find the resource in the specified bundle. The
`air.Localizer.RESOURCE_NOT_FOUND` constant defines the string
`"resourceNotFound"`. The event has three properties: `bundleName`,
`resourceName`, and `locale`. The `bundleName` property is the name of the
bundle in which the resource is not found. The `resourceName` property is the
name of the bundle in which the resource is not found. The `locale` property is
the name of the locale in which the resource is not found.

The `getString()` method dispatches a `bundleNotFound` event when it cannot find
the specified bundle. The `air.Localizer.BUNDLE_NOT_FOUND` constant defines the
string `"bundleNotFound"`. The event has two properties: `bundleName` and
`locale`. The `bundleName` property is the name of the bundle in which the
resource is not found. The `locale` property is the name of the locale in which
the resource is not found.

The `getString()` method operates asynchronously (and dispatches the
`resourceNotFound` and the `bundleNotFound` events asynchronously). The
following code sets event listeners for the `resourceNotFound` and
`bundleNotFound` events:

    air.Localizerlocalizer.addEventListener(air.Localizer.RESOURCE_NOT_FOUND, rnfHandler);
    air.Localizerlocalizer.addEventListener(air.Localizer.BUNDLE_NOT_FOUND, bnfHandler);
    var str = air.Localizer.localizer.getString("default", "error114", null, "fr_FR");
    function rnfHandler(event)
    {
        alert(event.bundleName + ": " + event.resourceName + ":." + event.locale);
    }
    function bnfHandler(event)
    {
        alert(event.bundleName + ":." + event.locale);
    }

The `getResourceBundle()` method of the Localizer object returns a specified
bundle for a given locale. The return value of the method is an object with
properties matching the keys in the bundle. (If the application cannot find the
specified bundle, the method returns `null`.)

The method takes two parameters—`locale` and `bundleName`.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><div>
<pre><code>locale</code></pre>
</div></td>
<td><p>The locale (such as <samp>"fr"</samp>).</p></td>
</tr>
<tr class="even">
<td><div>
<pre><code>bundleName</code></pre>
</div></td>
<td><p>The bundle name.</p></td>
</tr>
</tbody>
</table>

For example, the following code calls the `document.write()` method to load the
default bundle for the fr locale. It then calls the `document.write()` method to
write values of the `str1` and `str2` keys in that bundle:

    var aboutWin = window.open();
    var bundle = localizer.getResourceBundle("fr", "default");
    aboutWin.document.write(bundle.str1);
    aboutWin.document.write("<br/>");
    aboutWin.document.write(bundle.str2);
    aboutWin.document.write("<br/>");

The `getResourceBundle()` method dispatches a `bundleNotFound` event when it
cannot find the specified bundle. The `air.Localizer.BUNDLE_NOT_FOUND` constant
defines the string `"bundleNotFound"`. The event has two properties:
`bundleName` and `locale`. The `bundleName` property is the name of the bundle
in which the resource is not found. The `locale` property is the name of the
locale in which the resource is not found.

The `getFile()` method of the Localizer object returns the contents of a bundle,
as a string, for a given locale. The bundle file is read as a UTF-8 file. The
method includes the following parameters:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><div>
<pre><code>resourceFileName</code></pre>
</div></td>
<td><p>The filename of the resource file (such as
<samp>"about.html"</samp>).</p></td>
</tr>
<tr class="even">
<td><div>
<pre><code>templateArgs</code></pre>
</div></td>
<td><p>Optional. An array of strings to replace numbered tags in the
replacement string. For example, consider a call to the function where
the <samp>templateArgs</samp> parameter is <samp>["Raúl", "4"]</samp>
and the matching resource file contains two lines:</p><pre><code>&lt;html&gt; 
&lt;body&gt;Hello, {0}. You have {1} new messages.&lt;/body&gt; 
&lt;/html&gt; </code></pre><p>In this case, the function returns a string with two lines:</p><pre><code>&lt;html&gt; 
&lt;body&gt;Hello, Raúl. You have 4 new messages. &lt;/body&gt; 
&lt;/html&gt; </code></pre>
</div></td>
</tr>
<tr class="odd">
<td><div>
<pre><code>locale</code></pre>
</div></td>
<td><p>The locale code, such as <samp>"en_GB"</samp>, to use. If a
locale is provided and no matching file is found, the method does not
continue searching in other locales in the locale chain. If <em>no</em>
locale code is specified, the function returns the text in the first
locale in the locale chain that has a file matching the
<samp>resourceFileName</samp>.</p></td>
</tr>
</tbody>
</table>

For example, the following code calls the `document.write()` method using the
contents of the about.html file of the fr locale:

    var aboutWin = window.open();
    var aboutHtml = localizer.getFile("about.html", null, "fr");
    aboutWin.document.close();
    aboutWin.document.write(aboutHtml);

The `getFile()` method dispatches a `fileNotFound` event when it cannot find a
resource in the locale chain. The `air.Localizer.FILE_NOT_FOUND` constant
defines the string `"resourceNotFound"`. The `getFile()` method operates
asynchronously (and dispatches the `fileNotFound` event asynchronously). The
event has two properties: `fileName` and `locale`. The `fileName` property is
the name of the file not found. The `locale` property is the name of the locale
in which the resource is not found. The following code sets an event listener
for this event:

    air.Localizer.localizer.addEventListener(air.Localizer.FILE_NOT_FOUND, fnfHandler);
    air.Localizer.localizer.getFile("missing.html", null, "fr");
    function fnfHandler(event)
    {
        alert(event.fileName + ": " + event.locale);
    }

More Help topics

[Building a multilingual HTML-based application](http://www.adobe.com/devnet/air/ajax/quickstart/articles/multilingual_air_apps.html)
