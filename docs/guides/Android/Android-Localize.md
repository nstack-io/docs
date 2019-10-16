---
currentMenu: android-Localize
---

## Localize on Android

Read more about **Localization** in the [*Feature/Localization*](../../features/localize.html) section.

## Xml Translation

Starting with version `2.1.0` NStack-Kotlin now supports XML based translations embedded in the Android namespace.

```XML
android:text="{sectionName_keyName}"
android:hint="{sectionName_keyName}"
android:description="{sectionName_keyName}"
android:textOn="{sectionName_keyName}"
android:textOff="{sectionName_keyName}"
android:contentDescription="{sectionName_keyName}"
```

The method from 2.0.2+ is still supported as follows:

```XML
xmlns:nstack="http://schemas.android.com/apk/res-auto"
tools:ignore="MissingPrefix"
```

Before starting with the XML translations be sure to add the following block to the root of the layout you are using.

```XML
nstack:key="sectionName_keyName"
nstack:text="sectionName_keyName"
nstack:hint="sectionName_keyName"
nstack:description="sectionName_keyName"
nstack:textOn="sectionName_keyName"
nstack:textOff="sectionName_keyName"
nstack:contentDescription="sectionName_keyName"
```

The following field should be used to set the NStack key `nstack:key="keyGoesHere"`

When entering the key the following format should be used `sectionName_keyName`

If you're using the NStack Gradle plugin, a `nstack_keys.xml` should be generated containing all available keys. It is suggested that you reference those keys when using this feature

#### Queuing Manual Translations

Once you have that setup you can trigger the translation via the following method:

```kotlin
NStack.translate()
```

> **Note: Running this command is optional as the views get their translation added as they are added**

#### Clearing View Cache

If for whatever reason you need to clear the translate view cache, you can trigger that view the following method:

```kotlin
NStack.clearViewCache()
```



## Language Selection

```kotlin
NStack.availableLanguages
```
Provides an `Arraylist<Locale>` of all available languages

```kotlin
NStack.languages
```
Provides an `HashMap<Locale, JSONObject>` of all available languages as the key and the language json object as the value

```kotlin
NStack.language = selectedLocale
```

Using any of the provided locales you are able to select a language simply by setting the `language` variable in NStack

```kotlin
NStack.setLanguageByString("en-gb")
```

Allows you to set the language by string. The format must follow either the `language-country` or `language_country` format otherwise it will not do anything.



## Language Listeners
If you interested in locale changes events, NStack allows you set up a `LanguageListener`:
```kotlin
NStack.addLanguageChangeListener{ locale: Locale ->
  // Your code
}
```

Adds a listener to NStack that will trigger every time the language is changed (returns the new locale)


```kotlin
NStack.addLanguagesChangeListener {
}
```

This listener should trigger every time the available languages change