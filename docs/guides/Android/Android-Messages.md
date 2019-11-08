---
currentMenu: android-Messages
---

## Messages on Android

In order to receive messages, you'll need to register an `OnAppUpdateListener` with the SDK. When you receive an update containing a message, you can access it through the `message` property. If the property is `null`, no new message has been received.   

If the `message` is not null, you can display the contained data to the user. 

``` kotlin
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