---
currentMenu: android-Rate-Reminder
---

## Rate Reminder on Android

In order to use reminder actions, you should create an empty `RateReminderActions.kt` file in your project. NStack will then generate the code necessary.

Calling `./gradlew generateRateReminderActions` in your project folder will generate a `RateReminderActions` class in the mentioned file. Inside the class, the SDK will also generate methods for the actions you specified in the NStack backend. You should call these methods in your app's events that match the actions you defined. 

Your app should call `NStack.RateReminder.shouldShow()` to decide if it should ask the user to give a rating. If the method returns `true`, the app should call `NStack.RateReminder.show(context)` in order to show the rating dialog. 

You can customize the text of the dialog before calling this method (see example below). The visual style of the dialog can also be adjusted by passing a style via `ContextThemeWrapper`. 

The `show` method displays the dialog and returns the user's answer. In general, you'd want to take the user to rate the app in the Play Store after a positive answer, or show some appropriate feedback if you receive a negative one (e.g. a screen saying you're sorry about their experience with the option of sending feedback).

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
