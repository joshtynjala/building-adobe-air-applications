# Localizing the ApplicationUpdaterUI interface

The ApplicationUpdaterUI class provides a default user interface for the update
process. This includes dialog boxes that let the user start the process, cancel
the process, and perform other related actions.

The `description` element of the update descriptor file lets you define the
description of the application in multiple languages. Use multiple `text`
elements that define `lang` attributes, as in the following:

    <?xml version="1.0" encoding="utf-8"?>
    <update xmlns="http://ns.adobe.com/air/framework/update/description/1.0">
        <version>1.1a1</version>
        <url>http://example.com/updates/sample_1.1a1.air</url>
        <description>
            <text xml:lang="en">English description</text>
            <text xml:lang="fr">French description</text>
            <text xml:lang="ro">Romanian description</text>
        </description>
    </update>

The update framework uses the description that best fits the end user's
localization chain. For more information, see Defining the update descriptor
file and adding the AIR file to your web server.

Flex developers can directly add a new language to the
`"ApplicationUpdaterDialogs"` bundle.

JavaScript developers can call the `addResources()` method of the updater
object. This method dynamically adds a new resource bundle for a language. The
resource bundle defines localized strings for a language. These strings are used
in various dialog box text fields.

JavaScript developers can use the `localeChain` property of the
ApplicationUpdaterUI class to define the locale chain used by the user
interface. Typically, only JavaScript (HTML) developers use this property. Flex
developers can use the ResourceManager to manage the locale chain.

For example, the following JavaScript code defines resource bundles for Romanian
and Hungarian:

    appUpdater.addResources("ro_RO",
                        {titleCheck: "Titlu", msgCheck: "Mesaj", btnCheck: "Buton"});
    appUpdater.addResources("hu", {titleCheck: "Cím", msgCheck: "Üzenet"});
    var languages = ["ro", "hu"];
    languages = languages.concat(air.Capabilities.languages);
    var sortedLanguages = air.Localizer.sortLanguagesByPreference(languages,
                             air.Capabilities.language,
                             "en-US");
    sortedLanguages.push("en-US");
    appUpdater.localeChain = sortedLanguages;

For details, see the description of the `addResources()` method of the
ApplicationUpdaterUI class in the language reference.
