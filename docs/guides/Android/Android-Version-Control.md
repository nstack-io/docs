---
currentMenu: android-Version-Control
---

## Version Control on Android

Version control information is part of the result from `appOpen`.
It is up to the app to decide how to handle the app update status, meaning you must provide your own way to inform the user about the update (i.e. your custom dialog and e.t.c).

```kotlin
when (appOpenResult.value.data.update.state) {
    AppUpdateState.NONE -> {
        // Do nothing because there is no update
    }
    AppUpdateState.UPDATE -> {
        // Show a user a dialog that is dismissible
    }
    AppUpdateState.FORCE -> {
        // Show the user an undismissable dialog
    }
    AppUpdateState.CHANGELOG -> {
        // Show change log (Not yet implemented because its never used)
    }
}
```

Read more about **Version control** in [*Features/Version-control*](../../features/version-control.html)