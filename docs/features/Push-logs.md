# UGC: Push logs

The push logs feature allows the **backend** responsible for sending out push notifications to **log** all the **notifications** it sends out.  
These logs can be seen on the NStack website and can be **easily sorted**.

These logs can be very **useful** if anything goes wrong in terms of push notifications, this is traditionally **very hard to debug** and figure out what went wrong, with these logs we should have a better idea on what was send and if it succeeded or not and can **save many hours debugging**.

The logs include:

- Push provider (e.g.: Firebase, urban-airship)
- Key: App key in fcm/ urban-airship
- Message: included in the push notification
- Succeeded: if the push was sent or not
- Type (e.g: standard, friend-request, taxi-arrived)
- UserID: The user ID used by the project
- Relation: Similar to type but more general (e.g.: Booking, Company, ...)