## Version Control on Vapor 

NStack has the ability to retrieve the latest version for a certain platform. You can achieve that with the `getLatestVersion(for platform: Platforms) -> Future<UpdateVersion?>` method, e.g.:

```swift
let nstack = try NStack.makeService(for: req)
nstack.application.version.getLatestVersion(for: .android)
```

Read more about **Version control** in [*Features/Version-control*](../../features/version-control.html)