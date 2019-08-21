# UGC: Feedback

The **feedback** feature is intended for **collecting** user **feedback** in **one place** where it can be easily accessible.
This can be used to include a "Send us feedback" section in the settings screen of the project.
Using the feedback feature the user can send feedback with the following properties:

- Operating system (iOS, Android, web)
- App version
- Device
- User's name
- User's email
- Message
- An image

When you have collected some feedback from users you have the following feature

- Assign a person
- Set a status (options: Created, Assigned, Progress, Done and Skipped)

> The NStack SDK (no matter the platform) does not have the **Feeback** feature implemented as a method.
>
> To use it, make a POST request to https://nstack.io/api/v2/ugc/feedbacks. 
>
> For details about the POST request, the required headers and request parameters, read more [here](https://documenter.getpostman.com/view/12675/S1a8yjgk?version=latest#7156694e-740c-4611-8e71-e9d0df5708a8)

