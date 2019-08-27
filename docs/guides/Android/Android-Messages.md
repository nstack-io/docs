---
currentMenu: android-Messages
---

## Messages on Android

The message is informed thought the `message` on the `onAppUpdateListener` . 

It indicates if a message shall be displayed. The variable contains the information that should be displayed.

```kotlin
NStack.onAppUpdateListener = { appUpdate ->
        appUpdate.message?.let { showMessageDialog(it) }
}
fun Activity.showMessageDialog(message: Message) {
    AlertDialog.Builder(this)
        .setMessage(message.message)
        .setCancelable(false)
        .setPositiveButton(Translation.defaultSection.ok) { dialog, _ ->
            NStack.messageSeen(message)
            dialog.dismiss()
        }
        .show()
}
```

Read more about **Messages** in [*Features/Messages*](../../features/messages.html)