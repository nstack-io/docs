---
currentMenu: android-App-Open
---

## App Open

You can use App Open to pull information for several features in a single API call. 
If you aren't already familiar with App Open, you can learn more about it [here](../../app-open.html).

The simplest way to activate App Open is to make the following call:

```kotlin
NStack.appOpen()
```

Additionaly, if you care about the outcome or want to run some code after the operation is done, you can use the following function:

```kotlin
  GlobalScope.launch {
      withContext(Dispatchers.IO) {
        val result: AppOpenResult = NStack.appOpen()
        when (result) {
          is AppOpenResult.Success -> // handle Success
          is AppOpenResult.Failure -> // handle failure
          is AppOpenResult.NoInternet -> // handle when offline
        }
    }
}
```

