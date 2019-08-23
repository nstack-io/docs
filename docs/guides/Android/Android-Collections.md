---
currentMenu: android-Collections
---

## Collections on Android

The purpose of the Collections feature in NStack is to enable you, as a client, to be able to control different data sets that are shown in the app.

In your application, you can obtain your collections either by using method with callback, or use power of Kotlin Coroutines with the `suspend` method.

Example using callback method:
```kotlin
  NStack.getCollectionResponse("slug",
      onSuccess = { response: String -> doSomething(response) },
      onError = {error: Exception -> handleError(error) }
  )
```
Example with `Coroutines`:
```kotlin
GlobalScope.launch {
    withContext(Dispatchers.IO) {
      val response: String? = NStack.getCollectionResponse("slug")
      doSomething(response)
  }
}
```

Read a more detailed explanation about **Collections** in [*Features/Collections*](../../features/collections.html)