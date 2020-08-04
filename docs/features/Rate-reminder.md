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

![iOS rate reminder](../images/FeatureOverview/iOS/iOS_rate_reminder.png)
![iOS rate reminder starred](../images/FeatureOverview/iOS/iOS_rate_reminder_starred.png)

**Android**

NStack sdk will show default alert dialog which can be styled by passing a theme to it with `ContextThemeWrapper`


You can find examples on how to implement **Rate Reminder** for the following platforms:

* [iOS](../../docs/guides/iOS/ios-rate-reminder.html)
* [Android](../../docs/guides/Android/android-rate-reminder.html)


# Version 2

Ratereminders V2 has the following endpoints:

 - [GET] Show
 - [GET] Actions
 - [Post] Action Events
 - [Post] Answer

# GUID

RateReminder requires every device to use a guid. If you are using the NStack SDK, the SDK will generate one for you. If you are implementing RateReminders without the SDK you will have to generate your own unique ID.
Remember to store your ID if you are not using the SDK, so the app does not generate a new every time the user opens the app. 

[read more about guid](API.md#what-is-a-guid)

# Authentication headers
all calls require the 2 authentication headers "X-Application-Id" and "X-Rest-Api-Key". These are automatically generated and can be found on nstack.io in your application.

For Post requests "Content-Type" - "application/json"  should be included.
 

# [GET] Show 
api/v2/notify/rate_reminder_v2?guid={{guid}}

The request will return 200 or 404.

200: You should prompt your user for a rating

{
    "data": {
        "id": 22,
        "points_to_trigger": 26,
        "days_delay_on_skip": 0,
        "localization": {
            "title": null,
            "body": null,
            "yesBtn": null,
            "laterBtn": null,
            "noBtn": null
        },
        "points": 50
    }
}

- "id": The ID for your rating. You will need to store it, as it required to post the users answer.
- "points_to_trigger": Amount of points required to show the rating - this can be changed on nstack.io
- "days_delay_on_skip": Amount of days a user will wait after pressing skip - this can be changed on nstack.io
- "localization": The translations to use when showing the  rating dialog. This can be setup on nstack.io. If you are not using the SDK you can also just use your own translations.
- "points": The users current amount of points 

404: You should not prompt the user for a rating

Will also return a message why the rate dialog should not be shown. This is mainly intended for debugging, you should not show it to the user. 

{
    "message": "Not yet, missing points - points: 0"
}

Note if a user has already answered this will also return 404
{
    "message": "Already answered"
}


# [GET] Actions 
api/v2/notify/rate_reminder_v2/actions

returns a list of the available actions:
{
    "data": [
        "appstart",
        "readarticle"
    ]
}


# [POST] Action Events 
api/v2/notify/rate_reminder_v2/events

Body: 
{
	"guid": "test-test-test7",
	"action": "appstart"
}

A succesfull response wil return:

{
    "guid": "test-test-test7",
    "points": 10,
    "action_id": 13,
    "updated_at": "2020-03-06 11:28:25",
    "created_at": "2020-03-06 11:28:25",
    "id": 343
}

If you try to call an action is not available the call will return 412.


# [POST] Action Events 
api/v2/notify/rate_reminder_v2/{{ratereminderid}}/answers

- Ratereminderid you can get from SHOW

POST Body

{
	"guid": "test-test-test7",
	"answer": "skip"
}

Answers: can be: "positive", "negative" or "skip".


*Note*  if the user skips the dialog but rate the app another way you can call  answers again with "positive" or "negative" to ensure that the user will not prompted again to rate the app. you can _not_ enable it again by setting the answer to skip.

If the user clicks negative, it would be normally be a good idea to get the user [feedback](Feedback.md)
