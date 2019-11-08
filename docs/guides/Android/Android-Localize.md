---
currentMenu: android-Localize
---

## Localize on Android

Read more about **Localization** in the [*Feature/Localization*](../../features/localize.html) section.

## Xml Translation

Starting with version `2.1.0` , NStack for Android supports XML-based translations embedded in the Android namespace.

``` XML
android:text="{sectionName_keyName}"
android:hint="{sectionName_keyName}"
android:description="{sectionName_keyName}"
android:textOn="{sectionName_keyName}"
android:textOff="{sectionName_keyName}"
android:contentDescription="{sectionName_keyName}"
```

The method from 2.0.2+ is still supported as follows:

``` XML
xmlns:nstack="http://schemas.android.com/apk/res-auto"
tools:ignore="MissingPrefix"
```

Before starting with the XML translations, be sure to add the following block to the root of the layout you are using.

``` XML
nstack:key="sectionName_keyName"
nstack:text="sectionName_keyName"
nstack:hint="sectionName_keyName"
nstack:description="sectionName_keyName"
nstack:textOn="sectionName_keyName"
nstack:textOff="sectionName_keyName"
nstack:contentDescription="sectionName_keyName"
```

The following field should be used to set the NStack key: `nstack:key="keyGoesHere"` 

The following format should be used when entering the key: `sectionName_keyName` 

If you're using the NStack Gradle plugin, a `nstack_keys.xml` should be generated containing all available keys. It is suggested that you reference those keys when using this feature

#### Queueing Manual Translations

Once you have that setup you can trigger the translation via the following method:

``` kotlin
NStack.translate()
```

> **Note: Running this command is optional as the views get their translation added as they are added**

#### Clearing View Cache

If for whatever reason you need to clear the translation view cache, you can trigger that using the following method:

``` kotlin
NStack.clearViewCache()
```

## Language Selection


You can get an `Arraylist<Locale>` of all available languages using the following property:

``` kotlin
NStack.availableLanguages
```

You can get a `HashMap<Locale, JSONObject>` of all available languages where the locale is the key and the language JSON object is the value:

``` kotlin
NStack.languages
```

You can simply select a language by setting the `language` variable to one of the provided locales:

``` kotlin
NStack.language = selectedLocale
```

You can also set the language using a locale string. The format must follow either the `language-country` or `language_country` form or otherwise it will not do anything.

``` kotlin
NStack.setLanguageByString("en-gb")
```

## Language Listeners

If you want to be notified when a language is changed, NStack allows you set up a `LanguageListener` with the new locale as the incoming argument:

``` kotlin
NStack.addLanguageChangeListener { locale: Locale ->
  // Your code
}
```

Additionally, if you'd like to be notified when the list of available languages changes you can use the following listener:

``` kotlin
NStack.addLanguagesChangeListener {
  // Your code
}
```
