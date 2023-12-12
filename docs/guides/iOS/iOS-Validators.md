---
currentMenu: ios-Validation
---

## Validation on iOS

NStack makes it possible to validate the syntax and domain of an email, just use:

~~~~swift
NStack.sharedInstance.validateEmail("tech@monstar-lab.com") { (valid, error) in
    if valid {
        //Email syntax and domain is valid
    }
}
~~~~

Read more about **Validation** in [*Features/Validation*](../../features/validators.html)