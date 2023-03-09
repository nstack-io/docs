---
currentMenu:  features-config
---

# Config

The config feature meant to be our go-to solution for feature flag configuration in our app productions.

Over time we've seen many different ways of storing and controlling state a la "feature flags" in NStack. Some have attempted to do it via `Localization` or via a custom `Response`. 

This is an attempt at a proper implementation.

- A feature is a name, type and value. The type can be `Integer`, `String` or `Boolean`. That should fit most use cases.
- These can be enabled or disabled, which just means it's not sent to the clients via `App Open`.
- An API is exposed to enable client SDK's to generate code similar to Translation classes for parsing feature flags.

Implementation details:

- Name is automatically converted from `News delay` to `NEWS_DELAY`.

**AppOpen**

```
{
	"data": {
		"count": 44,
		...
		"config": {
			"NEWS_DELAY": 8
		}
	},
	"meta": {
		"accept_Language": "en_DK"
	}
}
```

**/v2/content/config**

```
{
	"config": {
		"NEWS_DELAY": 8
	},
	"raw": [
		{
			"name": "NEWS_DELAY",
			"value": "8",
			"type": "integer"
		}
	]
}
```

**Admin panel**

<img width="967" alt="Screenshot 2022-04-17 at 14 55 07" src="https://user-images.githubusercontent.com/1464994/163734825-89ca5d1a-ab4d-4cfc-874e-29883bd02d9b.png">
