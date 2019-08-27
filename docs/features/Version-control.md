---
currentMenu:  features-versioncontrol
---

# Version control

Using the version control feature of NStack you can inform the user that a **new version** of the app is **available**.  
There are a few ways you can configure how the user should interact and be informed about the new version:

**Update mode:**

- "Off" - The user will **not** be prompted with the update dialog.

- "On" - The user will be prompted with the update dialog on app open. But can **decide** to say no to the update, 24h later they will see the dialog again.

  - When selecting "Yes" the **App Store** will be opened on the apps page where the user can **update** the app.
  - When selecting "No" the dialog will be **dismissed** and the app resumes as normal.

  ![iOS version control](https://nstack-io.github.io/documentation/images/FeatureOverview/iOS/iOS_version_control.png)

- "Force" - The user will be prompted with the update dialog on app open, Which they **cannot close**. They are forced to update the app.

  - When selecting "Yes" the **App store** updates screen will be opened.

  ![iOS version control force](https://nstack-io.github.io/documentation/images/FeatureOverview/iOS/iOS_version_control_force.png)

**New in version:**

- "Yes" - If the app has been **auto-updated**, we will show a dialog with the **change log** on the next app open.  
  ![iOS version control auto update](https://nstack-io.github.io/documentation/images/FeatureOverview/iOS/iOS_version_control_auto_update.png)
- "No" - No dialog will be shown after an auto-update.

**Change log:**

In the change log you can list all the **new features**, bug fixes or UI updates that are present in the new app and need to be presented to the user.

**File (Android):**

You can upload a file to the new version, this is mainly used when **releasing** an Android app **outside** of the **Google play** store using a .apk file.

**Text:**

The title and button texts used in the popups can be configured in the **localisation** section of the app on the **"Nstack(system)" platform**.

You can find examples on how to implement **Version Control** for the following platforms:

- [iOS](../../docs/guides/iOS/iOS-Version-Control.html)
- [Android](../../docs/guides/Android/Android-Version-Control.html)
- [Vapor](../../docs/guides/Vapor/Vapor-Version-Control.html)