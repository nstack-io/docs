# Language picker

According to standard following options can be passed in

 - `fr-CH;q=0.9, fr;q=0.8, en;q=0.7` (order list)
 - `fr-CH` (on specific with language-COUNTRY)
 - `fr` (one unspecific)

#list-full-match

Loop through all passed options, but only accept full match

#list-language-match

Loop through all passed options, accept full match and language match

fx if fr-CH is passed in but does not exist, but fr-FR does. It picks that over next item in list and thereby fallback language

#single-full-match

Only look at first item in list, accept full match 

#single-language-match

Only look at first item in list, accept full match and language match

fx if fr-CH is passed in but does not exist, but fr-FR does. It picks that over next item in list and thereby fallback language
