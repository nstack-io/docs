---
currentMenu: android-App-Open
---

## App Open

NStack's have a feature called App open, which enable apps to pull info from several features in one API request, 

You can learn more about it [here](../../app-open.html).

Minimal setup of this feature will only require to add this line:
```kotlin
NStack.appOpen()
```

Additionaly, if you care about the outcome or want to run code afterwards, you can use following function:
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

