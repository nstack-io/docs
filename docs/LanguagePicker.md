# Language picker

According to standard following options can be passed in

 - `fr-CH;q=0.9, fr;q=0.8, en;q=0.7` (order list)
 - `fr-CH` (on specific with language-COUNTRY)
 - `fr` (one unspecific)

The different configs consist of 2 different things

list or single:

List: loop through the entire list of locales
Single: Only look at first locale in the list

language match or full match

Full match: Looking at a match on the entire locale

`where locale = {locale} %`

That means passed locale `fr` can find a language with locale `fr-FR`
but if passed locale is `fr-CH` it WILL NOT find a language with locale `fr-FR`

Language match: First look for full match, else cut out the language from locale (`fr-CH` => `fr`) and look for any language starting with locale `fr`

That means passed locale `fr` can find a language with locale `fr-FR`
and if passed locale is `fr-CH` it WILL find a language with locale `fr-FR`

#list-full-match

Loop through all passed options, but only accept full match

Example: 

Languages: da-DK (fallback), en-UK, fr-FR 

| Accept-Language Header              | Picked locale    |
| ----------------------------------- | -----------------|
| fr-FR                               | fr-FR            |
| fr-CH                               | da-DK            |
| fr                                  | fr-FR            |
| fr-CH;q=0.9, en-UK;q=0.8            | en-UK            |
| fr-CH;q=0.9, en-US;q=0.8            | da-DK            |
| fr-CH;q=0.9, en;q=0.8               | en-UK            |
| sv-SV;q=0.9, en;q=0.8               | da-DK            |

#list-language-match

Loop through all passed options, accept full match and language match

Example: 

Languages: da-DK (fallback), en-UK, fr-FR 

| Accept-Language Header         | Picked locale |
| ------------------------------ | --------------|
| fr-FR                          | fr-FR         |
| fr-CH                          | fr-FR         |
| fr                             | fr-FR         |
| fr-CH;q=0.9, en-UK;q=0.8       | fr-FR         |
| fr-CH;q=0.9, en-US;q=0.8       | fr-FR         |
| fr-CH;q=0.9, en;q=0.8          | fr-FR         |
| sv-SV;q=0.9, en;q=0.8          | en-UK         |

#single-full-match

Only look at first item in list, accept full match

| Accept-Language Header         | Picked locale |
| ------------------------------ | --------------|
| fr-FR                          | fr-FR         |
| fr-CH                          | da-DK         |
| fr                             | fr-FR         |
| fr-CH;q=0.9, en-UK;q=0.8       | da-DK         |
| fr-CH;q=0.9, en-US;q=0.8       | da-DK         |
| fr-CH;q=0.9, en;q=0.8          | da-DK         |
| sv-SV;q=0.9, en;q=0.8          | da-DK         | 

#single-language-match

Only look at first item in list, accept full match and language match


| Accept-Language Header         | Picked locale |
| ------------------------------ | --------------|
| fr-FR                          | fr-FR         |
| fr-CH                          | fr-FR         |
| fr                             | fr-FR         |
| fr-CH;q=0.9, en-UK;q=0.8       | fr-FR         |
| fr-CH;q=0.9, en-US;q=0.8       | fr-FR         |
| fr-CH;q=0.9, en;q=0.8          | fr-FR         |
| sv-SV;q=0.9, en;q=0.8          | da-DK         |
 