# Localizing the application name and description in the AIR application installer

You can specify multiple languages for the `name` and `description` elements in
the application descriptor file. For example, the following specifies the
application name in three languages (English, French, and German):

    <name>
        <text xml:lang="en">Sample 1.0</text>
        <text xml:lang="fr">Échantillon 1.0</text>
        <text xml:lang="de">Stichprobe 1.0</text>
    </name>

The `xml:lang` attribute for each text element specifies a language code, as
defined in RFC4646 (<http://www.ietf.org/rfc/rfc4646.txt>).

The name element defines the application name that the AIR application installer
displays. The AIR application installer uses the localized value that best
matches the user interface languages defined by the operating system settings.

You can similarly specify multiple language versions of the `description`
element in the application descriptor file. This element defines description
text that the AIR application installer displays.

These settings only apply to the languages available in the AIR application
installer. They do not define the locales available for the running, installed
application. AIR applications can provide user interfaces that support multiple
languages, including and in addition to languages available to the AIR
application installer.

For more information, see
[AIR application descriptor elements](WSfffb011ac560372f2fea1812938a6e463-8000.html).

More Help topics

[Building multilingual Flex applications on Adobe AIR](http://www.adobe.com/devnet/air/flex/articles/localizing_flex_air_apps.html)

[Building a multilingual HTML-based application](http://www.adobe.com/devnet/air/ajax/quickstart/articles/multilingual_air_apps.html)
