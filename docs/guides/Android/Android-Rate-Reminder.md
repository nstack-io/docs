---
currentMenu: android-Rate-Reminder
---

## Rate Reminder on Android

NStack gradle plugin will generate rate reminder actions. For this it requires `RateReminderActions.kt` file to be created.

`./gradlew generateRateReminderActions` will create `RateReminderActions` with methods which send events to NStack backend. App should call those methods when an event happens.

App can check if dialog should be shown by calling `NStack.RateReminder.shouldShow()`. If the method returns true then the app should call `NStack.RateReminder.show(context)` in order to show the dialog. Dialog's text can be set before calling the method and the dialog can be styled by passing a style via `ContextThemeWrapper`. `show` method will return user's answer. If the answer is positive the app should take the user to the playstore page. If it's negative the app should go to feedback screen.

```kotlin

// call relevent methods when corresponding events happen
RateReminderActions.orderReceived()
RateReminderActions.paymentDeclined()
// etc

// ...

launch(Dispatchers.Main) {
    if (withContext(Dispatchers.IO) { NStack.RateReminder.shouldShow() }) {
        val answer = NStack.RateReminder.apply {
            title = Translation.rate.title
            message = Translation.rate.message
            yesButton = Translation.rate.yesButton
            noButton = Translation.rate.noButton
            skipButton = Translation.rate.skipButton
        }.show(ContextThemeWrapper(context, R.style.customDialog))
        when (answer) {
            RateReminderAnswer.POSITIVE -> // take user to the playstore page
            RateReminderAnswer.NEGATIVE -> // take user to the feedback screen
            RateReminderAnswer.SKIP -> // do nothing?
        }
    }
}

```

Read more about **Rate Reminder** in [*Features/Rate Reminder*](../../features/rate-reminder.html)
