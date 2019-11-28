# GDPR
## What data is stored
As a general note, NStack only stores General Personal Data - Rec.26; Art.4(1), so no sensitive data nor criminal offence related data

### `User management` module, is storing user data, to be able to login users and give access to applications / companies inside NStack

 - Name (Required)
 - Email (Required)
 - Password (hashed) (Required)
 - Profile image (Optional)
 - Invitations and permissions to access applications / companies inside NStack

### `Feedback` module, has options to store user data. But it is completely optional

 - Name
 - Email
 - Meta

### `Terms` module, has option to store an "identifier" to fx reference a view of a terms and conditions to a user. This identifier can have a userId to antoher DB or some other primary key


## Where is it stored

NStack has 4 databases. All are hosted on Amazons datacenter "eu-west-1" in Ireland.

* MySQL via AWS RDS: All persistent data to run the platform: users, permissions, content, user generated content etc

* Elastic search via cloud.elastic on AWS: Requests are stored for statistics. As personal information, we store an approximate location data (lat and long) deducted from the ip addresses we get from the requests (IP is not stored)

* Redis via AWS. Used for caching on top of MySQL

* AWS S3 file storage. 2 buckets for private and public files. All public files are served via CDN imginx or vapor.cloud

The data that is stored by NStack comes via:
* NStack RESTful API using secure data transfer (HTTPS using TLS) so that all collected data is encrypted while in transit from the app to the API.
* An Admin dashboard for serving HTML pages also using HTTPS/TLS

Some of the data is reaching the following services:
* Mailgun (Invitation & Reset password)
* Pusher (Socket connection for app open requests to dashboard module)


## Data retention schedule
All the request's data is kept for 6 months.

The Backend users information is soft deleted, so the above specified data is not deleted fully, but only marked as unavailable.

If you wish to get your user/company/application hard deleted. Please contact us via gdpr@nstack.io

