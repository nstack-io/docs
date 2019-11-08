---
currentMenu: android-Collections
---

## Collections on Android

Collections allow your Android app to display your project-specific datasets managed through the NStack CMS. 

You can obtain your collection using the `getCollectionResponse(...)` suspend function and passing a [slug](https://en.wikipedia.org/wiki/Clean_URL#Slug) representing that collection:

``` kotlin
GlobalScope.launch {
    withContext(Dispatchers.IO) {
      val response: String? = NStack.getCollectionResponse("your-slug-here")

      doSomething(response)
  }
}
```

Read a more detailed explanation about **Collections** in [*Features/Collections*](../../features/collections.html).

