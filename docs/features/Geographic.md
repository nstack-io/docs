# Geographic

**Note: The following datasets are global, meaning changing it in 1 project will change it for all projects.**

Encourage the developers to use these datasets in appropriate use cases, these datasets discourage hardcoding this data in the app or using a 3rd party datasets/libraries.
It also gives us more flexibility to update the data without a new app release should something change.

### Continents

The continents dataset includes the 7 continents, for each continent the following properties are available:

- Name
- Code
- Image

**Use cases:**

- Show list of continents for the user to pick from.
- Use images as markers on a map.
- ...

### Countries

The countries dataset includes around 250 countries, for each country the following properties are available:

- Country code
- ISO code
- 2 images
- English Name
- Native name
- Continent
- Capital
- Capital timezone
- Coordinates for the capital
- Phone number prefix
- Currency
- Languages

**Use cases:**

- Show list of countries for the user to pick from
- See what currency is used in a certain country
- Check what timezone a certain county uses
- Get the coordinates from a certain country's capital
- ...

### Time zones

The timezones dataset includes over 500 timezones, for each timezone the following properties are available:

- Name
- Abbreviation
- Offset from UTC in seconds
- A standardised text used in the UTC notation (e.g.: UTC+5)

**Use cases:**

- Show a list of timezones for the user to pick from.
- Check the offset from UTC for a certain timezone
- ...

*Notes:*

- *As there are so many timezones using this as a reference might a bit overkill.*
- *Many languages/platform have a build in way of handling/Referencing timezones, discuss with the developer what is needed/possible.*

### Languages

The languages dataset includes over 50 languages, for each language the following properties are available:

- Name
- Locale ( [language abbreviation] - [area] e.g.: en-Gb, en-US. Both english but different areas )
- Reading direction

**Use cases:**

- Show a list of languages
- ...

### IP's

The enormous IP dataset includes over 10 million IPs, for each IP range the following properties are available: 

- Start of range
- End of range
- Country
- State
- City
- Location coordinates
- Timezone
- ISP
- Type

**Use cases:**

- Use as a fallback when the user denied the location permissions
  Using this dataset as a reference we can see in what area the user is without relying on the device.
  This is useful in cases where the location of the user doesn't need to be accurate, where just a city is accurate enough.  
  **Warning: This is not 100% accurate, When traveling a IP address of the users home country can still be in use.**
- ...