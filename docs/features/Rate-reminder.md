---
currentMenu:  features-ratereminder
---

# Rate reminders

Rate reminders ask the user to **rate** the app on the platform specific **store**.
You can define rate reminder events and assign points to them. App is responsible for reporting events to NStack backend. App can check if it can show rate reminder dialog. Once the amount of points from events reach a certain threashold backend is going to allow app to show the dialog. Once app has permission from backend to show the dialog the app has to show rate reminder (using NStack SDK). When rate reminder dialog is shown the app should take user to the store page if user's response is positive, or to feedback screen if it's negative.


You can pretty much define a point system with +/- points "events", delays & required points to trigger rating reminder, example could be:
A taxi app we create following events
- +50 points on app open
- +500 points on completed trip and rated 5 stars
- +100 points on completed trip, no rating
- -250 points on driver cancelling before pickup

Trigger at 500 points with 30 days delay (Delay means, if they click "Not now" they get asked again after 30 days)

This means that should only be asking the user to rate the app, at a happy moment

**iOS**

On iOS this is done by showing Apple's build in rating popup.  
*"You should be aware that the prompt will only be displayed to a user a maximum of **three** times within a **365-day period**."* - [Apple docs](https://developer.apple.com/documentation/storekit/skstorereviewcontroller/requesting_app_store_reviews)

![iOS rate reminder](https://nstack-io.github.io/documentation/images/FeatureOverview/iOS/iOS_rate_reminder.png)
![iOS rate reminder starred](https://nstack-io.github.io/documentation/images/FeatureOverview/iOS/iOS_rate_reminder_starred.png)

**Android**

NStack sdk will show default alert dialog which can be styled by passing a theme to it with `ContextThemeWrapper`


You can find examples on how to implement **Rate Reminder** for the following platforms:

* [iOS](../../docs/guides/iOS/ios-rate-reminder.html)
* [Android](../../docs/guides/Android/android-rate-reminder.html)
