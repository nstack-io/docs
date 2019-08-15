# GDPR
## What data is stored
As a general note, NStack only stores General Personal Data - Rec.26; Art.4(1), so no sensitive data nor criminal offence related data. <br/><br/>
In MySql NStack DB, the only personal data we store is related to the backend users (names, passwords, tokens used within Nstack, roles they have within the applications that use Nstack, when they joined, photos) and of the ones that provide feedback (email, name, device they've sent the feedback from)<br/><br/>
In Elastic, as personal inf, we store an approximate location data (lat and long) deducted from the ip addresses we get from the requests.<br /><br />The same personal inf (lat and long), are send through the Pusher.
## Where is it stored
Storing DB:
* MySql (The personal data that is specified above)
* Elastic (The requests data).<br/><br/>
The data that is stored by Nstack comes via:
* Nstack RESTful API using secure data transfer (HTTPS using TLS) so that all collected data is encrypted while in transit from the app to the API.
* An Admin dashboard for the backend users <br/><br/>
Some of the data is reaching following services:
* Mailgun
* Pusher (for interacting with Pusher Channels HTTP API.)
* Amazon S3<br/><br/>
The server side framework used (Laravel) is currently running on LTS (Long Term Solution) version 5.5.

## Data retention schedule
All the request's data is kept in Elastic for 6 months. <br/>
The Backend users information are soft deleted, so the above specified data are not deleted fully, but only marked as unavailable.
