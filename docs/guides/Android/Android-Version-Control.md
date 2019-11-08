---
currentMenu: android-Version-Control
---

## Version Control on Android

When `appOpen` returns successfully (see [Android - App Open](/docs/guides/Android/android-app-open.html)) you will get the version control data as part of the result. It is up to you to handle this result, so you need to implement your own update feedback to the user (e.g. a customized dialog).

``` kotlin
when (appOpenResult.value.data.update.state) {
    AppUpdateState.NONE -> {
        // There is no update, you will probably want to keep this empty
    }
    AppUpdateState.UPDATE -> {
        // An update is available that does not require the user to switch to it immediately
    }
    AppUpdateState.FORCE -> {
        // A mandatory update is available and users should be forced to install the new app before being able to use it again 
        // (e.g. show a non-dismissive dialog at app start)
    }
    AppUpdateState.CHANGELOG -> {
        // Display the change log (not implemented in yet)
    }
}
```

Read more about **Version control** in [*Features/Version-control*](../../features/version-control.html)