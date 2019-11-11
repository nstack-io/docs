---
currentMenu: android-Feedback
---

## Feedback on Android

The purpose of the Feedback feature in NStack is to enable you, as a client, to obtain user feedback and bug reports.

Read a more detailed explanation about **Feedback** in [*Features/Feedback*](../../features/feedback.html)


You can simply request to show NStack's default feedback form by calling:

```kotlin
NStack.Feedback.show(context, feedbackType)
```

![android feedback from](https://nstack-io.github.io/documentation/docs/images/FeatureOverview/android/android_feedback.png)

NStack's feedback screen will respect your app's `Theme.MaterialComponents` theme.

If you decide to create your own user interface you can post feedback to NStack via: 
```kotlin
NStack.Feedback.postFeedback(name, email, message, image, type)
```
