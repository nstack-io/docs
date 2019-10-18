---
currentMenu: android-Terms
---

## Terms on Android

NStack Terms let's you access and interact with versioned content such as "Terms & Conditions" or "Privacy policies". Learn more about this feature [here](../../features/terms.html).


### Latest Terms

NStack provides a list of new Terms that haven't been seen by the current app instance as part of the `AppOpenResult`. After setting up App Open as outlined [here](android-app-open.html) you can access it with `result.appUpdateResponse.data.terms`.

NStack additionally provides a helper function to access a locally cached version via `NStack.Terms.latestTerms`.


### Terms Details

To present Terms content in your app use `NStack.Terms.getTermsDetails()`. This function will serve the latest available `TermsDetails` from NStack:

```kotlin
when (val result = NStack.Terms.getTermsDetails(
        termsID = 1
)) {
    is Result.Success -> {}
    is Result.Error -> {}
}
```


### Terms Viewed

NStack let's you mark a version of terms as viewed via `NStack.Terms.setTermsViewed()`. This function will set `TermsDetails.hasViewed` to `true` for the current app instance. 

```kotlin
when (val result = NStack.Terms.setTermsViewed(
        versionID = 1,
        userID = "1"
)) {
    is Result.Success -> {}
    is Result.Error -> {}
}
```