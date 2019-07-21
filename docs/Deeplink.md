# Deeplink

You can open NStack with access directly to one application

![App open sequence](../images/Deeplink/deeplink1.png)

The url is build by

`https://nstack.io/deeplin/{appplicationId}/{masterKey}`

When an user is clicking the url, following steps will happen:

1) Check if user is logged, else ask them to login

2) Prompt user that they are about to login to the specific app

3) Check if user has access to the application, else give user access

4) Redirect to application landing page