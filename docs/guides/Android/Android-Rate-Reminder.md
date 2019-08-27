---
currentMenu: android-Rate-Reminder
---

## Rate Reminder on Android

The rate reminder is informed thought the `rateReminder``onAppUpdateListener` on the . It indicates if a message asking the user to rate the app shall be displayed. The variable contains the information that should be displayed like body text, title, buttons labels, etc.


```kotlin
NStack.onAppUpdateListener = { appUpdate ->
        appUpdate.rateReminder?.let { showRateReminderDialog(it) }
}
fun Activity.showRateReminderDialog(rateReminder: RateReminder) {
        AlertDialog.Builder(this)
                .setMessage(rateReminder.body)
                .setTitle(rateReminder.title)
                .setCancelable(false)
                .setPositiveButton(rateReminder.yesButton) { dialog, _ ->
                    NStack.onRateReminderAction(true)
                    dialog.dismiss()
                }
                .setNegativeButton(rateReminder.noButton) { dialog, _ ->
                    NStack.onRateReminderAction(false)
                    dialog.dismiss()
                }
                .setNeutralButton(rateReminder.laterButton) { dialog, _ ->
                    dialog.dismiss()
                }
                .show()
}
```

> The example above shows how to use the Rate reminder in a simple Alert Dialog.
>
> Note: the NStack Rate Reminder feature has no UI. 
>
> It is up to the developer to create an appropiate UI element to show the user the rate reminder.

Read more about **Rate Reminder** in [*Features/Rate Reminder*](../../features/rate-reminder.html)



