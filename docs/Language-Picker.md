---
currentMenu: language-picker
---

# Language picker

A locale is a set of parameters that defines the user's language, region and any special variant preferences that the user wants to see in their user interface. Usually a locale identifier consists of at least a language code and a country/region code.
>Examples:
>  - `fr-CH;q=0.9, fr;q=0.8, en;q=0.7` (ordered list or types below)
>  - `fr-CH` (on specific with format: `language-COUNTRY`)
>  - `fr` (one unspecific format: `language`, with no region)

The way the locale works on Android and iOS is slightly different.

## iOS
The `Language picker` is initiliased as well in the `App Open` sequence.
The `NStack SDK` fetches the phone's preffered languages together with their locale. 

> Examples:  user can have his phone in English, but the region/locale can be set to Denmark/Spain/Sweden and not necessarily to US or UK.

Based on the setting chosen in `Localize language picker setting`, NStack will sent back the localization that matches what was sent from the phone, but also what is set up on the NStack web console.

The issue with iOS is: there is a preffered languages list. The language at the top of the list is the language that the device is on and all system installed apps will be shown in that language, together with apps that have localization for that language, while the other languages are selected by the user in the order of his/her preferences. (There are cases where the preferred languages list contains only one language and that is it).

>Example: The NStack application has localization for 2 languages: English and Danish. English is made the default language.
>
>An iOS user has his device set up with preffered languages. If his top most language is Danish and then English, then the localization coming from back from NStack will be in Danish. If it is the other way around (English > Danish), the localization will be in English.
>
>If the user has Russian/Swedish/Spanish as his top preffered language and English / Danish are not on the list, then the localization will be in English (the default language in NStack). If he has any of the two languages in his list (English / Danish), then the localization will be in that language (English / Danish)
>
> In the preffered languages list that iOS has, the region is the one the device is set up to use. There can be a device that has the following languages as preffered: English, Danish, Italian, Spanish and the region set up to Denmark. When the NStack client sends the list of languages, all of them will have DK as country.
> 
> The above example takes into consideration only the device's language, not the region. If the region is required to be taken into consideration, then NStack will try and match the language + the region and provide the appropiate localization. If it cannot find any match, it will provide the default localization. 

## Android

The `Language picker` is initiliased as well in the `App Open` sequence.
The `NStack SDK` fetches the phone's preffered languages together with their locale. 

> Examples:  user can have his phone in English, but the region/locale can be set to Denmark/Spain/Sweden and not necessarily to US or UK.

Based on the setting chosen in `Localize language picker setting`, NStack will sent back the localization that matches what was sent from the phone, but also what is set up on the NStack web console.

The Android platform makes it much easier to pick a language.

## `Localize language picker setting`

The different configurations consist of 2 different options:

### list or single:

* **List**: loop through the entire list of locales
* **Single**: Only look at first locale in the list

### language match or full match

* **Full match**: Looking at a match on the entire locale

  `where locale = {locale} %`

  If the passed locale is `fr` it can find a language with locale `fr-FR`
  If passed locale is `fr-CH` it WILL NOT find a language with locale `fr-FR`

* **Language match**: First look for full match, else extract the language from locale (`fr-CH` => `fr`) and look for any language starting with locale `fr`

  If the passed locale is `fr` it can find a language with locale `fr-FR`
  If passed locale is `fr-CH` it WILL find a language with locale `fr-FR`

## list-full-match

`Loop through all passed options, but only accept full match`

Example: Languages: da-DK (fallback), en-UK, fr-FR 

| Accept-Language Header  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;           | Picked locale    |
| ----------------------------------- | -----------------|
| fr-FR                               | fr-FR            |
| fr-CH                               | da-DK            |
| fr                                  | fr-FR            |
| fr-CH;q=0.9, en-UK;q=0.8            | en-UK            |
| fr-CH;q=0.9, en-US;q=0.8            | da-DK            |
| fr-CH;q=0.9, en;q=0.8               | en-UK            |
| sv-SV;q=0.9, en;q=0.8               | da-DK            |

## list-language-match

`Loop through all passed options, accept full match and language match`

Example:  Languages: da-DK (fallback), en-UK, fr-FR 

| Accept-Language Header  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;       | Picked locale |
| ------------------------------ | --------------|
| fr-FR                          | fr-FR         |
| fr-CH                          | fr-FR         |
| fr                             | fr-FR         |
| fr-CH;q=0.9, en-UK;q=0.8       | fr-FR         |
| fr-CH;q=0.9, en-US;q=0.8       | fr-FR         |
| fr-CH;q=0.9, en;q=0.8          | fr-FR         |
| sv-SV;q=0.9, en;q=0.8          | en-UK         |

## single-full-match

`Only look at first item in list, accept full match`

| Accept-Language Header   &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;      | Picked locale |
| ------------------------------ | --------------|
| fr-FR                          | fr-FR         |
| fr-CH                          | da-DK         |
| fr                             | fr-FR         |
| fr-CH;q=0.9, en-UK;q=0.8       | da-DK         |
| fr-CH;q=0.9, en-US;q=0.8       | da-DK         |
| fr-CH;q=0.9, en;q=0.8          | da-DK         |
| sv-SV;q=0.9, en;q=0.8          | da-DK         |

## single-language-match

`Only look at first item in list, accept full match and language match`


| Accept-Language Header  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;       | Picked locale |
| ------------------------------ | --------------|
| fr-FR                          | fr-FR         |
| fr-CH                          | fr-FR         |
| fr                             | fr-FR         |
| fr-CH;q=0.9, en-UK;q=0.8       | fr-FR         |
| fr-CH;q=0.9, en-US;q=0.8       | fr-FR         |
| fr-CH;q=0.9, en;q=0.8          | fr-FR         |
| sv-SV;q=0.9, en;q=0.8          | da-DK         |

------
